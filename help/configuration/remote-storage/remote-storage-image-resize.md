---
title: Configuration du redimensionnement des images pour le stockage distant
description: Optimisez les ressources du disque en configurant le redimensionnement des images côté serveur.
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 1%
---
# Configuration du redimensionnement des images pour le stockage distant

Par défaut, Adobe Commerce prend en charge le redimensionnement des images côté application. Cependant, en activant le module de stockage étendu, vous pouvez utiliser Nginx pour décharger le redimensionnement de l’image côté serveur, où vous pouvez économiser des ressources de disque et optimiser l’utilisation du disque.

Le diagramme suivant montre comment Nginx récupère, redimensionne et stocke les images dans le cache. Le redimensionnement est déterminé par les paramètres inclus dans l’URL, tels que la hauteur et la largeur.

![Configuration de Nginx pour le redimensionnement de l’image du stockage distant affichant les paramètres du bloc serveur](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>Pour les projets d’infrastructure cloud d’Adobe Commerce, consultez [Configuration du stockage distant pour Commerce sur l’infrastructure cloud](cloud-support.md)

## Configuration du format des URL dans Adobe Commerce

Pour redimensionner les images côté serveur, vous devez configurer Adobe Commerce afin de fournir des arguments pour la hauteur, la largeur et l’emplacement (URL) de l’image.

**Pour configurer Commerce pour le redimensionnement d’image côté serveur** :

1. Dans le panneau _Admin_, cliquez sur **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. Dans le volet de droite, développez **[!UICONTROL Url options]**.

1. Dans la section _Format d’URL de média catalogue_, effacez **[!UICONTROL Use system value]**.

1. Sélectionnez l’URL de `Image optimization based on query parameters` dans le champ **_Format d’URL des médias de catalogue_**.

1. Cliquez sur **[!UICONTROL Save Config]**.

1. Passez à la configuration [Nginx](#configure-nginx).

## Configurer Nginx

Pour continuer à configurer le redimensionnement de l&#39;image côté serveur, vous devez préparer le fichier `nginx.conf` et fournir une valeur `proxy_pass` pour la carte choisie.

**Pour permettre à Nginx de redimensionner les images** :

1. Installez le module de filtrage d&#39;image [Nginx](https://nginx.org/en/docs/http/ngx_http_image_filter_module.html).

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Créez un fichier `nginx.conf` basé sur le fichier de `nginx.conf.sample` de modèle inclus. Par exemple :

   ```conf
   location ~* \.(jpg|jpeg|png|gif|webp)$ {
       set $width "-";
       set $height "-";
       if ($arg_width != '') {
           set $width $arg_width;
       }
       if ($arg_height != '') {
           set $height $arg_height;
       }
       image_filter resize $width $height;
       image_filter_jpeg_quality 90;
   }
   ```

1. [_Facultatif_] Configurez une valeur `proxy_pass` pour votre carte spécifique.

   - [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

