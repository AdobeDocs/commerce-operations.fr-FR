---
title: Configuration avancée du vernis
description: Configurez les fonctionnalités de vernis avancées, notamment les modes contrôle de l’intégrité, grâce et saint.
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: ec3ab7e3c6c3835e73653b0d4f74aadc861016d3
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 0%

---

# Configuration avancée du vernis

Le vernis offre plusieurs fonctionnalités qui empêchent les clients de subir de longs retards et des délais d’expiration lorsque le serveur Commerce ne fonctionne pas correctement. Ces fonctionnalités peuvent être configurées dans le fichier `default.vcl`. Cette rubrique décrit les ajouts que Commerce fournit dans le fichier VCL (Varnish Configuration Language) que vous téléchargez à partir de l’interface d’administration.

Voir le [Manuel de référence du vernis](https://varnish-cache.org/docs/index.html) pour plus d&#39;informations sur l&#39;utilisation du langage de configuration du vernis.

## Contrôle de l’intégrité

La fonctionnalité de contrôle d’intégrité de Varnish interroge le serveur Commerce pour déterminer s’il répond dans les délais impartis. S’il répond normalement, le nouveau contenu est régénéré après l’expiration de la période de durée de vie (TTL). Sinon, le vernis sert toujours du contenu obsolète.

Commerce définit le contrôle d’intégrité par défaut suivant :

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

Toutes les 5 secondes, ce contrôle d’intégrité appelle le script `pub/health_check.php` . Ce script vérifie la disponibilité du serveur, de chaque base de données et de Redis (si installé). Le script doit renvoyer une réponse dans les 2 secondes. Si le script détermine que l’une de ces ressources est hors service, il renvoie un code d’erreur HTTP 500. Si ce code d’erreur est reçu dans six tentatives sur dix, le serveur principal est considéré comme non intègre.

Le script `health_check.php` se trouve dans le répertoire `pub` . Si votre répertoire racine Commerce est `pub`, veillez à modifier le chemin d’accès dans le paramètre `url` de `/pub/health_check.php` à `health_check.php`.

Pour plus d’informations, consultez la documentation [Contrôles d’intégrité Varnish](https://varnish-cache.org/docs/7.4/users-guide/vcl-backends.html#health-checks).

## Mode de grâce

Le mode de grâce permet à Varnish de conserver un objet dans le cache au-delà de sa valeur de durée de vie. Le vernis peut ensuite diffuser le contenu expiré (obsolète) pendant qu’il récupère une nouvelle version. Cela améliore le flux du trafic et réduit les temps de chargement. Il est utilisé dans les situations suivantes :

- Lorsque le serveur principal Commerce est intègre, mais qu’une requête prend plus de temps que d’habitude
- Lorsque le serveur principal Commerce n’est pas intègre.

La sous-routine `vcl_hit` définit la manière dont Varnish répond à une demande d’objets qui ont été mis en cache.

### Lorsque le serveur principal Commerce est intègre

Lorsque les contrôles d’intégrité déterminent que le serveur principal Commerce est intègre, Varnish vérifie que le temps reste dans la période de grâce. La période de grâce par défaut est de 300 secondes, mais un commerçant peut définir la valeur à partir de l’administrateur comme décrit dans [Configurer Commerce pour utiliser le vernis](configure-varnish-commerce.md). Si le délai de grâce n’a pas expiré, Varnish diffuse le contenu obsolète et actualise l’objet de manière asynchrone à partir du serveur Commerce. Si le délai de grâce a expiré, Varnish diffuse le contenu obsolète et actualise de manière synchrone l’objet à partir du serveur principal de Commerce.

La durée maximale pendant laquelle Varnish diffuse un objet obsolète est la somme de la période de grâce (300 secondes par défaut) et de la valeur de TTL (86400 secondes par défaut).

Pour modifier la période de grâce par défaut à partir du fichier `default.vcl`, modifiez la ligne suivante dans la sous-routine `vcl_hit` :

```conf
if (obj.ttl + 300s > 0s) {
```

### Lorsque le serveur principal Commerce n’est pas intègre

Si le serveur principal Commerce n’est pas réactif, Varnish diffuse le contenu obsolète du cache pendant trois jours (ou comme défini dans `beresp.grace`), plus la durée de vie restante (qui est d’un jour par défaut), sauf si le contenu mis en cache est purgé manuellement.

## Mode Saint

Le mode Saint exclut les serveurs principaux non intègres pendant une durée configurable. Par conséquent, les serveurs principaux malsains ne peuvent pas traiter le trafic lors de l’utilisation de Vernis comme répartition de charge. Le mode Saint peut être utilisé avec le mode Grace pour permettre une gestion complexe des serveurs principaux malsains. Par exemple, si un serveur principal n’est pas intègre, les reprises peuvent être acheminées vers un autre serveur. Si tous les autres serveurs sont hors service, diffusez les objets mis en cache obsolètes. Les hôtes principaux du mode saint et les périodes de coupure sont définis dans le fichier `default.vcl`.

Le mode Saint peut également être utilisé lorsque les instances Commerce sont mises hors ligne individuellement pour effectuer des tâches de maintenance et de mise à niveau sans affecter la disponibilité du site Commerce.

### Conditions préalables relatives au mode Saint

Désignez un ordinateur comme installation principale. Sur cet ordinateur, installez l’instance principale de Commerce, la base de données mySQL et Varnish.

Sur tous les autres ordinateurs, l’instance Commerce doit avoir accès à la base de données mySQL de l’ordinateur principal. Les ordinateurs secondaires doivent également avoir accès aux fichiers de l’instance Commerce principale.

Vous pouvez également désactiver le contrôle de version des fichiers statiques sur tous les ordinateurs. Pour y accéder, sélectionnez Admin sous **Magasins** > Paramètres > **Configuration** > **Avancé** > **Développeur** > **Paramètres des fichiers statiques** > **Sign Fichiers statiques** = **No**.

Enfin, toutes les instances Commerce doivent être en mode de production. Avant le démarrage de Varnish, effacez le cache de chaque instance. Dans Admin, accédez à **System** > Tools > **Cache Management** et cliquez sur **Flush Magento Cache**. Vous pouvez également exécuter la commande suivante pour effacer le cache :

```bash
bin/magento cache:flush
```

### Installation

Le mode Saint ne fait pas partie du paquet principal Varnish. Il s’agit d’un `vmod` avec version distincte qui doit être téléchargé et installé. Par conséquent, vous devez recompiler Varnish à partir de la source, comme décrit dans les [instructions d’installation](https://varnish-cache.org/docs/index.html) pour votre version de Varnish.

Après avoir recompilé, vous pouvez installer le module mode Saint . En règle générale, procédez comme suit :

1. Obtenez le code source des [modules de vernis](https://github.com/varnish/varnish-modules). Clonez la version Git (version principale), car les versions 0.9.x contiennent une erreur de code source.
1. Créez le code source à l’aide d’outils automatiques :

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Voir [Collection de modules Varnish](https://github.com/varnish/varnish-modules) pour plus d’informations sur l’installation du module Mode Saint.

### Exemple de fichier VCL

L’exemple de code suivant montre le code qui doit être ajouté à votre fichier VCL pour activer le mode saint. Placez les instructions de `import` et les définitions de `backend` en haut du fichier.

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
