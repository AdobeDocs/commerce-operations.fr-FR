---
title: Configuration du vernis pour Commerce
description: Découvrez comment mettre à jour et gérer votre fichier de configuration de vernis pour l’application Commerce.
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Configuration de l’application Commerce pour l’utilisation du vernis

Pour configurer Commerce de sorte qu’il utilise le vernis :

1. Connectez-vous à l’administrateur en tant qu’administrateur.
1. Cliquez sur **[!UICONTROL Stores]** > Paramètres > **Configuration** > **Avancé** > **Système** > **Cache de page complet**.
1. Dans la liste **[!UICONTROL Caching Application]**, cliquez sur **Mise en cache de vernis**.
1. Saisissez une valeur dans le champ **[!UICONTROL TTL for public content]** .
1. Développez **[!UICONTROL Varnish Configuration]** et saisissez les informations suivantes :

   | Champ | Description |
   | ----- | ----------- |
   | Liste d’accès | Saisissez le nom d’hôte complet, l’adresse IP ou la plage d’adresses IP de notation [Classless Inter-domain Routing (CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) pour laquelle invalider le contenu. Voir [Purge du cache vernis](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Hôte principal | Saisissez le nom d’hôte complet ou l’adresse IP et écoutez le port de marque _backend_ ou _origin server_ ; c’est-à-dire que le serveur fournissant le vernis de contenu accélère. En règle générale, il s’agit de votre serveur web. Voir [Serveur principal de cache de vernis](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Port principal | Port d’écoute du serveur d’origine. |
   | Période de grâce | Détermine la durée pendant laquelle Varnish diffuse du contenu obsolète si le serveur principal n’est pas réactif. La valeur par défaut est de 300 secondes. |
   | Gestion de la taille des paramètres | Spécifie le nombre maximal de [gestionnaires de mise en page](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles) à traiter sur le point de terminaison HTTP [`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) pour la mise en cache de la page entière. La limitation de la taille peut améliorer la sécurité et les performances. La valeur par défaut est 100. |

1. Cliquez sur **Enregistrer la configuration**.

Vous pouvez également activer le vernis à partir de la ligne de commande, au lieu de vous connecter à l’administrateur, à l’aide de l’outil d’interface de ligne de commande C :

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Exportation d’un fichier de configuration de vernis

Pour exporter un fichier de configuration de vernis depuis l’administrateur :

1. Cliquez sur l’un des boutons d’exportation pour créer un `varnish.vcl` que vous pouvez utiliser avec du vernis.

   Par exemple, si vous avez le vernis 4, cliquez sur **Export VCL for Varnish 4**

   La figure suivante illustre un exemple :

   ![Configurez Commerce pour utiliser le vernis dans l’Admin](../../assets/configuration/varnish-admin-22.png)

1. Sauvegardez votre `default.vcl` existant. Renommez ensuite le fichier `varnish.vcl` que vous venez d’exporter vers `default.vcl`. Copiez ensuite le fichier dans le répertoire `/etc/varnish/`.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe vous recommande d&#39;ouvrir `default.vcl` et de remplacer la valeur de `acl purge` par l&#39;adresse IP de l&#39;hôte vernis. (Vous pouvez spécifier plusieurs hôtes sur des lignes distinctes ou utiliser également la notation CIDR.)

   Par exemple,

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Si vous souhaitez personnaliser les contrôles d’intégrité Vagrant ou la configuration du mode de grâce ou saint, reportez-vous à la section [Configuration de vernis avancé](config-varnish-advanced.md).

1. Redémarrez le vernis et votre serveur web :

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Fichiers statiques du cache

Les fichiers statiques ne doivent pas être mis en cache par défaut, mais si vous souhaitez les mettre en cache, vous pouvez modifier la section `Static files caching` du VCL pour y afficher le contenu suivant :

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Vous devez apporter ces modifications avant de configurer Commerce pour utiliser le vernis.
