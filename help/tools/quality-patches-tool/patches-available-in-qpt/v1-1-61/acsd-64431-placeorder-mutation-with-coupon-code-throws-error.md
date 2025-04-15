---
title: 'ACSD-64431 : la mutation « placeOrder » avec le code de coupon dans la requête renvoie une erreur de serveur interne'
description: Appliquez le correctif ACSD-64431 pour résoudre le problème d’Adobe Commerce où la mutation « placeOrder » contenant les informations du code de coupon dans la requête renvoie une erreur de serveur interne au lieu de passer la commande avec succès.
feature: GraphQL, Orders, Promotions/Events
role: Admin, Developer
source-git-commit: 883b9db12308c8832afbf709bc188edab746618f
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# ACSD-64431 : la mutation « placeOrder » avec le code de coupon dans la requête renvoie une erreur interne

Le correctif ACSD-64431 corrige le problème en raison duquel la mutation `placeOrder` contenant les informations de code de coupon dans la requête génère une erreur de serveur interne au lieu de passer la commande avec succès. Ce correctif est disponible lorsque la version 1.1.61 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64431. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mutation `placeOrder` qui contient les informations de code de coupon dans la requête renvoie une erreur interne au lieu de passer la commande avec succès.

<u>Procédure à suivre </u> :

1. Créez un produit simple avec des 2836611 __ SKU.
1. Créez un **[!UICONTROL Cart Price Rule]**, définissez **[!UICONTROL Coupon]** sur `Specific Coupon` et saisissez _TEST1234_ comme code de coupon.
1. Créer un client :

   ```
   mutation {
   createCustomer(
       input: {
       firstname: "John"
       lastname: "Doe"
       email: "john.doe@example.com"
       password: "b1b2b3l@w+"
       is_subscribed: true
       }
   ) {
       customer {
       firstname
       lastname
       email
       is_subscribed
       }
   }
   }
   ```

1. Générez un jeton client. Vous pouvez utiliser ce jeton pour les requêtes suivantes.

   ```
   mutation {
   generateCustomerToken(email: "john.doe@example.com", password: "b1b2b3l@w+") {
       token
   }
   }
   ```

1. Créez un panier vide. Enregistrez l’ID de panier et utilisez-le pour les requêtes suivantes.

   ```
   mutation {
       createEmptyCart
   } 
   ```

1. Ajoutez le produit au panier :

   ```
   mutation {
       addProductsToCart(
           cartId: "xxxx"
           cartItems: [{ quantity: 1, sku: "2836611" }]
       ) {
           cart {
               itemsV2 {
                   items {
                       product {
                           name
                           sku
                       }
                       ... on ConfigurableCartItem {
                           configurable_options {
                               configurable_product_option_uid
                               value_label
                           }
                       }
                       quantity
                   }
                   total_count
                   page_info {
                       page_size
                       current_page
                       total_pages
                   }
               }
           }
           user_errors {
               code
               message
           }
       }
   }
   ```

1. Appliquer le coupon :

   ```
   mutation {
       applyCouponToCart(input: { cart_id: "xxxx", coupon_code: "TEST1234" }) {
           cart {
               itemsV2 {
                   items {
                       product {
                           name
                       }
                       quantity
                   }
                   total_count
                   page_info {
                       page_size
                       current_page
                       total_pages
                   }
               }
               applied_coupons {
                   code
               }
               prices {
                   grand_total {
                       value
                       currency
                   }
               }
           }
       }
   }
   ```

1. Définir une adresse de livraison :

   ```
   mutation {
       setShippingAddressesOnCart(
           input: {
               cart_id: "xxxxx"
               shipping_addresses: [
                   {
                       address: {
                           firstname: "John"
                           lastname: "Doe"
                           company: "Company Name"
                           street: ["3320 N Crescent Dr", "Beverly Hills"]
                           city: "Los Angeles"
                           region: "CA"
                           region_id: 12
                           postcode: "90210"
                           country_code: "US"
                           telephone: "123-456-0000"
                           save_in_address_book: false
                       }
                   }
               ]
           }
       ) {
           cart {
               shipping_addresses {
                   firstname
                   lastname
                   company
                   street
                   city
                   region {
                       code
                       label
                   }
                   postcode
                   telephone
                   country {
                       code
                       label
                   }
                   available_shipping_methods {
                       carrier_code
                       carrier_title
                       method_code
                       method_title
                   }
               }
           }
       }
   }
   ```

1. Définir un mode d&#39;expédition :

   ```
   mutation {
       setShippingMethodsOnCart(
           input: {
               cart_id: "xxxx"
               shipping_methods: [{ carrier_code: "flatrate", method_code: "flatrate" }]
           }
       ) {
           cart {
               shipping_addresses {
                   selected_shipping_method {
                       carrier_code
                       carrier_title
                       method_code
                       method_title
                       amount {
                           value
                           currency
                       }
                   }
               }
           }
       }
   }
   ```

1. Définir une adresse de facturation :

   ```
   mutation {
       setBillingAddressOnCart(
           input: {
               cart_id: "xxxx"
               billing_address: {
                   address: {
                       firstname: "John"
                       lastname: "Doe"
                       company: "Company Name"
                       street: ["64 Strawberry Dr", "Beverly Hills"]
                       city: "Los Angeles"
                       region: "CA"
                       region_id: 12
                       postcode: "90210"
                       country_code: "US"
                       telephone: "123-456-0000"
                       save_in_address_book: true
                   }
               }
           }
       ) {
           cart {
               billing_address {
                   firstname
                   lastname
                   company
                   street
                   city
                   region {
                       code
                       label
                   }
                   postcode
                   telephone
                   country {
                       code
                       label
                   }
               }
           }
       }
   }
   ```

1. Définir un mode de paiement :

   ```
   mutation {
       setPaymentMethodOnCart(
           input: { cart_id: "xxxx", payment_method: { code: "checkmo" } }
       ) {
           cart {
               selected_payment_method {
                   code
               }
           }
       }
   }
   ```

1. Passer la commande :

   ```
   mutation {
   placeOrder(
       input: {
       cart_id: "{{cart_id}}"
       }
   ) {
       orderV2 {
       number
       token
       }
       errors {
       message
       code
       }
   }
   }
   ```


<u>Résultats attendus</u> :

La commande doit être passée.

<u>Résultats réels</u> :

Le message d’erreur suivant s’affiche :
`"message": "Internal server error"`

`exception.log` contient l&#39;erreur suivante :

```
    report.ERROR: "discount_model" value should be specifiedGraphQL (1:135)
    1: mutation { placeOrder(input: {cart_id: "xxxx"}) { orderV2 { total { discounts { amount { currency value } coupon { code } } } } errors { message code } } }
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Étapes supplémentaires requises après l’installation du correctif

(Cette section est facultative ; certaines étapes peuvent être nécessaires après l’application du correctif pour résoudre le problème.) 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
