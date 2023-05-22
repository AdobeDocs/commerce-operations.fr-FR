---
title: Configuration du vernis avancé
description: Configurez les fonctions Varnish avancées, notamment les modes Contrôle de l’intégrité, Grace et saint.
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 0%

---

# Configuration du vernis avancé

Varnish fournit plusieurs fonctionnalités qui empêchent les clients de subir de longs délais et délais d’expiration lorsque le serveur Commerce ne fonctionne pas correctement. Ces fonctionnalités peuvent être configurées dans la variable `default.vcl` fichier . Cette rubrique décrit les ajouts que Commerce fournit dans le fichier VCL (Varnish Configuration Language) que vous téléchargez depuis l’administrateur.

Voir [Manuel de référence des pointes](https://varnish-cache.org/docs/6.3/reference/index.html) pour plus d’informations sur l’utilisation du langage de configuration vernis.

## Contrôle de l’intégrité

La fonction de contrôle de l’intégrité de Varnish interroge le serveur Commerce pour déterminer s’il répond en temps voulu. S’il répond normalement, le contenu neuf est régénéré après l’expiration de la période de temps d’activation (TTL). Sinon, Varnish diffuse toujours du contenu obsolète.

Commerce définit le contrôle de l’intégrité par défaut suivant :

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

Toutes les 5 secondes, ce contrôle de l’intégrité appelle la variable `pub/health_check.php` script. Ce script vérifie la disponibilité du serveur, de chaque base de données et de Redis (s’il est installé). Le script doit renvoyer une réponse dans les 2 secondes. Si le script détermine que l’une de ces ressources est hors service, il renvoie un code d’erreur HTTP 500. Si ce code d’erreur est reçu dans six tentatives sur dix, le serveur principal est considéré comme malsain.

Le `health_check.php` se trouve dans la variable `pub` répertoire . Si votre répertoire racine Commerce est `pub`, puis assurez-vous de modifier le chemin d’accès dans la variable `url` du paramètre `/pub/health_check.php` to `health_check.php`.

Pour plus d’informations, voir [Contrôles de l’intégrité vernis](https://varnish-cache.org/docs/6.3/users-guide/vcl-backends.html?highlight=health%20check#health-checks) documentation.

## Mode de grâce

Le mode Grace permet à Varnish de garder un objet en cache au-delà de sa valeur TTL. Le vernis peut ensuite diffuser le contenu obsolète (obsolète) lorsqu’il récupère une nouvelle version. Cela améliore le flux du trafic et réduit les temps de chargement. Il est utilisé dans les situations suivantes :

- Lorsque le serveur principal Commerce est sain, mais qu’une requête prend plus de temps que la normale
- Lorsque le serveur principal Commerce n’est pas sain.

Le `vcl_hit` subroutine définit la manière dont Varnish répond à une demande d’objets qui ont été mis en cache.

### Lorsque le serveur principal Commerce est sain

Lorsque les contrôles de l’intégrité déterminent que le serveur principal Commerce est sain, Varnish vérifie si le temps reste dans la période de grâce. La période de grâce par défaut est de 300 secondes, mais un commerçant peut définir la valeur de l’administrateur comme décrit dans la section [Configuration de Commerce pour l’utilisation du vernis](configure-varnish-commerce.md). Si la période de grâce n’a pas expiré, Varnish diffuse le contenu obsolète et actualise de manière asynchrone l’objet à partir du serveur Commerce. Si la période de grâce a expiré, Varnish diffuse le contenu obsolète et actualise de manière synchrone l’objet à partir du serveur principal Commerce.

La durée maximale pendant laquelle Varnish diffuse un objet obsolète est la somme de la période de grâce (300 secondes par défaut) et de la valeur TTL (86 400 secondes par défaut).

Pour modifier la période de grâce par défaut à partir de la fonction `default.vcl` modifiez la ligne suivante dans le fichier `vcl_hit` sous-routine :

```conf
if (obj.ttl + 300s > 0s) {
```

### Lorsque le serveur principal Commerce n’est pas sain

Si le serveur principal Commerce n’est pas réactif, Varnish diffuse du contenu obsolète du cache pendant trois jours (ou tel que défini dans `beresp.grace`) plus la durée de vie restante (qui est par défaut d’un jour), sauf si le contenu mis en cache est purgé manuellement.

## Mode Saint

Le mode Saint exclut les arrière-plans malsains pendant une durée configurable. Par conséquent, les arrière-plans malsains ne peuvent pas traiter le trafic lors de l’utilisation de Varnish comme équilibreur de charge. Le mode Saint peut être utilisé avec le mode de grâce pour permettre une gestion complexe des serveurs principaux malsains. Par exemple, si un serveur principal n’est pas sain, les reprises peuvent être routées vers un autre serveur. Si tous les autres serveurs sont en panne, alors diffusez des objets mis en cache obsolètes. Les hôtes principaux du mode saint et les périodes de blackout sont définis dans la variable `default.vcl` fichier .

Le mode Saint peut également être utilisé lorsque les instances de Commerce sont mises hors ligne individuellement pour effectuer des tâches de maintenance et de mise à niveau sans affecter la disponibilité du site de Commerce.

### Prérequis du mode Saint

Désignez une machine comme Principale installation. Sur cette machine, installez l’instance principale de Commerce, de la base de données mySQL et de Varnish.

Sur tous les autres ordinateurs, l’instance Commerce doit avoir accès à la base de données mySQL de l’ordinateur Principal. Les machines secondaires doivent également avoir accès aux fichiers de l’instance Principale Commerce.

Vous pouvez également désactiver le contrôle de version des fichiers statiques sur tous les ordinateurs. Vous pouvez y accéder à partir de la section Admin sous **Magasins** > Paramètres > **Configuration** > **Avancé** > **Développeur** > **Paramètres des fichiers statiques** > **Signature de fichiers statiques** = **Non**.

Enfin, toutes les instances de Commerce doivent être en mode de production. Avant le démarrage de Varnish, effacez le cache de chaque instance. Dans Admin, accédez à **Système** > Outils > **Gestion du cache** et cliquez sur **Vider le cache du Magento**. Vous pouvez également exécuter la commande suivante pour effacer le cache :

```bash
bin/magento cache:flush
```

### Installation

Le mode Saint ne fait pas partie du package vernis principal. Il s’agit d’une version séparée. `vmod` qui doit être téléchargé et installé. Par conséquent, vous devez recompiler le vernis à partir de la source, comme décrit dans les articles suivants :

- [Installation de Varnish 6.4](https://varnish-cache.org/docs/6.4/installation/install.html)
- [Installation de Varnish 6.0](https://varnish-cache.org/docs/6.0/installation/install.html) (LTS)

Après avoir recompilé, vous pouvez installer le module de mode Saint. En général, procédez comme suit :

1. Obtention du code source à partir de [Modules vernis](https://github.com/varnish/varnish-modules). Cloner la version Git (version maître), car les versions 0.9.x contiennent une erreur de code source.
1. Créez le code source avec des outils automatiques :

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Voir [Collection de modules en vernis](https://github.com/varnish/varnish-modules) pour plus d’informations sur l’installation du module mode Saint.

### Exemple de fichier VCL

L’exemple de code suivant illustre le code qui doit être ajouté à votre fichier VCL pour activer le mode saint. Placez le `import` et `backend` Définitions en haut du fichier.

```cpp
import saintmode;
import directors;

backend default1 {
    .host = "192.168.0.1";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

backend default2 {
    .host = "192.168.0.2";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

sub vcl_init {
    # Instantiate sm1, sm2 for backends tile1, tile2
    # with 10 blacklisted objects as the threshold for marking the
    # whole backend sick.
    new sm1 = saintmode.saintmode(default1, 10);
    new sm2 = saintmode.saintmode(default2, 10);

    # Add both to a director. Use sm0, sm1 in place of tile1, tile2.
    # Other director types can be used in place of random.
    new magedirector = directors.random();
    magedirector.add_backend(sm1.backend(), 1);
    magedirector.add_backend(sm2.backend(), 1);
}

sub vcl_backend_fetch {
    # Get a backend from the director.
    # When returning a backend, the director will only return backends
    # saintmode says are healthy.
    set bereq.backend = magedirector.backend();
}

sub vcl_backend_response {
    if (beresp.status >= 500) {
        # This marks the backend as sick for this specific
        # object for the next 20s.
        saintmode.blacklist(20s);
        # Retry the request. This will result in a different backend
        # being used.
        return (retry);
    }
}
```
