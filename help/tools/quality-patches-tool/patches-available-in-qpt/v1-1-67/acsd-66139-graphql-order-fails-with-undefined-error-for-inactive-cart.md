---
title: 'ACSD-66139 : la commande GraphQL échoue avec une erreur UNDEFINED pour le panier inactif'
description: Appliquez le correctif ACSD-66139 pour résoudre le problème d’Adobe Commerce où, lors de la commande d’un panier inexistant ou inactif, GraphQL renvoie un code d’erreur UNDEFINED au lieu d’un code spécifique lorsque les messages d’erreur sont traduits.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: 5a1a94ca-f274-4098-8b44-d3f1a0ea65a1
source-git-commit: 8681dd706e614f86bbee36c182b47491ec707196
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-66139 : la commande GraphQL échoue avec l’erreur « UNDEFINED » pour le panier inactif

Le correctif ACSD-66139 corrige le problème où, lors de la commande d’un panier inexistant ou inactif, GraphQL renvoie un code d’erreur *UNDEFINED* au lieu d’un code spécifique lorsque les messages d’erreur sont traduits. Ce correctif est disponible lorsque la version 1.1.67 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66139. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers l’icône dernières versions et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

GraphQL renvoie un code d’erreur *UNDEFINED* au lieu d’un code spécifique lors de la commande d’un panier inexistant ou inactif, si le message d’erreur est traduit.

<u>Procédure à suivre </u> :

1. Ajoutez des `app/i18n/Magento/de_DE/de_DE.csv` et incluez la traduction de chaîne d’erreur suivante :

```
"Could not find a cart with ID ""%masked_cart_id""","Oh noo, we have an UNDEFINED issue, see!",module,Magento_QuoteGraphQl
```

1. Dans le panneau d’administration, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** > **[!UICONTROL Create Store View]** pour créer une vue de magasin.
1. Définissez **[!UICONTROL Code]** sur *test*.
1. Attribuez `german` langue à la vue de magasin nouvellement créée.
1. Exécutez `setup:upgrade` et `setup:static-content:deploy -f`.
1. Exécutez la requête GraphQL suivante avec les `Store:test` d’en-tête :

```
mutation {
    placeOrder(input: { cart_id: "test" }) {
        orderV2 {
            id
            number
        }
    }
}
```

<u>Résultats attendus</u> :

Réponse d’erreur correcte :

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "CART_NOT_FOUND"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

<u>Résultats réels</u> :

La `error_code` renvoyée est *UNDEFINED* :

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "UNDEFINED"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
