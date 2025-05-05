---
title: 'ACSD-56158 : valeur de taxe incorrecte dans la réponse GraphQL lorsque plusieurs règles de taxe sont appliquées au panier'
description: Appliquez le correctif ACSD-56158 pour résoudre le problème Adobe Commerce en raison duquel le rendu de la valeur de taxe dans la réponse GraphQL est incorrect lorsque plusieurs règles de taxe sont appliquées au panier.
feature: GraphQL, Taxes
role: Admin, Developer
exl-id: dc22861c-cd41-402f-be37-d02c02b59433
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# ACSD-56158 : valeur de taxe incorrecte dans la réponse GraphQL lorsque plusieurs règles de taxe sont appliquées au panier

Le correctif ACSD-56158 corrige le problème en raison duquel le rendu de la valeur de taxe dans la réponse GraphQL est incorrect lorsque plusieurs règles de taxe sont appliquées au panier. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 est installé. L’ID de correctif est ACSD-56158. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le rendu de la valeur de taxe dans la réponse GraphQL est incorrect lorsque plusieurs règles de taxe sont appliquées au panier.

<u>Étapes à reproduire</u> :

1. Créez un client avec une adresse américaine.
1. Accédez au panneau Admin.
1. Créez un produit au prix de 100 €.
1. Créez deux taux d&#39;imposition pour l&#39;adresse des Etats-Unis : un pour 10% et l&#39;autre pour 5%.
1. Configurez deux règles de taxe pour les États-Unis à partir de **[!UICONTROL Stores]** > **[!UICONTROL Taxes]** > **[!UICONTROL Tax Rule]**.
1. Attribuez un taux d’imposition à une règle.
1. Depuis l’interface utilisateur frontale, connectez-vous en tant que client avec l’adresse américaine et ajoutez le produit au panier.
1. Générez un jeton client via GraphQL.
1. Générez un identifiant de panier via GraphQL.
1. Vérifiez que la taxe appliquée est correcte en obtenant le panier du client via GraphQL :

   ```GraphQL
   {
       cart(cart_id: "o3Yqt6zkn8ncOzFxGnR1IWdT..") {
           id
           email
           billing_address {
               city
               country {
                   code
                   label
               }
               firstname
               lastname
               company
               postcode
               vat_id
               region {
                   code
                   label
               }
               street
               telephone
           }
           shipping_addresses {
               firstname
               lastname
               company
               street
               city
               postcode
               vat_id
               region {
                   code
                   label
               }
               country {
                   code
                   label
               }
               telephone
               available_shipping_methods {
                   amount {
                       currency
                       value
                   }
                   available
                   carrier_code
                   carrier_title
                   error_message
                   method_code
                   method_title
                   price_excl_tax {
                       value
                       currency
                   }
                   price_incl_tax {
                       value
                       currency
                   }
               }
               selected_shipping_method {
                   amount {
                       value
                       currency
                   }
                   carrier_code
                   carrier_title
                   method_code
                   method_title
               }
           }
           available_payment_methods {
               code
               title
           }
           selected_payment_method {
               code
               title
           }
           applied_coupons {
               code
           }
           prices {
               grand_total {
                   value
                   currency
               }
               subtotal_excluding_tax {
                   value
                   currency
               }
               subtotal_including_tax {
                   value
                   currency
               }
               applied_taxes {
                   label
                   amount {
                       currency
                       value
                   }
               }
           }
       }
   }    
   ```

<u>Résultats attendus</u> :

Chaque taux d&#39;imposition indique son propre montant d&#39;impôt :

```
"applied_taxes": [
    {
        "label": "US-CA-*-Rate 1",
        "amount": {
            "currency": "USD",
            "value": 10
        }
    },
    {
        "label": "US-CA-*-Rate 2",
        "amount": {
            "currency": "USD",
            "value": 5
        }
    }
]
```

<u>Résultats réels</u> :

Montant total de la taxe retourné pour chaque règle :

```
"applied_taxes": [
    {
        "label": "US-CA-*-Rate 1",
        "amount": {
            "currency": "USD",
            "value": 15
        }
    },
    {
        "label": "US-CA-*-Rate 2",
        "amount": {
            "currency": "USD",
            "value": 15
        }
    }
]
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
