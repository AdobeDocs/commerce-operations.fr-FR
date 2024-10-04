---
title: "ACSD-49370 : l’attribut de produit a le type 'FilterMatchTypeInput' dans le schéma GraphQL"
description: Appliquez le correctif ACSD-49370 pour résoudre le problème Adobe Commerce où l’attribut de produit a un type "FilterMatchTypeInput" dans le schéma GraphQL.
feature: Admin Workspace, Attributes, GraphQL, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-49370 : l’attribut de produit est de type `FilterMatchTypeInput` dans le schéma GraphQL

Le correctif ACSD-49370 corrige le problème lorsque l’attribut de produit a un type `FilterMatchTypeInput` dans le schéma GraphQL. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 est installé. L’ID de correctif est ACSD-49370. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’attribut de produit a un type `FilterMatchTypeInput` dans le schéma GraphQL.

<u>Étapes à reproduire</u> :

1. Créez l’attribut de produit *Date et heure*.

   * [!UICONTROL Type] : [!UICONTROL DateTime]
   * [!UICONTROL Default Label] : [!UICONTROL Date Time]
   * [!UICONTROL Use in Search] : [!UICONTROL Yes]
   * [!UICONTROL Visible in Advanced Search] : [!UICONTROL Yes]

1. Recherchez la documentation *API GQL* pour la définition de type `ProductAttributeFilterInput`.
1. Observez le type d’entrée pour l’attribut créé.

<u>Résultats attendus</u> :

L’attribut *Date Time* affiche le type d’entrée de filtre `FilterRangeTypeInput`.

<u>Résultats réels</u> :

L’attribut *Date Time* affiche le type d’entrée de filtre `FilterMatchInputType`.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].