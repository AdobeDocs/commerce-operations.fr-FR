---
title: 'MDVA-43348 : la demande de GraphQL de carte cadeau affiche une erreur'
description: Le correctif MDVA-43348 corrige le problème en raison duquel la requête de GraphQL de carte cadeau affiche une erreur si « gift_card_options » contient « uid ». Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-43348. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Gift, GraphQL
role: Admin
exl-id: 94cb939a-fad2-4f01-a641-d8d5b656d931
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# MDVA-43348 : la demande de GraphQL de carte cadeau affiche une erreur

Le correctif MDVA-43348 corrige le problème en raison duquel la requête de GraphQL de carte cadeau affiche une erreur si `gift_card_options` contient « uid ». Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-43348. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La demande de GraphQL de carte cadeau affiche une erreur si les options_carte_cadeau contiennent « uid ».

<u>Procédure à suivre </u> :

1. Créez un produit de carte cadeau.
1. Effectuez la réindexation.
1. Effectuez un appel GraphQL où la clé URL est « chèque-cadeau » :

<pre>
<code class="language-graphql">
query getProductOptionsForProductPage_bypassFastly($urlKey: String!) &lbrace;
  products(filter: { url_key: { eq: $urlKey } }) &lbrace;
    items &lbrace;
      id
      url_key
      ... on GiftCardProduct &lbrace;
        allow_open_amount
        open_amount_min
        open_amount_max
        giftcard_type
        is_redeemable
        lifetime
        allow_message
        message_max_length
        gift_card_options &lbrace;
          uid
          title
          required
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>Résultats attendus</u> :

Les données de la carte cadeau sont retournées sur demande.

<u>Résultats réels</u> :

L’erreur suivante se produit lors de la demande des données de carte cadeau :

<pre>
<code class="language-graphql">
&lbrace;
  "errors": &lbrack;
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        0,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        1,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        2,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        3,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        4,
        "uid"
      &rbrack;
    &rbrace;
  &rbrack;,
  "data": &lbrace;
    "products": &lbrace;
      "items": &lbrack;
        &lbrace;
          "id": 2,
          "url_key": "gitf-card",
          "allow_open_amount": false,
          "open_amount_min": null,
          "open_amount_max": null,
          "giftcard_type": "VIRTUAL",
          "is_redeemable": true,
          "lifetime": 0,
          "allow_message": true,
          "message_max_length": 255,
          "gift_card_options": &lbrack;
            null,
            null,
            null,
            null,
            null
          &rbrack;
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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
