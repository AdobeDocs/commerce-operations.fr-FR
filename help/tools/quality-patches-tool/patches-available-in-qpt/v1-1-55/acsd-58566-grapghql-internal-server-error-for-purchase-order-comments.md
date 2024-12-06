---
title: 'ACSD-58566 : Erreur interne du serveur GraphQL pour les commentaires de commande'
description: Appliquez le correctif ACSD-58566 pour résoudre le problème Adobe Commerce en raison duquel GraphQL renvoie une erreur de serveur interne lors de l’interrogation du champ "created_at" dans la mutation "addPurchaseOrderComment".
feature: B2B, Purchase Orders, GraphQL
role: Admin, Developer
source-git-commit: 3b8cc44ea8d71982b8a2eb76d9d7ec2a5c3180b0
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-58566 : Erreur interne du serveur GraphQL pour les commentaires de commande

Le correctif ACSD-58566 corrige le problème en raison duquel l’interrogation du champ `created_at` dans la mutation `addPurchaseOrderComment` renvoie une valeur nulle au lieu de la date-time attendue. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 est installé. L’ID de correctif est ACSD-58566. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

GraphQL renvoie une erreur de serveur interne lors de l’interrogation du champ `created_at` dans la mutation `addPurchaseOrderComment`.

<u>Conditions préalables</u> :

Les modules B2B sont installés et la société et les commandes sont activées.

<u>Étapes à reproduire</u> :

1. Générez un jeton client pour un utilisateur de société.
1. Exécutez la séquence de requêtes GraphQL suivante :
   1. Créez un *panier* à l’aide de `customerCart`.
   1. Ajoutez un produit au *panier* à l’aide de `addProductsToCart`.
   1. Placez la commande à l’aide de `placePurchaseOrder`.
   1. Ajoutez un commentaire au bon de commande à l’aide de `addPurchaseOrderComment`.

   ```
   mutation {
       addPurchaseOrderComment(
           input: { purchase_order_uid: "MQ==", comment: "Looks good to me" }
   ) {
           comment {
               uid
               created_at
               author {
                   firstname
                   lastname
                   email
               }
               text
           }
       }
   }
   ```

<u>Résultats attendus</u> :

Le champ `created_at` renvoie la date et l’heure du commentaire du bon de commande.

<u>Résultats réels</u> :

Affiche null au lieu de la date `created_at`.

```
{
  "errors": [
    {
      "message": "Internal server error",
      "locations": [
        {
          "line": 10,
          "column": 1
        }
      ],
      "path": [
        "addPurchaseOrderComment",
        "comment",
        "created_at"
      ]
    }
  ],
  "data": {
    "addPurchaseOrderComment": null
  }
}
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

[[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
