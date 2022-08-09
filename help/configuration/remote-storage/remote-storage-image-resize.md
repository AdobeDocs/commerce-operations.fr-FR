---
title: Configuration du redimensionnement des images pour le stockage à distance
description: Optimisez les ressources disque en configurant le redimensionnement des images côté serveur.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---

# Configuration du redimensionnement des images pour le stockage à distance

Par défaut, [!DNL Commerce] prend en charge le redimensionnement d’image du côté de l’application. Cependant, en activant le module de stockage distant, vous pouvez utiliser Nginx pour décharger le redimensionnement des images côté serveur, où vous pouvez économiser des ressources de disque et optimiser l’utilisation du disque.

Le diagramme suivant montre comment Nginx récupère, redimensionne et stocke les images dans le cache. Le redimensionnement est déterminé par les paramètres inclus dans l’URL, tels que la hauteur et la largeur.

![redimensionnement d’image](../../assets/configuration/remote-storage-nginx-image-resize.png)

## Configuration du format d’URL dans [!DNL Commerce]

Pour redimensionner les images côté serveur, vous devez configurer Commerce afin de fournir des arguments pour la hauteur, la largeur et l’emplacement (URL) de l’image.

**Pour configurer Commerce pour le redimensionnement d’image côté serveur**:

1. Dans le _Administration_ panneau, cliquez sur **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. Dans le volet de droite, développez **[!UICONTROL Url options]**.

1. Dans le _Format d’URL de média de catalogue_ , effacer **[!UICONTROL Use system value]**.

1. Sélectionnez la `Image optimization based on query parameters` URL dans le **_Format d’URL de média de catalogue_** champ .

1. Cliquez sur **[!UICONTROL Save Config]**.

1. Passez à la [Configuration de Nginx](#configure-nginx).

## Configuration de Nginx

Pour continuer à configurer le redimensionnement des images côté serveur, vous devez préparer la `nginx.conf` et fournissez un `proxy_pass` pour l’adaptateur de votre choix.

**Pour permettre à Nginx de redimensionner les images**:

1. Installez le [Module de filtre d’image Nginx][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Créez un `nginx.conf` fichier basé sur le modèle inclus `nginx.conf.sample` fichier . Par exemple :

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

1. [_Facultatif_] Configurez une `proxy_pass` pour votre adaptateur spécifique.

   - [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html