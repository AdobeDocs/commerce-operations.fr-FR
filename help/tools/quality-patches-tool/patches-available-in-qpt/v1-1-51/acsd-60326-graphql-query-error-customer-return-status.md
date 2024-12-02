---
title: 'ACSD-60326 : La requête GraphQL sur le statut du client [!UICONTROL Returns] renvoie une erreur'
description: Appliquez le correctif ACSD-60326 pour résoudre le problème Adobe Commerce en raison duquel une erreur se produit dans la requête GraphQL pour l’état du client [!UICONTROL Returns].
feature: GraphQL, Returns, Customers
role: Admin, Developer
exl-id: 5cfd7e0d-8703-43a0-86d3-e69612347534
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# ACSD-60326 : La requête GraphQL sur le statut du client [!UICONTROL Returns] renvoie une erreur

Le correctif ACSD-60326 corrige le problème lorsqu’une erreur se produit dans la requête GraphQL pour l’état du client [!UICONTROL Returns]. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 est installé. L’ID de correctif est ACSD-60326. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête GraphQL sur le statut du client [!UICONTROL Returns] renvoie une erreur.

<u>Étapes à reproduire</u> :

1. Initialisez une nouvelle instance avec des exemples de données.
1. Sur la barre latérale *[!UICONTROL Admin]*, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]** et définissez **[!UICONTROL Enable RMA on Storefront]** sur *Oui*.
1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** et renseignez l’adresse.
1. Modifiez le mot de passe du client `roni_cost@example.com`.
1. Connectez-vous au panneau d’administration et passez une commande pour le client `roni_cost@example.com` avec les produits suivants :
   * *WSH12-32-Red*
   * *WSH12-32-Purple*
   * *WSH12-32-Green*
1. Créez *[!UICONTROL Invoice]* et *[!UICONTROL Shipment]* pour cette commande.
1. Sélectionnez **[!UICONTROL Create Returns]**.
1. Accédez à **[!UICONTROL Return Items]** > **[!UICONTROL Add Items]** et :
   * Sélectionnez *WSH12-32-Red* et *WSH12-32-Purple*
   * Cliquez sur **[!UICONTROL Add Selected Products to returns]** :
      * Set **[!UICONTROL Requested]** = *1*
      * Définissez **[!UICONTROL Return Reason]** sur *Out of Service*
      * Définissez **[!UICONTROL Item Condition]** sur *Ayant ouvert*
      * Définissez **[!UICONTROL Resolution]** sur *Refund*
   * Cliquez sur **[!UICONTROL Submit Returns]**.
1. Ouvrez **[!UICONTROL Returns]** et sélectionnez **[!UICONTROL Return Items]** à gauche.
   * Définissez **[!UICONTROL Authorized]** = *1* pour les deux produits.
   * Définissez **[!UICONTROL Status]** comme *Autorisé* pour *WSH12-32-Purple*
   * Définissez **[!UICONTROL Status]** sur *Refusé* pour *WSH12-32-Red*
   * Cliquez sur **[!UICONTROL Save]**
1. Créez une nouvelle commande avec les mêmes produits.
1. Créez un *[!UICONTROL Invoice]*, un *[!UICONTROL Shipment]* et un *[!UICONTROL Returns]* pour les mêmes produits. Autorisez les deux et continuez jusqu’à la fin du processus [!UICONTROL Returns].
1. Générez un jeton client à l’aide de la requête GraphQL suivante :

   ```GraphQL
    mutation {
     generateCustomerToken(email: "roni_cost@example.com", password: "password") {
       token
      }
   }
   ```

1. Autoriser avec le jeton reçu et effectuer la requête suivante :

   ```
   {
   customer {
       returns(pageSize: 20, currentPage: 1) {
        total_count
           items {
               uid
               number
               status
               created_at
           }
       }
   }
   }
   ```

<u>Résultats attendus</u> :

La requête n’affiche aucune erreur. L’état du second retour n’est pas *null*.

<u>Résultats réels</u> :

La requête renvoie une erreur de serveur interne :

```
    {
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 8,
                    "column": 5
                }
            ],
            "path": [
                "customer",
                "returns",
                "items",
                1,
                "status"
            ]
        }
    ],
    "data": {
        "customer": {
            "returns": {
                "total_count": 2,
                "items": [
                    {
                        "uid": "MQ==",
                        "number": "000000001",
                        "status": "PARTIALLY_AUTHORIZED",
                        "created_at": "2024-07-09 10:35:55"
                    },
                    {
                        "uid": "Mg==",
                        "number": "000000002",
                        "status": null,
                        "created_at": "2024-07-09 10:50:02"
                    }
                ]
            }
        }
    }
    } 
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
