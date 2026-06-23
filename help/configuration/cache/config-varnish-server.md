---
title: Configurer les nœuds pour la mise en cache du vernis
description: Découvrez comment configurer votre serveur web pour qu’il fonctionne avec la mise en cache de vernis pour Adobe Commerce. Découvrez la configuration et les exigences de configuration des ports.
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
badgePaas: label="Sur Site" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets sur site Adobe Commerce."
autotag-review: '2026-06-22T21:49:41.837Z'
TQID: 'https://experienceleague.adobe.com/0vOg86gRkST8CZGhdIESzhld63HQ5IUlO4go-Hgw9Xs'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: c8faa589c9e9d1dbc01863d90aad5f91b11c0140
workflow-type: tm+mt
source-wordcount: 806
ht-degree: 0%

---

# Configurer les onglets pour la mise en cache du vernis {#configure-web-server-for-varnish-caching}

Lorsque Varnish est utilisé comme cache de pleine page devant Adobe Commerce, il écoute généralement sur le port HTTP public et transfère les requêtes à nginx sur un port principal autre que le port par défaut, tel que 8080. Mettez à jour la configuration du site nginx pour que votre serveur d’origine Commerce écoute sur le port principal que Varnish utilisera.

{{varnish-config-cloud}}

Les sections suivantes utilisent le port 8080 comme exemple.

**Modifiez le port d’écoute nginx pour le serveur Commerce origin** :

1. Ouvrez la configuration du site nginx pour votre serveur Adobe Commerce origin dans un éditeur de texte.

L’emplacement dépend de votre système d’exploitation et de la mise en page du moteur. Par exemple, Ubuntu utilise souvent un fichier sous `/etc/nginx/sites-available/`.

