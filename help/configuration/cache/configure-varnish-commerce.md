---
title: Configurer le vernis pour Commerce
description: Découvrez comment mettre à jour et gérer votre fichier de configuration Varnish pour l’application Commerce.
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Configuration de l’application Commerce pour utiliser le vernis

Pour configurer Commerce afin d’utiliser le vernis :

1. Connectez-vous à l’administrateur en tant qu’administrateur.
1. Clic **[!UICONTROL Stores]** > Paramètres > **Configuration** > **Avancé** > **Système** > **Full Page Cache**.
1. À partir du **[!UICONTROL Caching Application]** liste, cliquez sur **Mise en cache du vernis**.
1. Saisissez une valeur dans le champ **[!UICONTROL TTL for public content]** champ .
1. Développer **[!UICONTROL Varnish Configuration]** et renseignez les informations suivantes :

   | Champ | Description |
   | ----- | ----------- |
   | Liste d&#39;accès | Entrez le nom d&#39;hôte complet, l&#39;adresse IP ou [Routage inter-domaines sans classe (CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) notation Plage d’adresses IP pour laquelle le contenu doit être invalidé. Voir [Purge du cache de vernis](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Hôte principal | Entrez le nom d&#39;hôte complet ou l&#39;adresse IP et le port d&#39;écoute du vernis _serveur principal_ ou _serveur d’origine_ En d’autres termes, le serveur qui fournit le contenu Varnish accélère. En règle générale, il s’agit de votre serveur web. Voir [Serveurs principaux du cache de vernis](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Port du serveur principal | Port d’écoute du serveur d’origine. |
   | Délai de grâce | Détermine la durée pendant laquelle le vernis diffuse du contenu obsolète si le serveur principal ne répond pas. La valeur par défaut est de 300 secondes. |
   | Gère la taille des paramètres | Spécifie le nombre maximal de [poignées de mise en page](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles) à traiter sur le [`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) Point d’entrée HTTP pour la mise en cache de toutes les pages. Limiter la taille peut améliorer la sécurité et les performances. La valeur par défaut est 100. |

1. Clic **Enregistrer la configuration**.

Vous pouvez également activer Varnish à partir de la ligne de commande, au lieu de vous connecter à Admin, à l’aide de l’outil d’interface de ligne de commande C :

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Exporter un fichier de configuration de vernis

Pour exporter un fichier de configuration Vernis à partir de l&#39;Admin :

1. Cliquez sur l’un des boutons d’exportation pour créer une `varnish.vcl` vous pouvez utiliser avec le vernis.

   Par exemple, si vous avez Vernis 4, cliquez sur **Exporter VCL pour vernis 4**

   La figure suivante en est un exemple :

   ![Configuration de Commerce pour utiliser le vernis dans l’administration](../../assets/configuration/varnish-admin-22.png)

1. Sauvegarde de votre existant `default.vcl`. Renommez ensuite le `varnish.vcl` fichier vers lequel vous venez d’exporter `default.vcl`. Copiez ensuite le fichier dans le `/etc/varnish/` répertoire.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe vous recommande d’ouvrir `default.vcl` et modifiez la valeur de `acl purge` à l&#39;adresse IP de l&#39;hôte Varnish. (Vous pouvez spécifier plusieurs hôtes sur des lignes distinctes ou vous pouvez également utiliser la notation CIDR.)

   Par exemple,

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Si vous souhaitez personnaliser les contrôles d’intégrité de Vagrant, la configuration du mode de grâce ou du mode saint, voir [Configuration avancée du vernis](config-varnish-advanced.md).

1. Redémarrez Varnish et votre serveur web :

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Mettre en cache les fichiers statiques

Les fichiers statiques ne doivent pas être mis en cache par défaut, mais si vous souhaitez les mettre en cache, vous pouvez modifier la section `Static files caching` dans le VCL pour avoir le contenu suivant :

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Vous devez effectuer ces modifications avant de configurer Commerce pour utiliser le vernis.
