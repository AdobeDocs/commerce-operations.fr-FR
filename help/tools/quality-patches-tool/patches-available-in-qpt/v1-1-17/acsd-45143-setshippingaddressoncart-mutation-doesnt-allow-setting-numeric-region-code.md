---
title: 'ACSD-45143 : mutation setShippingAddressesOnCart ne définissant pas le code de région numérique comme « région »'
description: Le correctif ACSD-45143 corrige le problème en raison duquel la mutation setShippingAddressesOnCart ne permet pas de définir le code de région numérique comme « région ». Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID du correctif est ACSD-45143. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.
feature: Orders, Shipping/Delivery, Shopping Cart
role: Admin
exl-id: c7d9d1f2-4731-406f-93bd-036f0fe75b1d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-45143 : mutation setShippingAddressesOnCart ne définissant pas le code de région numérique comme « région »

Le correctif ACSD-45143 corrige le problème en raison duquel la mutation setShippingAddressesOnCart ne permet pas de définir le code de région numérique comme « région ». Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID du correctif est ACSD-45143. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mutation setShippingAddressesOnCart ne permet pas de définir le code de région numérique comme « région ».

<u>Procédure à suivre </u> :

1. Créez un panier à l’aide de la requête ci-dessous.

   <pre>
    <code class="language-graphql">
    mutation {
      createEmptyCart
    }
    </code>
    </pre>

1. Envoyez une demande pour définir l’adresse de livraison dans le panier.

   <pre>
    <code class="language-graphql">
    mutation ($cartId: String!) {
      setShippingAddressesOnCart(
        input: {
          cart_id: $cartId
          shipping_addresses: {
            address: {
              firstname: "Tomek"
              lastname: "Nowak"
              company: "Company Name"
              street: ["234 Rue de Rivoli"]
              region: "58"
              city: "Lille"
              postcode: "59800"
              country_code: "FR"
              telephone: "123-456-0000"
              save_in_address_book: false
            }
          }
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
            }
          }
        }
      }
      </code>
      </pre>

   Remarque : le code pays est défini sur « FR » et le code région sur « 58 » dans cet exemple. Selon le tableau `directory_country_region` Db, le code de région 58 est « Nièvre ».

1. Vérifiez la réponse renvoyée.

<u>Résultats attendus</u> :

Adobe Commerce permet de définir un code de région numérique dans la requête GraphQL.

<u>Résultats réels</u> :

Le code de région est remplacé par 47.

<pre>
<code class="language-graphql">
{
  "data": {
    "setShippingAddressesOnCart": {
      "cart": {
        "shipping_addresses": [
        {
          "firstname": "Tomek",
          "lastname": "Nowak",
          "company": "Company Name",
          "street": [
          "234 Rue de Rivoli"
          ],
          "city": "Lille",
          "region": {
            "code": "47",
            "label": "Lot-et-Garonne"
            },
            "postcode": "59800",
            "telephone": "123-456-0000",
            "country": {
              "code": "FR",
              "label": "FR"
            }
          }
        ]
      }
    }
  }
}
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

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
