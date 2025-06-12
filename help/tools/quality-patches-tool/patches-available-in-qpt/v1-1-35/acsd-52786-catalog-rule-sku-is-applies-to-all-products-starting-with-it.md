---
title: 'ACSD-52786 : la règle de catalogue *[!UICONTROL SKU is]* s’applique à tous les produits commençant par le SKU'
description: Appliquez le correctif ACSD-52786 pour résoudre le problème d’Adobe Commerce où la condition de règle de catalogue *[!UICONTROL SKU is]* s’applique à tous les produits commençant par le SKU donné.
feature: Price Rules
role: Admin
exl-id: 668d5f16-18a9-4054-aa6e-1fb8fa211373
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52786 : la règle de catalogue « *[!UICONTROL SKU is]* » s’applique à tous les produits commençant par le SKU

Le correctif ACSD-52786 corrige le problème où la condition de règle de catalogue *[!UICONTROL SKU is]* s’applique à tous les produits commençant par le SKU donné. Ce correctif est disponible lorsque la version 1.1.35 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-52786. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La condition de règle de catalogue *[!UICONTROL SKU is]* s’applique à tous les produits commençant par le SKU donné.

<u>Procédure à suivre </u> :

1. Créez deux produits, un avec le SKU « 24 » et un autre avec le SKU « 24-MB01 ».
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Appliquez la condition suivante :
   * *[!UICONTROL If ** TOUTES **ces conditions sont** VRAIES **]*: *[!UICONTROL SKU is 24]*
1. Définissez un montant de remise dans les actions.
1. Cliquez sur **[!UICONTROL Save and Apply]**.
1. Videz le cache.
1. Rendez-vous sur le storefront et vérifiez le prix de 24-MB01.

<u>Résultats attendus</u> :

La règle de catalogue est appliquée uniquement à un seul produit avec un SKU égal à 24.

<u>Résultats réels</u> :

La condition de règle de catalogue *[!UICONTROL SKU is]* s’applique à tous les produits commençant par le SKU donné.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
