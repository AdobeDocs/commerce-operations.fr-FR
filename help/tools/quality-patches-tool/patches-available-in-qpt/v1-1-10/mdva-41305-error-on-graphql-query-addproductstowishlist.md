---
title: 'MDVA-41305 : erreur sur la requête GraphQL addProductsToWishlist pour les produits configurables.'
description: Le correctif MDVA-41305 résout le problème où les utilisateurs et utilisatrices obtiennent une erreur sur la requête GraphQL « addProductsToWishlist » pour les produits configurables. Ce correctif est disponible lorsque l’[Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 est installé. L’ID du correctif est MDVA-41305. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: GraphQL, Configuration, Products
role: Admin
exl-id: 985c3c46-d2c8-4479-b9e4-e5f9504ab03b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-41305 : erreur sur la requête GraphQL addProductsToWishlist pour les produits configurables.

Le correctif MDVA-41305 résout le problème où les utilisateurs et utilisatrices obtiennent une erreur lors de l’`addProductsToWishlist` de requêtes GraphQL pour les produits configurables. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 est installé. L’ID du correctif est MDVA-41305. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque les utilisateurs ajoutent des produits configurables (avec ou sans configuration) à la liste de souhaits de GraphQL, ils ne peuvent pas obtenir de SKU configurables et d’options configurables en réponse.

<u>Procédure à suivre </u> :

1. Créez un produit configurable (avec l’option bleue, grise et une option personnalisée).
1. Ouvrez front-end ; connectez-vous en tant que client et créez une liste de souhaits (vérifiez wishlist_id).
1. Ouvrez Postman et créez un jeton client :

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      generateCustomerToken(email: "", password: "") &lbrace;
        token
      &rbrace;
     &rbrace;
     </code>
     </pre>

1. Définissez ce jeton pour l’autorisation du porteur.
1. Essayez d’ajouter un produit configurable *bleu* à la liste de souhaits en suivant les instructions ci-dessous :

<pre>
<code class="language-graphql">
mutation &lbrace;
 addProductsToWishlist(
   wishlistId: 1
   wishlistItems: &lbrack;
     &lbrace;
       sku: "conf2"
       selected_options: &lbrack;
            "Y29uZmlndXJhYmxlLzkzLzUw"
       &rbrack;
       quantity: 1
       entered_options: &lbrack;
         &lbrace;
           uid: "Y3VzdG9tLW9wdGlvbi8x"
           value: "test"
         &rbrace;
       &rbrack;
     &rbrace;
    &rbrack;
  ) &lbrace;
    wishlist &lbrace;
      id
      items_count
      items_v2 (currentPage: 1, pageSize: 8 ) &lbrace;
        items &lbrace;
         id
         quantity
         ... on ConfigurableWishlistItem  &lbrace;
           child_sku
           customizable_options &lbrace;
             customizable_option_uid
           &rbrace;
         &rbrace;
         product &lbrace;
           uid
           name
           sku
           options_container
           ... on CustomizableProductInterface &lbrace;
             options &lbrace;
              title
              required
              sort_order
              option_id
              ... on CustomizableFieldOption &lbrace;
                value &lbrace;
                  uid
                  sku
                  price
                  price_type
                  max_characters
                &rbrace;
              &rbrace;
            &rbrace;
          &rbrace;
          price_range &lbrace;
            minimum_price &lbrace;
              regular_price &lbrace;
                currency
                value
              &rbrace;
            &rbrace;
            maximum_price &lbrace;
               regular_price &lbrace;
                 currency
                 value
               &rbrace;
             &rbrace;
           &rbrace;
         &rbrace;
       &rbrace;
     &rbrace;
   &rbrace;
  user_errors &lbrace;
    code
    message
   &rbrace;
 &rbrace;
&rbrace;
</code>
</pre>

<u>Résultats attendus</u> :

Les utilisateurs peuvent voir un ensemble d’options de produit configurées dans la réponse spécifiée dans la payload et ajoutée à la liste de souhaits.

<u>Résultats réels</u> :

Les utilisateurs reçoivent en réponse une *Erreur de serveur interne*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
