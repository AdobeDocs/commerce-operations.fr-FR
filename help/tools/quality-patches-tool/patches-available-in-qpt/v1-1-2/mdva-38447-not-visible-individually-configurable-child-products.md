---
title: 'MDVA-38447 : les produits enfants configurables « Non visibles individuellement » sont renvoyés dans la réponse GraphQL et la requête MySQL est lente'
description: Le correctif Adobe Commerce MDVA-38447 corrige le problème en raison duquel les produits enfants configurables « Non visibles individuellement » sont renvoyés dans la réponse de GraphQL et ralentissent la requête MySQL pour la requête de produits GraphQL avec un filtre de catégorie. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID du correctif est MDVA-38447. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
exl-id: d97297c5-e8e8-407b-b43b-033937426fe2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 1%
---
# MDVA-38447 : les produits enfants configurables « Non visibles individuellement » sont renvoyés dans la réponse GraphQL et la requête MySQL est lente

Le correctif Adobe Commerce MDVA-38447 corrige le problème en raison duquel les produits enfants configurables « Non visibles individuellement » sont renvoyés dans la réponse de GraphQL et ralentissent la requête MySQL pour la requête de produits GraphQL avec un filtre de catégorie. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID du correctif est MDVA-38447. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

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
      name
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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
