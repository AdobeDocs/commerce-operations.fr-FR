---
title: Configuration du vernis pour Commerce
description: Découvrez comment mettre à jour et gérer votre fichier de configuration de vernis pour l’application Commerce.
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Configuration de l’application Commerce pour l’utilisation du vernis

Pour configurer Commerce de manière à utiliser le vernis :

1. Connectez-vous à l’administrateur en tant qu’administrateur.
1. Cliquez sur **[!UICONTROL Stores]** > Paramètres > **Configuration** > **Avancé** > **Système** > **Cache de page complète**.
1. Dans la **[!UICONTROL Caching Application]** liste, cliquez sur **Mise en cache des Varnières**.
1. Saisissez une valeur dans le champ **[!UICONTROL TTL for public content]** champ .
1. Développer **[!UICONTROL Varnish Configuration]** et saisissez les informations suivantes :

   | Champ | Description |
   | ----- | ----------- |
   | Liste d’accès | Saisissez le nom d’hôte qualifié complet, l’adresse IP ou [Routage interdomaines sans classe (CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) plage d’adresses IP de notation pour laquelle invalider le contenu. Voir [Purge du cache en vernis](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Hôte principal | Saisissez le nom d’hôte complet ou l’adresse IP et le port d’écoute du vernis. _backend_ ou _serveur d’origine_; en d’autres termes, le serveur fournissant le contenu vernis accélère. En règle générale, il s’agit de votre serveur web. Voir [Serveur principal de cache de marque](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Port principal | Port d’écoute du serveur d’origine. |
   | Période de grâce | La période de grâce détermine la durée pendant laquelle Varnish diffuse du contenu obsolète si le serveur principal n’est pas réactif. La valeur par défaut est de 300 secondes. |

1. Cliquez sur **Enregistrer la configuration**.

Vous pouvez également activer le vernis à partir de la ligne de commande, au lieu de vous connecter à l’administrateur, à l’aide de l’outil d’interface de ligne de commande C :

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Exportation d’un fichier de configuration de vernis

Pour exporter un fichier de configuration de vernis depuis l’administrateur :

1. Cliquez sur l’un des boutons d’exportation pour créer un `varnish.vcl` vous pouvez l&#39;utiliser avec du vernis.

   Si, par exemple, vous avez la valeur 4, cliquez sur **Export VCL pour le vernis 4**

   La figure suivante illustre un exemple :

   ![Configuration de Commerce pour l’utilisation du vernis dans l’administration](../../assets/configuration/varnish-admin-22.png)

1. Sauvegardez votre `default.vcl`. Renommez ensuite la variable `varnish.vcl` fichier vers lequel vous venez d’exporter `default.vcl`. Copiez ensuite le fichier dans la fonction `/etc/varnish/` répertoire .

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe vous recommande d’ouvrir `default.vcl` et modifiez la valeur de `acl purge` à l’adresse IP de l’hôte Varnish. (Vous pouvez spécifier plusieurs hôtes sur des lignes distinctes ou utiliser également la notation CIDR.)

   Par exemple :

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Si vous souhaitez personnaliser les contrôles d’intégrité Vagrant, le mode de grâce ou la configuration du mode saint, reportez-vous à la section [Configuration du vernis avancé](config-varnish-advanced.md).

1. Redémarrez le vernis et votre serveur web :

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Fichiers statiques du cache

Les fichiers statiques ne doivent pas être mis en cache par défaut, mais si vous souhaitez les mettre en cache, vous pouvez modifier la section . `Static files caching` dans le VCL pour disposer du contenu suivant :

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Vous devez apporter ces modifications avant de configurer Commerce pour utiliser le vernis.
