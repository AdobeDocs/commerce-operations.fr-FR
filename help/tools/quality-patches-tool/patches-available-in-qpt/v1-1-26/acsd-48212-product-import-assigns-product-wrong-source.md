---
title: 'ACSD-48212 : l’importation de produit affecte un produit à une source incorrecte'
description: Appliquez le correctif ACSD-48212 pour résoudre le problème d’Adobe Commerce où l’importation du produit affecte le produit à la mauvaise source.
feature: Admin Workspace, Data Import/Export, Products
role: Admin
exl-id: d573d95b-95fc-4f59-b518-18088855a154
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%
---
# ACSD-48212 : l’importation de produit affecte un produit à une source incorrecte

Le correctif ACSD-48212 corrige le problème en raison duquel l’importation du produit affecte le produit à une source incorrecte. Ce correctif est disponible lorsque la version 1.1.26 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-48212. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’importation de produits affecte le produit à une source incorrecte.

<u>Procédure à suivre </u> :

1. Créez une source d&#39;inventaire secondaire.
1. Créez un produit avec l&#39;origine d&#39;inventaire par défaut uniquement.
1. Exportez le produit.
1. Exécutez `bin/magento cron:run`.
1. Ouvrez **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Sélectionnez le produit dans la grille.
1. Annulez l&#39;affectation du stock à l&#39;aide du menu *[!UICONTROL mass action]*.
1. Exécutez `bin/magento cron:run`.
1. Attribuez la source secondaire à l’aide du menu *[!UICONTROL mass action]*.
1. Exécutez `bin/magento cron:run`.
1. Supprimez le produit à l’aide du menu *[!UICONTROL mass action]* .
1. Exécutez `bin/magento cron:run`.
1. Importez le produit à l’aide du fichier CSV précédemment exporté.
1. Vérifiez l’affectation de la source.

<u>Résultats attendus</u> :

Le produit est affecté à la source par défaut uniquement.

<u>Résultats réels</u> :

Le produit est affecté à la fois à la source par défaut et à la source secondaire.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
