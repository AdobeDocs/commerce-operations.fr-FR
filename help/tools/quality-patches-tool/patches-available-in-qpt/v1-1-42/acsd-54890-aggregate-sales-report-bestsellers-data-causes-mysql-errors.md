---
title: 'ACSD-54890 : « aggregate_sales_report_bestsellers_data » entraîne des erreurs [!DNL MySQL]'
description: Appliquez le correctif ACSD-54890 pour résoudre le problème d’Adobe Commerce en raison duquel « aggregate_sales_report_bestsellers_data » provoque des erreurs [!DNL MySQL] en raison du manque d’espace de « /tmpdisk ».
feature: Attributes
role: Admin, Developer
exl-id: 21f926e0-a4f4-45ae-9397-4885a85db947
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
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
source-wordcount: '335'
ht-degree: 0%
---
# ACSD-54890 : `aggregate_sales_report_bestsellers_data` provoque des erreurs MySQL

Le correctif ACSD-54890 corrige le problème où le `aggregate_sales_report_bestsellers_data` provoque des erreurs [!DNL MySQL] en raison du manque d’espace de `/tmpdisk`. Ce correctif est disponible lorsque la version 1.1.42 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-54890. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le `aggregate_sales_report_bestsellers_data` provoque des erreurs **[!DNL MySQL]** en raison du manque d’espace `/tmpdisk`.

<u>Procédure à suivre </u> :

Exécutez la tâche cron `aggregate_sales_report_bestsellers_data` lorsque la table `sales_bestsellers_aggregated_daily` contient une énorme quantité d’enregistrements, comme des dizaines de millions d’enregistrements.

<u>Résultats attendus</u> :

Aucune erreur ne se produit.

<u>Résultats réels</u> :

L’erreur suivante se produit :
`report.ERROR: Cron Job aggregate_sales_report_bestsellers_data has an error: SQLSTATE[HY000]: General error: 3 Error writing file '/tmp/#sql/fd=72' (Errcode: 28 "No space left on device")`

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [&#x200B; Mises à niveau et correctifs > Appliquer des correctifs &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool]
* [Recommandations relatives à la modification des tables de base de données](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
