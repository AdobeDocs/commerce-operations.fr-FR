---
title: 'ACSD-63883 : correction d’un « items_count » incorrect dans [!DNL GraphQL] réponse pour [!UICONTROL Requisition List]'
description: Appliquez le correctif ACSD-63883 pour résoudre le problème où le [!UICONTROL Requisition List] renvoie un « items_count » incorrect dans la réponse [!DNL GraphQL].
feature: B2B, GraphQL
role: Admin, Developer
exl-id: 8946d7fb-558a-4867-a843-a61715416f25
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
source-wordcount: '317'
ht-degree: 0%
---
# ACSD-63883 : correction d’un `items_count` incorrect dans [!DNL GraphQL] réponse pour [!UICONTROL Requisition List]

Le correctif ACSD-63883 corrige le problème où le **[!UICONTROL Requisition List]** renvoie un `items_count` incorrect dans la réponse [!DNL GraphQL]. Ce correctif est disponible lorsque la version 1.1.61 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63883. Notez que le problème est planifié pour être corrigé dans Adobe Commerce B2B 1.5.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La **[!UICONTROL Requisition List]** renvoie un `items_count` incorrect dans la réponse [!DNL GraphQL].


<u>Procédure à suivre </u> :

1. Activez la fonctionnalité de **[!UICONTROL Requisition List]** B2B.
1. Créez quelques produits.
1. Créez un compte client.
1. Cliquez sur **[!UICONTROL Create new Requisition List]**.
1. Envoyez la demande de mutation `addProductsToRequisitionList` [!DNL GraphQL] avec un produit pour l’ajouter au [!UICONTROL Requisition List].

   ```graphql
   mutation addProductsToRequisitionList(
   $requisitionListUid: ID!
   $requisitionListItems: [RequisitionListItemsInput!]!
   ) {
   addProductsToRequisitionList(
   requisitionListUid: $requisitionListUid
   requisitionListItems: $requisitionListItems
   ) {
   requisition_list
   { uid name description items_count }
   }
   }
   ```

1. Envoyez la demande de mutation `addProductsToRequisitionList` [!DNL GraphQL] avec trois autres produits pour les ajouter au [!UICONTROL Requisition List].
1. Vérifiez le `items_count` dans la réponse.

**Résultats attendus** :

* `items_count` : 4 doit être renvoyé dans la réponse.

**Résultats réels** :

* `items_count` : 2 est renvoyé dans la réponse.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
