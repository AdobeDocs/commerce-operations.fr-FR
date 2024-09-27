---
title: 'ACSD-54739: *[!UICONTROL Product Stock]* statut non appliqué pour *[!UICONTROL Related Product Rules]*'
description: Appliquez le correctif ACSD-54739 pour résoudre le problème Adobe Commerce où l’état *[!UICONTROL Product Stock]* n’est pas appliqué pour *[!UICONTROL Related Product Rules]*.
feature: Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACSD-54739 : état *[!UICONTROL Product stock]* non appliqué pour *[!UICONTROL Related Product Rules]*

Le correctif ACSD-54739 corrige le problème où l’état *[!UICONTROL Product stock]* n’est pas appliqué pour *[!UICONTROL Related Product Rules]*. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 est installé. L’ID de correctif est ACSD-54739. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’état *[!UICONTROL Product stock]* n’est pas appliqué pour *[!UICONTROL Related Product Rules]*.

<u>Étapes à reproduire</u> :

1. Définissez la configuration **[!UICONTROL Display Out of Stock Products]** sur *Oui*.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]** et définissez *Oui* pour la condition de règle promo.
1. Créez la règle de produit associée. Accédez à **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > Ajouter une condition avec une quantité d’attributs (sélectionnez en stock/en rupture de stock).
1. Vérifiez les produits à l’avant-plan.

<u>Résultats attendus</u> :

Le produit en stock/en rupture de stock correspond à *[!UICONTROL Related Product Rules]*.

<u>Résultats réels</u> :

Le produit en stock/en rupture de stock ne correspond pas à celui de *[!UICONTROL Related Product Rules]*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
