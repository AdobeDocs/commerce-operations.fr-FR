---
title: 'MDVA-38447 : les produits enfants configurables « Non visibles individuellement » sont renvoyés dans la réponse GraphQL et la requête MySQL est lente'
description: Le correctif Adobe Commerce MDVA-38447 corrige le problème en raison duquel les produits enfants configurables « Non visibles individuellement » sont renvoyés dans la réponse de GraphQL et ralentissent la requête MySQL pour la requête de produits GraphQL avec un filtre de catégorie. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID du correctif est MDVA-38447. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
exl-id: d97297c5-e8e8-407b-b43b-033937426fe2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-38447 : les produits enfants configurables « Non visibles individuellement » sont renvoyés dans la réponse GraphQL et la requête MySQL est lente

Le correctif Adobe Commerce MDVA-38447 corrige le problème en raison duquel les produits enfants configurables « Non visibles individuellement » sont renvoyés dans la réponse de GraphQL et ralentissent la requête MySQL pour la requête de produits GraphQL avec un filtre de catégorie. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID du correctif est MDVA-38447. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits enfants configurables « Non visibles individuellement » sont renvoyés dans la réponse GraphQL et la requête MySQL lente pour la requête de produits GraphQL avec le filtre de catégorie.

<u>Conditions préalables</u> :

Les modules B2B doivent être installés.

<u>Procédure à suivre </u> :

1. Créez un produit configurable avec des produits simples définis sur **Non visibles individuellement**.
1. Exécutez une **réindexation complète**.
1. Exécutez une requête GraphQL **** comme suit :

<pre>requête getFilteredProducts(
  $filter : ProductAttributeFilterInput !
  $sort : ProductAttributeSortInput !
  $search : chaîne
  $pageSize: Int!
  $currentPage : Int !
) {
  products(
    filter : $filter
    sort : $sort
    recherche : $search
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
      nom
      sku
    }
  }
}</pre>

Variables :

<pre>{« filter »:{« user_group »:{« eq »:« }},« search »:« config-100 »,« sort »:{},« pageSize »:200,« currentPage »:1}
</pre>

<u>Résultats attendus</u> :

Les produits dont la visibilité est définie sur « Non visible individuellement » ne seront pas renvoyés en réponse.

<u>Résultats réels</u> :

Les produits dont la visibilité est définie sur « Non visibles individuellement » sont renvoyés en réponse.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
