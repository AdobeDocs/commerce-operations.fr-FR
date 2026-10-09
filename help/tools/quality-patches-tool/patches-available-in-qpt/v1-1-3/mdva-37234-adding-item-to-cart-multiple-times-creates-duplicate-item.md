---
title: 'MDVA-37234 : l’ajout multiple d’articles au panier crée des lignes en double'
description: Le correctif MDVA-37234 corrige le problème en raison duquel l’ajout multiple d’un article au panier (requête parallèle) pour le même SKU crée un élément de ligne en double pour le même ID de panier. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID du correctif est MDVA-37234. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Orders, Shopping Cart
role: Admin
exl-id: d4e9fca1-7fba-4a33-9c5e-c9695cbfc61c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%
---
# MDVA-37234 : l’ajout multiple d’articles au panier crée des lignes en double

Le correctif MDVA-37234 corrige le problème en raison duquel l’ajout multiple d’un article au panier (requête parallèle) pour le même SKU crée un élément de ligne en double pour le même ID de panier. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.3 est installé. L’ID du correctif est MDVA-37234. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.6, 2.4.1 et 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.3.7-p1 et 2.4.1 - 2.4.2-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’ajout multiple d’un article au panier (demande parallèle) pour le même SKU crée un duplicata d’article en ligne pour le même ID de panier.

<u>Procédure à suivre </u> :

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

1. Créez un script pour effectuer deux requêtes `addSimpleProductsToCart` exécutées en parallèle. Par exemple :

   <pre>
    <YOUR_ACCESS_TOKEN><YOUR_CART_ID><YOUR_ACCESS_TOKEN><YOUR_CART_ID>
    </pre>

1. Exécutez le script .

<u>Résultats attendus</u> :

Une seule ligne de produits avec une quantité totale (trois dans ce cas) est créée dans le panier.

<u>Résultats réels</u> :

Deux lignes distinctes pour le même produit sont créées dans le panier.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
