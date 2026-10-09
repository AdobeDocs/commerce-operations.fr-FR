---
title: 'ACSD-54324 : la demande requisition_lists de GraphQL ne prend pas en compte les paramètres de pagination'
description: Appliquez le correctif ACSD-54324 pour résoudre le problème d’Adobe Commerce en raison duquel la requête « requisition_lists » de GraphQL ne prend pas en compte les paramètres de pagination et renvoie tous les résultats.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 60f82602-1cfc-4523-a50d-46af5d5f10d9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%
---
# ACSD-54324 : la demande de `requisition_lists` GraphQL ne prend pas en compte les paramètres de pagination.

Le correctif ACSD-54324 corrige le problème en raison duquel la requête de `requisition_lists` GraphQL ne prend pas en compte les paramètres de pagination et renvoie tous les résultats. Ce correctif est disponible lorsque la version 1.1.41 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-54324. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête de `requisition_lists` GraphQL ne prend pas en compte les paramètres de pagination et renvoie tous les résultats.

<u>Procédure à suivre </u> :

1. Connectez-vous en tant qu’administrateur et accédez à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Définissez *[!UICONTROL Enable Requisition List]* sur *Oui*.

1. Connectez-vous au serveur frontal, accédez à **[!UICONTROL My Requisition Lists]** à partir du menu supérieur ou de **[!UICONTROL My Account]**, puis créez plusieurs demandes d&#39;approvisionnement (exemple : 7).
1. Après avoir généré un jeton client, exécutez la requête `requisition_lists` GraphQL ci-dessous pour le client.

   * Assurez-vous que la taille de la page est inférieure au nombre total de listes de demandes d&#39;approvisionnement que vous avez créées (exemple : 4)

   ```graphql
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. Notez que la valeur du champ `total_count` affiche 7, alors qu’elle devrait afficher 4.

   Le nombre d’éléments indique également 7 alors qu’il devrait être identique à la *taille de la page*.

<u>Résultats attendus</u> :

* Le nombre répertorié comme *taille de la page* est renvoyé sous `total_count` et non le nombre total d’enregistrements.
* Le nombre d’éléments est identique à la *taille de la page*.

<u>Résultats réels</u> :

Le nombre total d’enregistrements est renvoyé sous `total_count`, même si *taille de la page* est mentionné.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
