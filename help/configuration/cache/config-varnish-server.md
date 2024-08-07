---
title: Configuration du serveur web
description: Découvrez comment configurer votre serveur web pour qu’il fonctionne avec le vernis.
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# Configuration du serveur web

Configurez votre serveur web pour qu’il écoute sur un port autre que le port par défaut 80, car Varnish répond directement aux requêtes HTTP entrantes et non au serveur web.

Les sections suivantes utilisent le port 8080 comme exemple.

**Pour modifier le port d’écoute Apache 2.4** :

1. Ouvrez `/etc/httpd/conf/httpd.conf` dans un éditeur de texte.
1. Recherchez la directive `Listen` .
1. Remplacez la valeur du port d’écoute par `8080`. (Vous pouvez utiliser n’importe quel port d’écoute disponible.)
1. Enregistrez vos modifications dans `httpd.conf` et quittez l’éditeur de texte.

## Modification de la configuration du système Varnish

Pour modifier la configuration du système vernis :

1. En tant qu’utilisateur disposant des privilèges `root`, ouvrez votre fichier de configuration de l’annulation dans un éditeur de texte :

   - CentOS 6 : `/etc/sysconfig/varnish`
   - CentOS 7 : `/etc/varnish/varnish.params`
   - Debian : `/etc/default/varnish`
   - Ubuntu : `/etc/default/varnish`

1. Définissez le port d’écoute du vernis sur 80 :

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Pour Varnish 4.x, assurez-vous que DAEMON_OPTS contient le port d’écoute correct pour le paramètre `-a` (même si VARNISH_LISTEN_PORT est défini sur la valeur correcte) :

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. Enregistrez vos modifications dans le fichier de configuration de vernis et quittez l’éditeur de texte.

### Modification de la VCL par défaut

Cette section explique comment fournir une configuration minimale afin que Varnish renvoie des en-têtes de réponse HTTP. Cela vous permet de vérifier que le vernis fonctionne avant de configurer l’application [!DNL Commerce] pour utiliser le vernis.

Pour configurer minimalement le vernis :

1. Sauvegardez `default.vcl` :

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. Ouvrez `/etc/varnish/default.vcl` dans un éditeur de texte.
1. Localisez la scène suivante :

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. Remplacez la valeur de `.host` par le nom d’hôte complet ou l’adresse IP et le port d’écoute du _serveur principal_ ou du _serveur d’origine_ ; c’est-à-dire que le serveur fournissant le contenu Varnish va accélérer.

   En règle générale, il s’agit de votre serveur web. Voir [Serveurs principaux](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) dans le _guide de vernis_.

1. Remplacez la valeur de `.port` par le port d’écoute du serveur web (8080 dans cet exemple).

   Exemple : Apache est installé sur l’hôte 192.0.2.55 et Apache écoute sur le port 8080 :

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Si Varnish et Apache s’exécutent sur le même hôte, Adobe vous recommande d’utiliser une adresse IP ou un nom d’hôte et non `localhost`.

1. Enregistrez vos modifications dans `default.vcl` et quittez l’éditeur de texte.

1. Redémarrez le vernis :

   ```bash
   service varnish restart
   ```

Si Varnish ne démarre pas, essayez de l’exécuter à partir de la ligne de commande comme suit :

```bash
varnishd -d -f /etc/varnish/default.vcl
```

Les messages d’erreur doivent s’afficher.


>[!INFO]
>
>Si Varnish ne démarre pas en tant que service, vous devez configurer les règles SELinux pour l’autoriser à s’exécuter.

## Vérifier que le vernis fonctionne

Les sections suivantes expliquent comment vérifier que Varnish fonctionne, mais _sans_ configurer Commerce pour l’utiliser. Avant de configurer Commerce, vous devez l’essayer.

Effectuez les tâches décrites dans les sections suivantes dans l’ordre indiqué :

- [Démarrage du vernis](#start-varnish)
- [`netstat`](#netstat)

### Démarrage du vernis

Entrée : `service varnish start`

Si Varnish ne démarre pas en tant que service, démarrez-le à partir de la ligne de commande comme suit :

1. Démarrez l’interface de ligne de commande de vernis :

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Démarrez le processus enfant Varnish :

   Lorsque vous y êtes invité, saisissez `start`

   Les messages suivants s’affichent pour confirmer un démarrage réussi :

   ```
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Connectez-vous au serveur Varnish et saisissez la commande suivante :

```bash
netstat -tulpn
```

Recherchez notamment les résultats suivants :

```
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

Le précédent présente Varnish s’exécutant sur le port 80 et Apache s’exécutant sur le port 8080.

Si vous ne voyez pas de sortie pour `varnishd`, vérifiez que Varnish est en cours d’exécution.

Voir [`netstat` options](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Installation du logiciel Commerce

Installez le logiciel Commerce si ce n’est pas déjà fait. Lorsque vous êtes invité à saisir une URL de base, utilisez l’hôte Varnish et le port 80 (pour Varnish), car Varnish reçoit toutes les requêtes HTTP entrantes.

Erreur possible lors de l’installation de Commerce :

```
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

Si vous rencontrez cette erreur, modifiez `default.vcl` et ajoutez un délai d’attente à la barre d’état `backend` comme suit :

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## Vérification des en-têtes de réponse HTTP

Vous pouvez maintenant vérifier que Varnish diffuse les pages en examinant les en-têtes de réponse de l’HTML renvoyés depuis n’importe quelle page.

Avant de pouvoir consulter les en-têtes, vous devez définir Commerce pour le mode Développeur. Il existe plusieurs façons de le faire, dont la plus simple consiste à modifier `.htaccess` dans la racine de l’application Commerce. Vous pouvez également utiliser la commande [`magento deploy:mode:set`](../cli/set-mode.md).

### Définition de Commerce pour le mode Développeur

Pour définir Commerce en mode Développeur, utilisez la commande [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode).

### Consultez le journal de vernis

Assurez-vous que le vernis est en cours d’exécution, puis saisissez la commande suivante sur le serveur de vernis :

```bash
varnishlog
```

Dans un navigateur web, accédez à n’importe quelle page Commerce.

Une longue liste d’en-têtes de réponse s’affiche dans la fenêtre de votre invite de commande. Recherchez des en-têtes comme ceux-ci :

```
-   BereqHeader    X-Varnish: 3
-   VCL_call       BACKEND_FETCH
-   VCL_return     fetch
-   BackendOpen    17 default(10.249.151.10,,8080) 10.249.151.10 60914
-   Backend        17 default(10.249.151.10,,8080)
-   Timestamp      Bereq: 1440449534.261791 0.000618 0.000618
-   ReqHeader      Host: 10.249.151.10
-   ReqHeader      Connection: keep-alive
-   ReqHeader      Content-Length: 86
-   ReqHeader      Cache-Control: max-age=0
-   ReqHeader      Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
-   ReqHeader      Origin: http://10.249.151.10
```

Si des en-têtes comme ceux-ci s&#39;affichent _not_, arrêtez Varnish, vérifiez votre `default.vcl`, puis réessayez.

### Vérification des en-têtes de réponse d’HTML

Il existe plusieurs façons d’examiner les en-têtes de réponse, notamment l’utilisation d’un module externe de navigateur ou d’un inspecteur de navigateur.

L’exemple suivant utilise `curl`. Vous pouvez saisir cette commande depuis n’importe quel ordinateur qui peut accéder au serveur Commerce en utilisant HTTP.

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

Par exemple,

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Recherchez des en-têtes comme ceux-ci :

```
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
