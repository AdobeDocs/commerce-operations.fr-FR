---
title: 'ACSD-52921 : erreur de demande des détails du panier à GraphQL pour le produit configurable en rupture de stock.'
description: Appliquez le correctif ACSD-52921 pour résoudre le problème d’Adobe Commerce en raison duquel une erreur interne se produit lors de la demande des détails du panier à GraphQL pour un produit configurable en rupture de stock.
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 7790718a-6b86-497e-b1a1-88ba22c3e8ff
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-52921 : erreur de demande des détails du panier à GraphQL pour le produit configurable en rupture de stock.

Le correctif ACSD-52921 corrige le problème où une erreur interne se produit lors de la demande des détails du panier à GraphQL pour un produit configurable en rupture de stock. Ce correctif est disponible lorsque la version 1.1.35 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-52921. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur interne se produit lors de la demande des détails du panier à GraphQL pour un produit configurable en rupture de stock.

<u>Procédure à suivre </u> :

1. Créez un produit configurable avec quelques options.
1. Ajoutez une option pour le produit configurable ci-dessus au panier à partir du front-end (passage en caisse des invités).
1. Récupérez le `[ masked_id ]` de la table de base de données `[ quote_id_mask ]` pour le devis créé ci-dessus.
1. Exécutez la requête GraphQL suivante pour obtenir les détails du panier d’invités ci-dessus.

   Ajoutez la `[ masked_id ]` reçue de l’étape 3 dans la requête.

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. Les détails du devis sont alors renvoyés sans problème.
1. Accédez au serveur principal et mettez à jour la *[!UICONTROL Stock Status]* du produit configurable sur *[!UICONTROL Out of Stock]*.
1. Exécutez la même requête GraphQL, comme indiqué à l’étape 4.

<u>Résultats attendus</u> :

Le message d’erreur est correctement envoyé/traité dans la réponse.

<u>Résultats réels</u> :

*500 Internal Server* une erreur est générée en réponse à la requête GraphQL.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [&#x200B; Mises à niveau et correctifs > Appliquer des correctifs &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool]
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
