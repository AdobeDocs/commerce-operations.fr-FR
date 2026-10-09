---
title: 'ACSD-55427 : un administrateur ne peut pas annuler l’attribution du produit à partir de **[!UICONTROL Product in Shared Catalogs]** sur la page du produit'
description: Appliquez le correctif ACSD-55427 pour résoudre le problème d’Adobe Commerce en raison duquel l’affectation d’un produit ne peut pas être annulée de **[!UICONTROL Product in Shared Catalogs]**.
feature: Products, B2B
role: Admin, Developer
exl-id: 974347fd-351d-4a4b-a9ca-a534daf3fbd7
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '405'
ht-degree: 0%
---
# ACSD-55427 : un administrateur ne peut pas annuler l’attribution du produit à **[!UICONTROL Product in Shared Catalogs]** sur la page du produit

Le correctif ACSD-55427 corrige le problème en raison duquel vous ne pouvez pas annuler l’attribution d’un produit à **[!UICONTROL Product in Shared Catalogs]** sur la page du produit dans le catalogue de l’administrateur Commerce. Ce correctif est disponible lorsque la version 1.1.44 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-55427. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Vous ne pouvez pas annuler l’affectation d’un produit à partir de **[!UICONTROL Product in Shared Catalogs]** sur la page du produit dans le catalogue de l’administrateur Commerce.

<u>Procédure à suivre </u> :

Conditions préalables : Adobe Commerce installé avec B2B et **[!UICONTROL Shared Catalogs]** activés.
1. Créez un produit.
1. Accédez au tableau de bord du catalogue partagé et ouvrez le catalogue partagé par défaut.
1. Affectez le produit au catalogue par défaut et définissez un prix inférieur au prix du produit.
1. Enregistrez le catalogue partagé.
1. Exécutez le [!UICONTROL CRON] pour mettre à jour les consommateurs/indexeurs.
1. Ouvrez le produit et supprimez le produit de sous **[!UICONTROL Product in Shared Catalogs]** section .

<u>Résultats attendus</u> :

Le produit doit être supprimé de sous **[!UICONTROL Product in Shared Catalogs]** section .

<u>Résultats réels</u> :

Le produit s’affiche toujours dans la section **[!UICONTROL Product in Shared Catalogs]**.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
