---
title: 'ACSD-64813 : l’annulation de l’affectation de catégories dans [!DNL B2B] catalogue partagé via l’API REST est lente'
description: Appliquez le correctif ACSD-64813 pour résoudre le problème d’Adobe Commerce en raison duquel l’annulation de l’affectation de catégories dans un catalogue partagé [!DNL B2B] via l’API REST est lente.
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
exl-id: e6fd89c2-d3c0-462f-b328-7a80b456d96d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
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
source-wordcount: '398'
ht-degree: 0%
---
# ACSD-64813 : l’annulation de l’affectation de catégories dans [!DNL B2B] catalogue partagé via l’API REST est lente

Le correctif ACSD-64813 corrige le problème de lenteur de l’annulation de l’affectation de catégories dans un catalogue partagé [!DNL B2B] via l’API REST. Ce correctif est disponible lorsque la version 1.1.65 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64813. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’annulation de l’affectation de catégories dans un catalogue partagé [!DNL B2B] via l’API REST est lente.

<u>Procédure à suivre </u> :

1. Activez **[!UICONTROL B2B]**, **[!UICONTROL Company]** et **[!UICONTROL Shared Catalog]**.
1. générer 30 000 produits actifs en stock ;
1. Créez un [catalogue partagé personnalisé](https://experienceleague.adobe.com/fr/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls) et affectez-y tous les produits.
1. Créez une catégorie sous la catégorie racine par défaut et attribuez-lui quelques produits.
1. Utilisez le jeton d’administration pour appeler le point d’entrée de l’API REST `rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories` avec le nouvel ID de catégorie.

   ```json
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

1. Vérifiez que la réponse est *true*.
1. Exécutez `bin/magento cron:run` deux fois ou effectuez une réindexation.
1. Utilisez le jeton d’administration pour appeler le point d’entrée de l’API REST `rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories` avec le nouvel ID de catégorie.

   ```json
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

<u>Résultats attendus</u> :

L&#39;opération devrait être terminée dans un délai raisonnable (moins de deux minutes).

<u>Résultats réels</u> :

L’exécution prend environ 30 minutes ou génère une erreur de temporisation.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
