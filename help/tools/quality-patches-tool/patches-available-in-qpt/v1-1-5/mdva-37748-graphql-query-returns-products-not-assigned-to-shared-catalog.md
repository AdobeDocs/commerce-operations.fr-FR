---
title: 'MDVA-37748 : la requête GraphQL renvoie les produits non affectés au catalogue partagé'
description: Le correctif MDVA-37748 corrige le problème où une requête GraphQL renvoie des produits non affectés à un catalogue partagé. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID du correctif est MDVA-37748. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: B2B, GraphQL, Catalog Management, Categories, Products
role: Admin
exl-id: 8aa00953-dbf0-4533-9b53-b809bf59ec20
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-37748 : la requête GraphQL renvoie les produits non affectés au catalogue partagé

Le correctif MDVA-37748 corrige le problème où une requête GraphQL renvoie des produits non affectés à un catalogue partagé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID du correctif est MDVA-37748. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête GraphQL renvoie des produits non affectés à un catalogue partagé.

<u>Conditions préalables</u> :

Les modules B2B sont installés.

<u>Procédure à suivre </u> :

1. Créez deux produits et affectez-les à une catégorie :
   * Produit 1 - Public
   * Produit 2

1. Affectez « Produit 1 - Public » au catalogue partagé « Par défaut (Général) ».
1. Créez un catalogue partagé personnalisé supplémentaire et affectez-le à « Produit 2 ».
1. Créez une nouvelle entreprise et affectez-la au catalogue partagé supplémentaire créé à l’étape 3.
1. Après l’exécution/la réindexation du cron, vérifiez sur le front-end que vous pouvez voir « Produit 1 - Public » si vous n’êtes pas connecté.
1. Connectez-vous en tant qu’administrateur de la société créée à l’étape 4 et vérifiez que vous ne voyez que « Produit 2 ».
1. Demandez un jeton d’autorisation à l’aide de la requête GraphQL suivante :

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      generateCustomerToken(
        email: "company.admin@exapmle.test"
        password: "password"
      ) &lbrace;
        token
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. Ajoutez l’en-tête **Authorization Bearer value-of-the-token** et exécutez la requête GraphQL suivante :

   <pre>
    <code class="language-graphql">
    &lbrace;
      products(
          filter: {},
          pageSize: 100,
          currentPage: 1
          sort: {}
        ) &lbrace;
          total_count
          page_info &lbrace;
            page_size
            current_page
          &rbrace;
          aggregations &lbrace;
            attribute_code
            count
            label
            options &lbrace;
              label
              value
              count
            &rbrace;
          &rbrace;
          items &lbrace;
            name
            sku
            created_at
            updated_at
            stock_status
            description {html}
            short_description {html}
            url_key
            url_path
            price_tiers&lbrace;
              final_price&lbrace;
                  value
                  currency
                &rbrace;
              discount&lbrace;
                  amount_off
                  percent_off
                &rbrace;
              quantity
            &rbrace;
            price_range &lbrace;
             maximum_price &lbrace;
              regular_price &lbrace;
                value
              &rbrace;
              final_price &lbrace;
                value
              &rbrace;
            &rbrace;
            minimum_price &lbrace;
              regular_price &lbrace;
                value
              &rbrace;
              final_price &lbrace;
               value
              &rbrace;
            &rbrace;
          &rbrace;
          image &lbrace;
           url
          &rbrace;
          thumbnail &lbrace;
           url
          &rbrace;
          small_image &lbrace;
           url
          &rbrace;
          media_gallery &lbrace;
           url
          &rbrace;
          ... on ConfigurableProduct &lbrace;
            configurable_options &lbrace;
             id

             label
             position
             use_default
             attribute_code
             values &lbrace;
               value_index
               label
               swatch_data &lbrace;
                 value
               &rbrace;
            &rbrace;
            product_id
          &rbrace;
          variants &lbrace;
            product &lbrace;
              id
              name
              sku
              &#x200B;#margin
              &#x200B;#margin_percentage
              image &lbrace;
                url
              &rbrace;
              small_image &lbrace;
                url
              &rbrace;
              thumbnail &lbrace;
                url
              &rbrace;
              media_gallery&lbrace;
                url
              &rbrace;
              attribute_set_id
              ... on PhysicalProductInterface &lbrace;
                weight
              &rbrace;
              price_range &lbrace;
                minimum_price &lbrace;
                  regular_price &lbrace;
                    value
                    currency
                  &rbrace;
                &rbrace;
              &rbrace;
            &rbrace;
            attributes &lbrace;
              label
              code
              value_index
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;

    &rbrace;
&rbrace;
</code>
</pre>

<u>Résultats attendus</u> :

Le nombre et le produit renvoyés par GraphQL ne prennent en compte que le produit affecté au catalogue partagé associé à l’utilisateur connecté.

<u>Résultats réels</u> :

Seul « Produit 2 » est renvoyé, mais le `total_count` en affiche deux.

<pre>
<code class="language-graphql">
&lbrace;
  "data": &lbrace;
    "products": &lbrace;
      "total_count": 2,
      "page_info": &lbrace;
        "page_size": 100,
        "current_page": 1
      &rbrace;,
      "aggregations": &lbrack;
        &lbrace;
          "attribute_code": "price",
          "count": 2,
          "label": "Price",
          "options": &lbrack;
            &lbrace;
              "label": "0-100",
              "value": "0_100",
              "count": 1
            &rbrace;,
            &lbrace;
              "label": "100-200",
              "value": "100_200",
              "count": 1
            &rbrace;
          &rbrack;
        &rbrace;,
        &lbrace;
          "attribute_code": "category_id",
          "count": 1,
          "label": "Category",
          "options": &lbrack;
            &lbrace;
              "label": "Cat 1",
              "value": "3",
              "count": 2
            &rbrace;
          &rbrack;
        &rbrace;
      &rbrack;,
      "items": &lbrack;
        &lbrace;
          "name": "Product 2",
          "sku": "Product 2",
          "created_at": "2021-05-12 10:51:44",
          "updated_at": "2021-05-12 11:03:24",
          "stock_status": "IN_STOCK",
          "description": &lbrace;
            "html": ""
          &rbrace;,
          "short_description": &lbrace;
            "html": ""
          &rbrace;,
          "url_key": "product-2",
          "url_path": null,
          "price_tiers": &lbrack;
            &lbrace;
              "final_price": &lbrace;
                "value": 90,
                "currency": "USD"
              &rbrace;,
              "discount": &lbrace;
                "amount_off": 10,
                "percent_off": 10
              &rbrace;,
              "quantity": 1
            &rbrace;
          &rbrack;,
          "price_range": &lbrace;
            "maximum_price": &lbrace;
              "regular_price": &lbrace;
                "value": 100
              &rbrace;,
              "final_price": &lbrace;
                "value": 90
              &rbrace;
            &rbrace;,
            "minimum_price": &lbrace;
              "regular_price": &lbrace;
                "value": 100
              &rbrace;,
              "final_price": &lbrace;
                "value": 90
              &rbrace;
            &rbrace;
          &rbrace;,
          "image": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/image.jpg"
          &rbrace;,
          "thumbnail": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/thumbnail.jpg"
          &rbrace;,
          "small_image": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/small_image.jpg"
          &rbrace;,
          "media_gallery": []
        &rbrace;
      &rbrack;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
