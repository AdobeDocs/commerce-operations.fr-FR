---
title: 'ACSD-58566 : erreur de serveur interne GraphQL pour les commentaires de bon de commande'
description: Appliquez le correctif ACSD-58566 pour résoudre le problème Adobe Commerce où GraphQL renvoie une erreur de serveur interne lors de l’interrogation du champ « created_at » dans la mutation « addPurchaseOrderComment ».
feature: B2B, Purchase Orders, GraphQL
role: Admin, Developer
exl-id: 6d051f57-7a2f-44a5-a1c9-834917ed986c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-58566 : erreur de serveur interne GraphQL pour les commentaires de bon de commande

Le correctif ACSD-58566 corrige le problème où l’interrogation du champ `created_at` dans la mutation `addPurchaseOrderComment` renvoie une valeur nulle au lieu de la date et de l’heure attendues. Ce correctif est disponible lorsque la version 1.1.55 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-58566. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

GraphQL renvoie une erreur de serveur interne lors de l’interrogation du champ `created_at` dans la mutation `addPurchaseOrderComment`.

<u>Conditions préalables</u> :

Les modules B2B sont installés et les commandes d’entreprise et d’achat sont activés.

<u>Procédure à suivre </u> :

1. Générez un jeton client pour un utilisateur d’entreprise.
1. Exécutez la séquence de requêtes GraphQL suivante :
   1. Créez un *panier* à l’aide de `customerCart`.
   1. Ajoutez un produit au *panier* à l’aide de `addProductsToCart`.
   1. Passez la commande en utilisant `placePurchaseOrder`.
   1. Ajoutez un commentaire à la commande fournisseur à l&#39;aide de `addPurchaseOrderComment`.

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

Le champ `created_at` renvoie la date et l’heure du commentaire de la commande fournisseur.

<u>Résultats réels</u> :

Affiche « null » au lieu de la date de `created_at`.

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

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

[[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
