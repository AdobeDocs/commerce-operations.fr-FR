---
title: 'MDVA-39935 : GraphQL renvoie les produits enfants configurables désactivés au niveau du site web »'
description: Le correctif Adobe Commerce MDVA-39935 corrige le problème en raison duquel GraphQL renvoie les produits enfants configurables désactivés au niveau du site web. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID du correctif est MDVA-39935. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: GraphQL, Configuration, Products
role: Admin
exl-id: b86b1595-ddd5-41ce-b126-287046462561
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# MDVA-39935 : GraphQL renvoie les produits enfants configurables désactivés au niveau du site web

Le correctif Adobe Commerce MDVA-39935 corrige le problème en raison duquel GraphQL renvoie les produits enfants configurables désactivés au niveau du site web. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID du correctif est MDVA-39935. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

GraphQL renvoie des produits enfants configurables même après leur désactivation au niveau du site web.

<u>Procédure à suivre </u> :

1. Activez l’option Afficher les produits en rupture de stock sous **Boutique** > **Configuration** > **Catalogue** > **Inventaire** > **Options de stock** > **Afficher les produits en rupture de stock** > **Yes**.
1. Sélectionnez un **produit configurable** qui comporte plus de deux **produits simples**.
1. Désactivez **Produit simple** et enregistrez le **Produit configurable**.
1. Récupérez les données **Produit configurable** à l’aide de GraphQL.

<pre>
  <code class="language-graphql">
&lbrace;
  products(filter: { sku: { eq: "cp1" } }) &lbrace;
    items &lbrace;
      __typename
      name
      sku
      ... on ConfigurableProduct &lbrace;
        variants &lbrace;
          product &lbrace;
            __typename
            name
            sku
            color
            stock_status
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>Résultats attendus</u> :

Les produits désactivés ne sont PAS affichés dans les résultats de la variante.

<u>Résultats réels</u> :

Les données des produits désactivés sont récupérées dans les résultats de la variante.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr).
