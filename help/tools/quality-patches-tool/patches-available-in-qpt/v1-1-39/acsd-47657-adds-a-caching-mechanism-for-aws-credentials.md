---
title: 'ACSD-47657 : ajoute un mécanisme de mise en cache pour les informations d’identification AWS'
description: Appliquez le correctif ACSD-47657 pour résoudre le problème d’Adobe Commerce qui se produit lors d’un chargement élevé de requêtes vers AWS S3 en ajoutant un mécanisme de mise en cache pour les informations d’identification AWS.
feature: Cache
role: Admin, Developer
exl-id: 2851d511-a9b0-49f8-94ba-ad63d2397ca5
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '354'
ht-degree: 0%
---
# ACSD-47657 : ajoute un mécanisme de mise en cache pour les informations d’identification AWS

Le correctif ACSD-47657 corrige le problème qui se produit lors d’un chargement élevé de requêtes vers AWS S3 en ajoutant un mécanisme de mise en cache pour les informations d’identification AWS. Ce correctif est disponible lorsque la version 1.1.39 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-47657. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Ajout d’un mécanisme de mise en cache des informations d’identification AWS récupérées d’AWS pour la configuration EC2.

<u>Procédure à suivre </u> :

1. Activez le stockage du compartiment AWS S3 pour Adobe Commerce :

   ```shell
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="magentopubmedia-prod" --remote-storage-region="aws-west" --no-interaction
   bin/magento config:set 
   system/media_storage_configuration/media_database 0 
   bin/magento cache:flush
   ```

1. Exécuter la synchronisation :

   ```shell
   bin/magento remote-storage:sync
   ```

<u>Résultats attendus</u> :

La synchronisation s’est terminée correctement.

<u>Résultats réels</u> :

Dans environ une heure, l’erreur suivante se produit :

```text
    report.CRITICAL: Aws\Exception\CredentialsException: Error retrieving credentials from the instance profile metadata service. (cURL error 28: Connection timed out after 1001 milliseconds) (see https://curl.haxx.se/libcurl/c/libcurl-errors.html) 
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