1. Dans le bloc `server` pour le site Commerce, modifiez la directive `listen` du port HTTP public au port principal que Varnish utilisera pour atteindre nginx.

   Par exemple, modifier

   ```conf
   server {
       listen 80;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   vers :

   ```conf
   server {
       listen 8080;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

1. Enregistrez le fichier.

1. Vérifiez la configuration nginx :

   ```shell
   nginx -t
   ```

1. Redémarrez Angles :

   ```shell
   systemctl restart nginx
   ```

## Modifier la configuration du système de vernis

Après avoir mis à jour nginx pour écouter sur le port principal, configurez Varnish pour transférer les requêtes vers cet hôte et ce port. Par exemple :

```conf
backend default {
    .host = "192.0.2.55";
    .port = "8080";
}
```

### Modifier le VCL par défaut

Cette section explique comment fournir une configuration minimale pour que Varnish renvoie des en-têtes de réponse HTTP. Cela vous permet de vérifier que le vernis fonctionne avant de configurer l&#39;application [!DNL Commerce] pour l&#39;utiliser.

Pour configurer le vernis de manière minimale :

1. Sauvegarde `default.vcl` :

   ```shell
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. Ouvrez `/etc/varnish/default.vcl` dans un éditeur de texte.
1. Localisez la strate suivante :

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. Remplacez la valeur de `.host` par le nom d’hôte complet ou l’adresse IP et le port d’écoute du Varnish _serveur principal_ ou _serveur d’origine_ ; en d’autres termes, le serveur qui fournit le contenu Varnish s’accélérera.

   En règle générale, il s’agit de votre serveur web. Voir [Serveurs principaux](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) dans le guide _Vernis_.

1. Remplacez la valeur de `.port` par le port d’écoute du serveur web (8080 dans cet exemple).

   Exemple : nginx est installé sur l&#39;hôte 192.0.2.55 et écoute sur le port 8080 :

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Si Varnish et nginx sont exécutés sur le même hôte, Adobe vous recommande d’utiliser une adresse IP ou un nom d’hôte et non `localhost`.

1. Enregistrez vos modifications dans `default.vcl` et quittez l’éditeur de texte.

1. Redémarrer le vernis :

   ```shell
   service varnish restart
   ```

Si Varnish ne démarre pas, essayez de l’exécuter à partir de la ligne de commande comme suit :

```shell
varnishd -d -f /etc/varnish/default.vcl
```

Cela devrait afficher des messages d’erreur.


>[!INFO]
>
>Si Varnish ne démarre pas en tant que service, vous devez configurer les règles SELinux pour permettre son exécution.

## Vérifier que le vernis fonctionne

Les sections suivantes expliquent comment vérifier que Varnish fonctionne mais _sans_ configurer Commerce pour l’utiliser. Vous devez essayer ceci avant de configurer Commerce.

Effectuez les tâches décrites dans les sections suivantes dans l’ordre indiqué :

- [Commencer le vernis](#start-varnish)
- [`netstat`](#netstat)

### Commencer le vernis

Enter : `service varnish start`

Si Varnish ne démarre pas en tant que service, démarrez-le à partir de la ligne de commande comme suit :

1. Démarrez l’interface de ligne de commande du vernis :

   ```shell
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Démarrez le processus enfant Vernis :

   À l’invite, saisissez `start`

   Les messages suivants s’affichent pour confirmer un démarrage réussi :

   ```text
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Connectez-vous au serveur Varnish et saisissez la commande suivante :

```shell
netstat -tulpn
```

Recherchez en particulier le résultat suivant :

```text
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/nginx
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

La figure précédente montre Varnish s&#39;exécutant sur le port 80 et nginx s&#39;exécutant sur le port 8080.

Si vous ne voyez pas de sortie pour `varnishd`, assurez-vous que le vernis est en cours d’exécution.

Voir [`netstat` options](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Installation du logiciel Commerce

Installez le logiciel Commerce si vous ne l’avez pas déjà fait. Lorsque vous êtes invité à saisir une URL de base, utilisez l’hôte et le port Varnish 80 (pour Varnish), car Varnish reçoit toutes les requêtes HTTP entrantes.

Erreur possible lors de l’installation de Commerce :

```text
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

Si vous rencontrez cette erreur, modifiez les `default.vcl` et ajoutez un délai d’expiration à la stature `backend` comme suit :

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## Vérifier les en-têtes de réponse HTTP

Vous pouvez maintenant vérifier que Varnish diffuse des pages en examinant les en-têtes de réponse HTML renvoyés depuis n’importe quelle page.

Avant de pouvoir consulter les en-têtes, vous devez définir Commerce pour le mode Développeur. Il existe plusieurs façons de le faire, la plus simple étant de modifier les `.htaccess` à la racine de l’application Commerce. Vous pouvez également utiliser la commande [`magento deploy:mode:set`](../cli/set-mode.md).

### Définition de Commerce pour le mode Développeur

Pour définir Commerce en mode Développeur, utilisez la commande [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode).

### Regarde le journal du vernis

Assurez-vous que Varnish est en cours d’exécution, puis saisissez la commande suivante sur le serveur Varnish :

```shell
varnishlog
```

Dans un navigateur web, accédez à n’importe quelle page Commerce.

Une longue liste d’en-têtes de réponse s’affiche dans votre fenêtre d’invite de commande. Recherchez des en-têtes comme ceux-ci :

```text
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

Si des en-têtes comme ceux-ci ne s _affichent pas_ arrêtez Varnish, vérifiez votre `default.vcl` et réessayez.

### Examiner les en-têtes de réponse HTML

Il existe plusieurs façons d’examiner les en-têtes de réponse, y compris à l’aide d’un module externe de navigateur ou d’un inspecteur de navigateur.

L’exemple suivant utilise `curl`. Vous pouvez saisir cette commande à partir de n’importe quel ordinateur pouvant accéder au serveur Commerce à l’aide du protocole HTTP.

```shell
curl -I -v --location-trusted '<your Commerce base URL>'
```

Par exemple,

```shell
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Recherchez des en-têtes comme ceux-ci :

```text
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
