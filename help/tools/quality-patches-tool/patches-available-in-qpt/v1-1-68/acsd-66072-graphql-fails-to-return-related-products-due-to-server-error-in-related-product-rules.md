---
title: 'ACSD-66072 : GraphQL ne parvient pas à renvoyer les produits associés sur la page des détails du produit'
description: Appliquez le correctif ACSD-66072 pour résoudre le problème d’Adobe Commerce en raison duquel les produits associés ne sont pas renvoyés via GraphQL sur la page des détails du produit en raison d’une erreur de serveur interne lors de la configuration des règles de produits associés.
feature: GraphQL, Products
role: Admin, Developer
type: Troubleshooting
exl-id: a706a710-aed3-41a4-bc87-3150e9ba95f7
source-git-commit: 8bb921704239d2b4622931a7814759bda5e9401f
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-66072 : GraphQL ne parvient pas à renvoyer les produits associés sur la page des détails du produit

Le correctif ACSD-66072 corrige le problème où les produits associés ne sont pas renvoyés via GraphQL sur la page des détails du produit en raison d’une erreur de serveur interne lors de la configuration de **[!UICONTROL Related Products Rule]**. Ce correctif est disponible lorsque la version 1.1.68 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66072. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits associés ne sont pas renvoyés via GraphQL dans la page Détails du produit en raison d’une erreur de serveur interne lors de la configuration de **[!UICONTROL Related Products Rule]**.

<u>Procédure à suivre </u> :

1. Créer des produits configurables :
   * **Produit 1** : `config1` avec `option1`
   * **Produit 2** : `config2` avec `option2`

1. Créer et affecter des produits à une catégorie
   * Créez une **nouvelle catégorie**.
   * Attribuez les deux produits (`config1` et `config2`) à cette catégorie.

1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Related Products Rule]**, puis créez une règle avec les paramètres suivants :

   * **[!UICONTROL Priority]** : 1
   * **[!UICONTROL Applies To]** : **[!UICONTROL Related Products]**
   * **[!UICONTROL Result Limit]** : 10
   * **[!UICONTROL Products to Match]** : **[!UICONTROL Attribute Set is Default]**
   * **[!UICONTROL Products to Display]** : `Product Category is the Same as Matched Product Categories`

1. Exécutez les commandes de l’interface de ligne de commande Magento suivantes :

   ```bash
   bin/magento indexer:reindex
   bin/magento cache:clean
   ```

1. Envoyez une requête POST à `../graphql` avec la payload suivante :

   ```
   query getRelatedProductsForProductPage($urlKey: String!) 
   {
       products(filter: { url_key: { eq: $urlKey } }) 
       {
           items {
               id
               __typename
               uid
               url_key
               name
               sku
               related_products {
                   id
                   uid
                   name
                   sku
                   stock_status
                   url_key
                   small_image {
                       url
                       __typename
                       }
                       thumbnail {
                           url
                           __typename
                           }
                           image {
                               url
                               __typename
                               }
                               price_range {
                                   maximum_price {
                                       regular_price {
                                           currency
                                           value
                                           __typename
                                           }
                                           __typename
                                           }
                                           minimum_price {
                                               discount {
                                                   amount_off
                                                   percent_off
                                                   __typename
                                                   }
                                                   final_price {
                                                       currency
                                                       value
                                                       __typename
                                                       }
                                                       regular_price {
                                                           currency
                                                           value
                                                           __typename}
                                                           __typename}
                                                           __typename}
                                                           __typename
                                                           }
                                                           }
                                                           __typename
                                                           }
                                                           }
   ```

<u>Résultats attendus</u> :

La requête renvoie le produit associé (`config1`).

<u>Résultats réels</u> :

```graphql
{
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 10,
                    "column": 7
                }
            ],
            "path": [
                "products",
                "items",
                0,
                "related_products"
            ]
        }
    ],
    "data": {
        "products": {
            "items": [
                {
                    "id": 4,
                    "__typename": "ConfigurableProduct",
                    "uid": "NA==",
                    "url_key": "config2",
                    "name": "config2",
                    "sku": "config2",
                    "related_products": null
                }
            ],
            "__typename": "Products"
        }
    }
}
```

Le fichier `var/log/exception.log` contient :

```
report.ERROR: Deprecated Functionality: explode(): Passing null to parameter #2 ($string) of type string is deprecated in /home/magento2ee/app/code/Magento/TargetRule/Model/ResourceModel/Index.php on line 557
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
