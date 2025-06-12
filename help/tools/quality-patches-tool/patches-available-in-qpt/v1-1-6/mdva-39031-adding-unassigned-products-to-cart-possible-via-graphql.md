---
title: 'MDVA-39031 : ajout possible de produits non affectés au panier via GraphQL'
description: Le correctif MDVA-39031 résout le problème où l’ajout d’un produit au panier via GraphQL est possible même s’il n’est pas attribué au site web cible. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID du correctif est MDVA-39031. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
exl-id: 6250c6f6-b74b-4713-a704-d252270693d4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-39031 : ajout possible de produits non affectés au panier via GraphQL

Le correctif MDVA-39031 résout le problème où l’ajout d’un produit au panier via GraphQL est possible même s’il n’est pas attribué au site web cible. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID du correctif est MDVA-39031. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’ajout d’un produit au panier via GraphQL est possible même s’il n’est pas attribué au site web cible.

<u>Procédure à suivre </u> :

1. Créez un site web secondaire.
1. Créez un produit et affectez-le au site web principal.
1. Créez un panier vide pour le site web secondaire à l’aide de GraphQL.

   <pre>
    <code class="language-graphql">
    mutation&lbrace;
     createEmptyCart
    &rbrace;
    </code>
    </pre>

   Avec des en-têtes tels que :

   <pre>
    <code class="language-graphql">
    &lbrace;
      "Store":"en_au"
    &rbrace;
    </code>
    </pre>

1. Ajoutez le produit affecté au site web principal au panier dans le site web secondaire.

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      addProductsToCart(
          cartId: "XHrUN2nJ37OqDByhtL0VC8OxYsEZs41c"
          cartItems: &lbrack;
            &lbrace;
              quantity: 1
              sku: "p1"
            &rbrace;
          &rbrack;
        ) &lbrace;
          cart &lbrace;
           items &lbrace;
            product &lbrace;
              name
              sku
            &rbrace;
            quantity
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

   En-têtes

   <pre>
    <code class="language-graphql">
    &lbrace;
      "Store":"en_au"
    &rbrace;
    </code>
    </pre>

<u>Résultats attendus</u> :

Le produit n’est pas ajouté au panier, car il n’a pas été affecté au magasin défini dans l’en-tête .

<u>Résultats réels</u> :

Le produit est correctement ajouté au panier.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
