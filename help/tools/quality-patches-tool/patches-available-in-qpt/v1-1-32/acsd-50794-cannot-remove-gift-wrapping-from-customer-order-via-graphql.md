---
title: 'ACSD-50794 : impossible de supprimer l’encapsulation des cadeaux de la commande client via GraphQL'
description: Appliquez le correctif ACSD-50794 pour résoudre le problème Adobe Commerce en raison duquel les utilisateurs ne peuvent pas supprimer l’emballage cadeau de la commande client via GraphQL.
feature: Gift, GraphQL, Orders
role: Admin
exl-id: e088fb18-89d3-47e4-ad02-54068c1ab653
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-50794 : impossible de supprimer l’encapsulation des cadeaux de la commande client via GraphQL

Le correctif ACSD-50794 corrige le problème en raison duquel les utilisateurs ne peuvent pas supprimer l’encapsulation des cadeaux de la commande client via GraphQL. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32 est installé. L’ID de correctif est ACSD-50794. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne peuvent pas supprimer l’emballage cadeau de la commande client via GraphQL.

<u>Étapes à reproduire</u> :

1. Créez un client à partir du front-end.
1. Créez un produit simple.
1. Activez *[!UICONTROL Gift Messages]* en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** et définissez *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*.
1. Créez *[!UICONTROL Gift Wrapping]* en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. Obtenir le jeton client.
1. Créez un panier vide, customerCart.
   * Ajouter des produits au panier : mutation `addProductsToCart`
   * Définition de l’adresse de facturation : mutation `setBillingAddressOnCart`
   * Définition de l’adresse de livraison : mutation `setShippingAddressesOnCart`
   * Méthode de livraison définie : mutation `setShippingMethodsOnCart` (flatrate)
   * Méthode de paiement définie : mutation `setPaymentMethodOnCart` (checkmo)
1. Vérifiez maintenant l’encapsulage du cadeau *Uid* avec cette requête de panier :

   ```GraphQL
   {
     cart(cart_id: "{{CART_ID}}") {
       available_gift_wrappings{
           uid
       }
   }
   }
   ```

1. Définissez le retour automatique à la ligne cadeau à l’aide de `setGiftOptionsOnCart`.
1. Vérifiez la requête panier : panier.
1. Retour à la ligne du cadeau non défini à l’aide de `setGiftOptionsOnCart` (définissez la valeur sur null).
1. Vérifiez à nouveau la requête panier : panier.
1. Ordre de tri : mutation `placeOrder`.
1. Exécutez la requête du client : customer.

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

Une fois qu’un utilisateur a défini un retour automatique à la ligne du cadeau et l’a annulé, la requête du client renvoie &quot;null&quot;.

<u>Résultats réels</u> :

La requête du client renvoie toujours l’encapsulation du cadeau comme appliquée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
