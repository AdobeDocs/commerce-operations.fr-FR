---
title: 'ACSD-48366 : image du produit non affichée sur [!UICONTROL Back to Stock] modèle d’e-mail'
description: Appliquez le correctif ACSD-48366 pour résoudre le problème d’Adobe Commerce en raison duquel l’image miniature du produit n’est pas affichée dans l’e-mail d’alerte de stock du produit.
feature: Admin Workspace, Communications, Orders, Products
role: Admin
exl-id: a721f399-f50a-4a13-9f5d-17ae7f3985f6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48366 : image du produit non affichée sur [!UICONTROL Back to Stock] modèle d’e-mail

Le correctif ACSD-48366 corrige le problème en raison duquel l’image miniature du produit n’est pas affichée dans l’e-mail d’alerte de stock du produit. Ce correctif est disponible lorsque la version 1.1.26 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48366. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’image du produit ne s’affiche pas dans le modèle d’e-mail [!UICONTROL Back to Stock].

<u>Procédure à suivre </u> :

1. Activez *[!UICONTROL Product Alert]* pour *[!UICONTROL Back in Stock]* en accédant à **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]*.
1. Activez *[!UICONTROL Display Out of Stock Products]* en accédant à **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]*.
1. Créez un produit simple avec qté = 0.
1. Créez un client à partir du storefront et abonnez-vous au produit ci-dessus pour obtenir des alertes de produit lorsqu’il est en stock.
1. Mettre le produit en stock.
1. Exécutez le cron d’alerte du produit.

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Démarrer l’alerte produit pour le client.

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. Vérifiez l’e-mail. L’e-mail d’alerte de stock doit maintenant être disponible dans le collecteur de messages.

<u>Résultats attendus</u> :

L’image du produit s’affiche dans l’e-mail d’alerte de stock.

<u>Résultats réels</u> :

L’image du produit n’est pas disponible dans l’e-mail d’alerte de stock.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
