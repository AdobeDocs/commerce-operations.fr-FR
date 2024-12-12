---
title: 'ACSD-52801 : requête de filtre de produit GraphQL n’affichant pas les résultats de correspondance partielle'
description: Appliquez le correctif ACSD-52801 pour résoudre le problème Adobe Commerce en raison duquel la requête de filtre de produit GraphQL n’affichait pas les résultats de correspondance partielle.
feature: Products
role: Admin, Developer
exl-id: 946a7189-60b2-4812-92ca-ed7ba35b2488
source-git-commit: ec05b041c7af477abd6d3ade6ea95fed5065f2fa
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-52801 : requête de filtre de produit GraphQL n’affichant pas les résultats de correspondance partielle

>[!NOTE]
>
>Un correctif mis à jour ([ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md)) a été publié pour résoudre le même problème pour les versions 2.4.6 - 2.4.6-p8. Il remplace le correctif ACSD-52801 pour les versions 2.4.6 et ultérieures. Pour plus d’informations, voir [ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md).

Le correctif ACSD-52801 corrige le problème en raison duquel la requête de filtre de produit GraphQL n’affichait pas de résultats de correspondance partielle. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 est installé. L’ID de correctif est ACSD-52801. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2, 2.4.5-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête de filtre de produit GraphQL n’affiche pas les résultats de correspondance partielle.

<u>Étapes à reproduire</u> :

1. Installez une instance propre avec des exemples de données.
1. Exécutez la requête GraphQL suivante.

```GraphQL
{
  products(
    filter: { name: { match: "Life" } }
    sort: { position: ASC }
    pageSize: 100
    currentPage: 1
  ) {
    total_count
    items {
      url_key
      sku
      name
      meta_title
    }
  }
}
```

<u>Résultats attendus</u> :

Il permet des résultats de correspondance similaires à ceux de la recherche avancée du storefront en ajoutant l’attribut `match_type` ([!UICONTROL PARTIAL], [!UICONTROL FULL]) pour contrôler les résultats requis. [!UICONTROL FULL] correspond à des mots complets et [!UICONTROL PARTIAL] à des mots partiels comme la vie contenue dans la vie continue.

<u>Résultats réels</u> :

La requête de filtre de produit ne renvoie pas les résultats de correspondances partielles pour les mots-clés de recherche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
