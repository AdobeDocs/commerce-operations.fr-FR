---
title: 'ACSD-48366 : image du produit non affichée sur le modèle de courrier électronique [!UICONTROL Back to Stock]'
description: Appliquez le correctif ACSD-48366 pour résoudre le problème Adobe Commerce en raison duquel l’image de miniature du produit ne s’affiche pas dans l’e-mail d’alerte de stock du produit.
feature: Admin Workspace, Communications, Orders, Products
role: Admin
exl-id: a721f399-f50a-4a13-9f5d-17ae7f3985f6
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48366 : image du produit non affichée sur le modèle de courrier électronique [!UICONTROL Back to Stock]

Le correctif ACSD-48366 corrige le problème en raison duquel l’image de miniature du produit ne s’affiche pas dans l’e-mail d’alerte du produit. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 est installé. L’ID de correctif est ACSD-48366. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’image du produit ne s’affiche pas dans le modèle d’email [!UICONTROL Back to Stock].

<u>Étapes à reproduire</u> :

1. Activez *[!UICONTROL Product Alert]* pour *[!UICONTROL Back in Stock]* en accédant à **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]*.
1. Activez *[!UICONTROL Display Out of Stock Products]* en accédant à **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]*.
1. Créez un produit simple avec qty = 0.
1. Créez un client à partir du storefront et abonnez-vous au produit ci-dessus pour obtenir des alertes de produit lorsqu’il est en stock.
1. Faites le produit en stock.
1. Exécutez le cron d’alerte du produit.

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Lancez l’alerte de produit pour le client.

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. Vérifiez l&#39;email. Le message d’alerte Stock doit maintenant être disponible dans le receveur de courrier.

<u>Résultats attendus</u> :

L’image du produit s’affiche dans l’email d’alerte de stock.

<u>Résultats réels</u> :

L’image du produit n’est pas disponible dans l’email d’alerte de stock.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
