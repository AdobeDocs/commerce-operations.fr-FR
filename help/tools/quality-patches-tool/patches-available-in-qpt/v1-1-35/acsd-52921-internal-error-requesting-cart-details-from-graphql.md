---
title: 'ACSD-52921 : erreur de demande de détails de panier auprès de GraphQL pour un produit configurable en rupture de stock'
description: Appliquez le correctif ACSD-52921 pour résoudre le problème Adobe Commerce en raison duquel une erreur interne se produit lors de la demande des détails du panier auprès de GraphQL pour un produit configurable en rupture de stock.
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 7790718a-6b86-497e-b1a1-88ba22c3e8ff
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-52921 : erreur de demande de détails de panier auprès de GraphQL pour un produit configurable en rupture de stock

Le correctif ACSD-52921 corrige le problème d’erreur interne lors de la demande de détails de panier auprès de GraphQL pour un produit configurable en rupture de stock. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.35 est installé. L’ID de correctif est ACSD-52921. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur interne se produit lors de la demande des détails du panier auprès de GraphQL pour un produit configurable en rupture de stock.

<u>Étapes à reproduire</u> :

1. Créez un produit configurable avec quelques options.
1. Ajoutez une option pour le produit configurable ci-dessus dans le panier à partir de l’interface (passage en caisse des invités).
1. Récupérez le `[ masked_id ]` de la table de la base de données `[ quote_id_mask ]` pour le guillemet créé ci-dessus.
1. Exécutez la requête GraphQL suivante pour obtenir les détails du panier d’invités ci-dessus.

   Ajoutez le `[ masked_id ]` reçu de l’étape 3 dans la requête.

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

1. Cela renverra les détails des guillemets sans problème.
1. Accédez au serveur principal et mettez à jour le *[!UICONTROL Stock Status]* du produit configurable vers *[!UICONTROL Out of Stock]*.
1. Exécutez la même requête GraphQL, comme indiqué à l’étape 4.

<u>Résultats attendus</u> :

Le message d’erreur est envoyé/traité correctement dans la réponse.

<u>Résultats réels</u> :

*500 Internal Server* erreur générée en réponse à la requête GraphQL.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool]
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide d’infrastructure Commerce on Cloud

## Lecture connexe

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
