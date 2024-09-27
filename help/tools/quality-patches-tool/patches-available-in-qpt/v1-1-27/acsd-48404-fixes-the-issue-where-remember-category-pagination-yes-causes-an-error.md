---
title: "ACSD-48404: *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* entraîne une erreur lors de l’activation du bouton Précédent du navigateur"
description: Appliquez le correctif ACSD-48404 pour résoudre le problème Adobe Commerce où *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* provoque une erreur lors de l’activation du bouton Précédent du navigateur.
feature: Categories
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-48404 : *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* entraîne une erreur lors de l’activation du bouton Précédent du navigateur.

Le correctif ACSD-48404 corrige le problème où *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* provoque une erreur lors de l’activation du bouton Précédent du navigateur. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 est installé. L’ID de correctif est ACSD-48404. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* provoque une erreur lorsque vous appuyez sur le bouton Précédent du navigateur.


<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** et définissez *[!UICONTROL Remember Category Pagination]* sur *Oui*.
1. Ouvrez une catégorie sur le storefront.
1. Sélectionnez une valeur qui n’est pas la valeur par défaut dans la liste déroulante *[!UICONTROL Show Per Page]*. Après avoir sélectionné une option, la page se recharge.
1. Une fois la page rechargée, cliquez sur un produit de la page de catalogue.
1. Sur la page des détails du produit ouverte, cliquez sur le bouton **[!UICONTROL Back]** du navigateur.

<u>Résultats attendus</u> :

La page du catalogue s’ouvre à nouveau.

<u>Résultats réels</u> :

La page de catégorie renvoie une erreur.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
