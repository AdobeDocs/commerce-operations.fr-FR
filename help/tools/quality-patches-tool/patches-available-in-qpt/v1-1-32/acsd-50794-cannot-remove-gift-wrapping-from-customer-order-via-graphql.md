---
title: 'ACSD-50794 : impossible de supprimer l’emballage-cadeau de la commande client via GraphQL'
description: Appliquez le correctif ACSD-50794 pour résoudre le problème d’Adobe Commerce en raison duquel les utilisateurs ne peuvent pas supprimer l’emballage-cadeau de la commande client via GraphQL.
feature: Gift, GraphQL, Orders
role: Admin
exl-id: e088fb18-89d3-47e4-ad02-54068c1ab653
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-50794 : impossible de supprimer l’emballage-cadeau de la commande client via GraphQL

Le correctif ACSD-50794 corrige le problème en raison duquel les utilisateurs ne peuvent pas supprimer l’emballage-cadeau de la commande du client via GraphQL. Ce correctif est disponible lorsque la version 1.1.32 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-50794. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne peuvent pas supprimer l’emballage-cadeau de la commande client via GraphQL.

<u>Procédure à suivre </u> :

1. Créez un client à partir du serveur frontal.
1. Créez un produit simple.
1. Activez *[!UICONTROL Gift Messages]* en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** et en définissant *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*.
1. Créez des *[!UICONTROL Gift Wrapping]* en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. Obtention du jeton client.
1. Créez un panier vide, customerCart.
   * Ajouter des produits au panier : `addProductsToCart` mutation
   * Définir l&#39;adresse de facturation : mutation `setBillingAddressOnCart`
   * Définir l&#39;adresse de livraison : `setShippingAddressesOnCart` mutation
   * Définir le mode d&#39;expédition : `setShippingMethodsOnCart` mutation (flatté)
   * Définir le mode de paiement : `setPaymentMethodOnCart` mutation (checkmo)
1. Vérifiez maintenant l’emballage du cadeau *Uid* avec cette requête de panier :

   ```GraphQL
   {
     cart(cart_id: "{{CART_ID}}") {
       available_gift_wrappings{
           uid
       }
   }
   }
   ```

1. Enveloppe cadeau en utilisant `setGiftOptionsOnCart`.
1. Vérifier le panier : requête de panier.
1. Annuler l&#39;emballage cadeau à l&#39;aide de `setGiftOptionsOnCart` (définir la valeur sur null).
1. Vérifiez à nouveau la requête panier : panier .
1. Ordre de placement : mutation `placeOrder`.
1. Exécuter la requête client : client.

   ```GraphQL
   query {
     customer {
       firstname
       middlename
       lastname
       suffix
       email
       orders {
           items {
               order_date
               gift_wrapping {
                   design
                   uid
               }
           }
       }
       addresses {
         firstname
         middlename
         lastname
         street
         city
         region {
           region_code
           region
         }
         postcode
         country_code
         telephone
       }
     }
   }
   ```

<u>Résultats attendus</u> :

Une fois qu’un utilisateur a défini un habillage cadeau et l’a désactivé, la requête client renvoie la valeur null.

<u>Résultats réels</u> :

La requête client renvoie toujours l’emballage cadeau tel qu’appliqué.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
