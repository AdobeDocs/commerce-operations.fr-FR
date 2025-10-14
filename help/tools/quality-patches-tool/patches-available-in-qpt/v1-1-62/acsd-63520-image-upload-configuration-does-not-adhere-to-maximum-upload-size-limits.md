---
title: 'ACSD-63520 : les images téléchargées via la configuration de téléchargement d’images dépassent les limites de taille configurées'
description: Appliquez le correctif ACSD-63520 pour résoudre le problème d’Adobe Commerce en raison duquel les images chargées par le biais de la configuration de chargement des images dans le panneau d’administration ne respectent pas les limites de taille de chargement maximales configurées.
feature: Media, Products
role: Admin, Developer
exl-id: 5132bfa9-813a-4623-8e02-a8801f6396e8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-63520 : les images téléchargées via [!UICONTROL Image Upload Configuration] dépassent les limites de taille configurées

Le correctif ACSD-63520 résout un problème en raison duquel les images chargées par le biais de l’[!UICONTROL Images Upload Configuration] ne respectent pas les limites de taille de chargement maximales configurées. Pour résoudre ce problème, configurez les paramètres de [!UICONTROL Images Upload Configuration] dans le panneau [!UICONTROL Admin]. Ce correctif est disponible lorsque la version 1.1.62 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63520. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version [!DNL Adobe Commerce], mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les images chargées par le biais du [!UICONTROL Images Upload Configuration] dans le panneau [!UICONTROL Admin] ne respectent pas la taille maximale de chargement.

<u>Procédure à suivre </u> :

1. Connectez-vous au panneau **[!UICONTROL Admin]**.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Images Upload Configuration]** et définissez les éléments suivants :
   * Qualité : 100
   * Activer le redimensionnement front-end : oui
   * Largeur Maximale : 800
   * Hauteur Maximale : 600
1. Développez le **[!UICONTROL Media Gallery Image Optimization]** et définissez :
   * Activer l&#39;optimisation d&#39;image : Oui
   * Largeur Maximale : 1 000
   * Hauteur maximale : 1 000
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Configurable Product]**.
   1. Ajoutez **[!UICONTROL Product Name]**, **[!UICONTROL SKU]** et **[!UICONTROL Price]**.
   1. Cliquez sur **[!UICONTROL Create Configurations]**, sélectionnez **[!UICONTROL Attributes]**, puis cliquez sur **[!UICONTROL Next]**.
   1. Choisissez les tailles (S, M, L, XL), cliquez sur **[!UICONTROL Next]**.
   1. Sous **[!UICONTROL Images]**, sélectionnez **[!UICONTROL Apply single set of images to all SKUs]**.
   1. Chargez une image (minimum 1 024 x 1 024), puis cliquez sur **[!UICONTROL Next]**.
   1. Cliquez sur **[!UICONTROL Generate Product]**.
1. Cliquez sur **[!UICONTROL Save]**.

<u>Résultats attendus</u> :

Les images doivent respecter les limites de taille de chargement et de redimensionnement configurées.

<u>Résultats réels</u> :

Les images ne sont pas redimensionnées et dépassent les limites de taille de chargement configurées.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
