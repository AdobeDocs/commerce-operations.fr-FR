---
title: 'ACSD-65100 : la suppression des valeurs [!UICONTROL Maximum Width] et [!UICONTROL Maximum Height] dans la configuration [!UICONTROL Media Gallery Image Optimization] entraîne une erreur'
description: Appliquez le correctif ACSD-65100 pour résoudre le problème d’Adobe Commerce où la suppression des valeurs [!UICONTROL Maximum Width] et [!UICONTROL Maximum Height] dans la configuration [!UICONTROL Media Gallery Image Optimization] entraîne une erreur lors du processus d’optimisation de l’image.
feature: Media
role: Admin, Developer
source-git-commit: 97ffcd84b760962e1ad7290343f81860ca6568c7
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# ACSD-65100 : la suppression des valeurs [!UICONTROL Maximum Width] et [!UICONTROL Maximum Height] dans la configuration [!UICONTROL Media Gallery Image Optimization] entraîne une erreur

Le correctif ACSD-65100 corrige le problème en raison duquel la suppression des valeurs **[!UICONTROL Maximum Width]** et **[!UICONTROL Maximum Height]** dans la configuration **[!UICONTROL Media Gallery Image Optimization]** entraîne une erreur lors du processus d’optimisation des images. Ce correctif est disponible lorsque la version 1.1.64 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65100. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-P5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur se produit pendant le processus d’optimisation d’image lorsque les valeurs de **[!UICONTROL Maximum Width]** et **[!UICONTROL Maximum Height]** sont supprimées dans la configuration de **[!UICONTROL Media Gallery Image Optimization]**.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery Image Optimization]**.
1. Supprimez les valeurs de **[!UICONTROL Maximum Width]** et **[!UICONTROL Maximum Height]**.
1. Nettoyez le cache de configuration.
1. Accédez à **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**.
1. Ouvrez n’importe quelle page à modifier.
1. Dans la zone de contenu :
   1. Sélectionnez **[!UICONTROL Add Layout]** > **[!UICONTROL Row]**.
   1. Sélectionnez **[!UICONTROL Add Elements]** > **[!UICONTROL Text]**.
   1. Dans l’éditeur de WYSIWYG, cliquez sur **[!UICONTROL Add Image]**.
   1. Chargez une image et sélectionnez-la **[!UICONTROL Add Selected]**.
1. Vérifiez le fichier `var/log/exception.log`.

<u>Résultats attendus</u> :

Aucune erreur.

<u>Résultats réels</u> :

Une erreur similaire à la suivante est consignée :

```
report.ERROR: InvalidArgumentException: Invalid image dimensions. in /var/www/html/vendor/magento/framework/Image/Adapter/AbstractAdapter.php:630
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
