---
title: 'ACSD-66506 : une erreur de serveur principal se produit après la suppression et la réaffectation de produits de catalogue partagé'
description: Appliquez le correctif ACSD-66506 pour résoudre le problème Adobe Commerce où le serveur principal renvoie l’erreur *Le produit demandé n’existe pas. Vérifiez le produit et réessayez* après avoir supprimé les produits précédemment affectés et en avoir affecté de nouveaux à un catalogue partagé.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8f77101832ccfb415d040c202f0fc7221f97419a
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# ACSD-66506 : une erreur de serveur principal se produit après la suppression et la réaffectation de produits de catalogue partagé

Le correctif ACSD-66506 corrige le problème en raison duquel le serveur principal renvoie l’erreur *Le produit demandé n’existe pas. Vérifiez le produit et réessayez* après avoir supprimé les produits précédemment affectés et en avoir affecté de nouveaux à un catalogue partagé. Ce correctif est disponible lorsque la version 1.1.68 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66506. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Après avoir supprimé des produits précédemment affectés et en avoir affecté de nouveaux à un **[!UICONTROL Shared Catalog]**, le serveur principal renvoie l’erreur suivante : *Le produit demandé n’existe pas. Vérifiez le produit et réessayez*

<u>Procédure à suivre </u> :

1. Créez des produits à l’aide de la boîte à outils de performances : `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`
1. Accédez à **[!UICONTROL [!DNL B2B] Features]** Configuration , puis définissez **[!UICONTROL Enable Company]** et **[!UICONTROL Enable Shared Catalog]** sur `Yes`.
1. Créez un catalogue partagé.
1. Affectez tous les produits générés au catalogue partagé nouvellement créé.
1. Utilisez **[!UICONTROL Product Import]** pour supprimer un produit qui a été affecté au catalogue partagé.
   1. Exportez un produit filtré par SKU.
   1. Sélectionnez **[!UICONTROL Import Behavior: Delete]**, puis importez le même fichier.
1. Ouvrez le **[!UICONTROL Shared Catalog]** et configurez la tarification et la structure.
   1. Sélectionnez **[!UICONTROL Set Pricing and Structure]**.
   1. Cliquez sur **[!UICONTROL Next]**, puis sur **[!UICONTROL Generate Catalog]**.
   1. Cliquez sur **[!UICONTROL Save]**.

<u>Résultats attendus</u> :

Aucune erreur ne se produit et les produits restent dans le catalogue partagé même si une erreur se produit.

<u>Résultats réels</u> :

Une erreur se produit : *Le produit demandé n&#39;existe pas. Vérifiez le produit, puis réessayez* et tous les produits sont supprimés du catalogue partagé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
