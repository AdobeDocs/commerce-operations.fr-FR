---
title: "MDVA-37234 : l’ajout d’un article dans le panier plusieurs fois crée un article en double"
description: Le correctif MDVA-37234 corrige le problème en raison duquel l’ajout d’un élément au panier plusieurs fois (requête parallèle) pour le même SKU crée un élément de ligne dupliqué pour le même ID de panier. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID de correctif est MDVA-37234. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-37234 : l’ajout de plusieurs fois d’un article dans le panier crée un article en double.

Le correctif MDVA-37234 corrige le problème en raison duquel l’ajout d’un élément au panier plusieurs fois (requête parallèle) pour le même SKU crée un élément de ligne dupliqué pour le même ID de panier. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID de correctif est MDVA-37234. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.6, 2.4.1 et 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.3.7-p1 et 2.4.1 - 2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’ajout d’un élément au panier à plusieurs reprises (requête parallèle) pour le même SKU crée un élément de ligne dupliqué pour le même ID de panier.

<u>Étapes à reproduire</u> :

1. Créez un produit simple avec SKU = simple1.
1. Créez un client.
1. Générez un jeton client pour effectuer une requête GraphQL.

   <pre>
    <code class="language-graphql">
    mutation {
        generateCustomerToken(
            email: "customer email"
            password: "customer password"
        )
        {
            token
        }
    }
    </code>
    </pre>

1. Utilisez le jeton mentionné à l’étape 3 pour créer un panier vide pour le client.

   <pre>
    <code class="language-graphql">
    mutation{
     createEmptyCart
    }
    </code>
    </pre>

1. Créez un script pour exécuter deux requêtes `addSimpleProductsToCart` en parallèle. Par exemple :

   <pre>
    <code class="language-#!/bin/bash">
    curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MywiaWF0IjoxNjIzOTUyNjcwLCJleHAiOjE2MjM5NTYyNzB9.-fh7ysqiQTAacdB3MVvaXzFE9AmKyfF8TsVmICLJoWI" -d '{"query" : "mutation { addSimpleProductsToCart( input: { cart_id: \"S8dCF7uan1POMy0qY0Hup7tEv1AhFGdY\" cart_items: [ { data: { quantity: 2 sku: \"simple1\" } } ] } ) { cart { items { id product { name sku } quantity } } } }"}' http://magento2.3.local/graphql &
    curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MywiaWF0IjoxNjIzOTUyNjcwLCJleHAiOjE2MjM5NTYyNzB9.-fh7ysqiQTAacdB3MVvaXzFE9AmKyfF8TsVmICLJoWI" -d '{"query" : "mutation { addSimpleProductsToCart( input: { cart_id: \"S8dCF7uan1POMy0qY0Hup7tEv1AhFGdY\" cart_items: [ { data: { quantity: 1 sku: \"simple1\" } } ] } ) { cart { items { id product { name sku } quantity } } } }"}' http://magento2.3.local/graphql
    </code>
    </pre>

1. Exécutez le script.

<u>Résultats attendus</u> :

Une seule ligne de produit avec une quantité totale (ici trois) est créée dans le panier.

<u>Résultats réels</u> :

Deux lignes distinctes pour le même produit sont créées dans le panier.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

* [Outil de correctifs de qualité publié : un nouvel outil pour appliquer des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html-) .
