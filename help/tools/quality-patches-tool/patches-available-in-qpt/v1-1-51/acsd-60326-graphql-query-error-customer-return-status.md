---
title: 'ACSD-60326 : la requête GraphQL sur le statut du [!UICONTROL Returns] client renvoie une erreur'
description: Appliquez le correctif ACSD-60326 pour résoudre le problème d’Adobe Commerce où une erreur se produit dans la requête GraphQL pour le statut de la [!UICONTROL Returns] client.
feature: GraphQL, Returns, Customers
role: Admin, Developer
exl-id: 5cfd7e0d-8703-43a0-86d3-e69612347534
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# ACSD-60326 : la requête GraphQL sur le statut du [!UICONTROL Returns] client renvoie une erreur

Le correctif ACSD-60326 corrige le problème où une erreur se produit dans la requête GraphQL pour le statut de [!UICONTROL Returns] du client. Ce correctif est disponible lorsque la version 1.1.51 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-60326. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête GraphQL sur le statut de [!UICONTROL Returns] du client renvoie une erreur.

<u>Procédure à suivre </u> :

1. Initialisez une nouvelle instance avec des exemples de données.
1. Sur la barre latérale *[!UICONTROL Admin]*, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]** et définissez **[!UICONTROL Enable RMA on Storefront]** sur *Oui*.
1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** et renseignez l’adresse.
1. Modifiez le mot de passe du `roni_cost@example.com` client.
1. Connectez-vous au panneau d’administration et passez une commande pour l’`roni_cost@example.com` client avec les produits suivants :
   * *WSH12-32-Red*
   * *WSH12-32-Purple*
   * *WSH12-32-Vert*
1. Créez un *[!UICONTROL Invoice]* et un *[!UICONTROL Shipment]* pour cette commande.
1. Sélectionnez **[!UICONTROL Create Returns]**.
1. Accédez à **[!UICONTROL Return Items]** > **[!UICONTROL Add Items]** et :
   * Sélectionnez *WSH12-32-Red* et *WSH12-32-Purple*
   * Cliquez **[!UICONTROL Add Selected Products to returns]** :
      * Définir **[!UICONTROL Requested]** = *1*
      * Définissez **[!UICONTROL Return Reason]** sur *Hors service*
      * Définissez **[!UICONTROL Item Condition]** sur *Ouvert*
      * Définissez **[!UICONTROL Resolution]** sur *Remboursement*
   * Cliquez sur **[!UICONTROL Submit Returns]**.
1. Ouvrez **[!UICONTROL Returns]** et sélectionnez **[!UICONTROL Return Items]** à gauche.
   * Définissez **[!UICONTROL Authorized]** = *1* pour les deux produits
   * Définissez **[!UICONTROL Status]** comme *Autorisé* pour *WSH12-32-Purple*
   * Définissez **[!UICONTROL Status]** comme *Refusé* pour *WSH12-32-Red*
   * Clic **[!UICONTROL Save]**
1. Créez une nouvelle commande avec les mêmes produits.
1. Créez un *[!UICONTROL Invoice]*, un *[!UICONTROL Shipment]* et un *[!UICONTROL Returns]* pour les mêmes produits. Autorisez les deux et continuez jusqu’à la fin du processus de [!UICONTROL Returns].
1. Générez un jeton client à l’aide de la requête GraphQL suivante :

   ```GraphQL
    mutation {
     generateCustomerToken(email: "roni_cost@example.com", password: "password") {
       token
      }
   }
   ```

1. Autorisez avec le jeton reçu et effectuez la requête suivante :

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

La requête n’affiche aucune erreur. Le statut du deuxième retour n&#39;est pas *null*.

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

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
