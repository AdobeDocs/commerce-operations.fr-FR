---
title: 'ACSD-59952 : erreur lors de la suppression du catalogue partagé avec le même ID de groupe qu’un autre catalogue partagé'
description: Appliquez le correctif ACSD-59952 pour résoudre le problème d’Adobe Commerce où une erreur est générée lors de la suppression d’un catalogue partagé avec le même « customer_group_id » qu’un autre catalogue partagé.
feature: B2B, REST
role: Admin, Developer
exl-id: 11cba2e6-dd62-4063-a38c-b98ea70a72e9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
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
source-wordcount: '451'
ht-degree: 0%
---
# ACSD-59952 : erreur lors de la suppression du catalogue partagé avec le même ID de groupe qu’un autre catalogue partagé

Le correctif ACSD-59952 corrige l’erreur générée lors de la suppression de catalogues partagés avec le même `customer_group_id` qu’un autre catalogue partagé. Cela empêche en outre les utilisateurs et utilisatrices de créer de tels catalogues partagés. Ce correctif est disponible lorsque la version 1.1.52 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-59952. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Impossible de créer un nouveau catalogue partagé avec le même `customer_group_id` qu’un autre catalogue partagé. Cependant, en le faisant, la tentative de suppression du catalogue partagé avec le même `customer_group_id` renvoie une erreur.

<u>Conditions préalables</u> :

Installez les modules B2B d’Adobe Commerce.

<u>Procédure à suivre </u> :

1. Créez plusieurs catalogues partagés affectés au même `customer_group_id` à l’aide de l’appel API REST suivant :

   ```REST
   {
       "sharedCatalog": {
           "name": "test1",
           "description": "test",
           "customer_group_id": 1,
           "type": 0,
           "created_at": "03:11:00",
           "created_by": 1,
           "store_id": 0,
           "tax_class_id": 3
       }
   }
   ```

1. Essayez de supprimer l’un des catalogues partagés à l’aide de l’appel API REST suivant :

   ```REST
   /rest/default/V1/sharedCatalog/4
   ```

<u>Résultats attendus</u> :

* La création de plusieurs catalogues partagés affectés au même `customer_group_id` n’est pas possible.
* Le catalogue partagé dans le cas ci-dessus a été supprimé.

<u>Résultats réels</u> :

* Il est possible de créer plusieurs catalogues partagés affectés au même `customer_group_id`.
* L’erreur suivante est renvoyée lors de la tentative de suppression du catalogue partagé avec le même `customer_group_id` : *Impossible de supprimer le catalogue partagé*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] publié : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans notre base de connaissances d’assistance.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances d’assistance.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
