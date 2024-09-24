---
title: '''MDVA-38447: "Non visible individuellement" les produits enfants configurables sont renvoyés dans la réponse GraphQL et la requête MySQL lente"'
description: Le correctif Adobe Commerce MDVA-38447 corrige le problème en raison duquel les produits enfants configurables "Non visibles individuellement" sont renvoyés dans la réponse GraphQL et la requête MySQL lente pour les produits GraphQL avec filtre de catégorie. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID de correctif est MDVA-38447. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-38447 : les produits enfants configurables &quot;non visibles individuellement&quot; sont renvoyés dans la réponse GraphQL et la requête MySQL lente.

Le correctif Adobe Commerce MDVA-38447 corrige le problème en raison duquel les produits enfants configurables &quot;Non visibles individuellement&quot; sont renvoyés dans la réponse GraphQL et la requête MySQL lente pour les produits GraphQL avec filtre de catégorie. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID de correctif est MDVA-38447. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits enfants configurables &quot;non visibles individuellement&quot; sont renvoyés dans la réponse GraphQL et la requête MySQL lente pour les produits GraphQL avec filtre de catégorie.

<u>Conditions préalables</u> :

Les modules B2B doivent être installés.

<u>Étapes à reproduire</u> :

1. Créez un produit configurable avec des produits simples définis sur **Non visible individuellement**.
1. Exécutez une **réindexation complète**.
1. Exécutez une **requête GraphQL** comme :

<pre>query getFilteredProducts(
  $filter : ProductAttributeFilterInput!
  $sort: ProductAttributeSortInput!
  $search: String
  $pageSize: Int!
  $currentPage : Int!
) {
  products(
    filter : $filter
    sort : $sort
    search: $search
    pageSize : $pageSize
    currentPage : $currentPage
  ) {
    total_count
    page_info {
      total_pages
      current_page
      page_size
    }
    items {
      name
      sku
    }
  }
}</pre>

Variables :

<pre>{"filter":{"user_group":{"eq":""},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>Résultats attendus</u> :

Les produits dont la visibilité est définie sur &quot;Non visible individuellement&quot; ne seront pas renvoyés en réponse.

<u>Résultats réels</u> :

Les produits dont la visibilité est définie sur &quot;Non visible individuellement&quot; sont renvoyés en réponse.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

* [Outil de correctifs de qualité publié : un nouvel outil pour appliquer des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html-) .
