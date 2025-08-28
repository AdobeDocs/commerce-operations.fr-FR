---
title: 'ACP2E-3767 : l’option Dernier lot réapparaît après l’enregistrement d’un produit groupé'
description: Appliquez le correctif ACP2E-3767 pour résoudre le problème d’Adobe Commerce en raison duquel la dernière option de bundle d’un produit groupé n’a pas pu être supprimée.
feature: Products, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f39442925d9cc82087af9e84d91137a0fcd0ec14
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# ACP2E-3767 : l’option Dernier lot réapparaît après l’enregistrement d’un produit groupé

Le correctif ACP2E-3767 corrige le problème où la dernière option de lot réapparaît après l’enregistrement du produit du lot. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACP2E-3767. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Impossible de supprimer la dernière option de lot d’un produit du lot.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**.
1. Sélectionnez **[!UICONTROL Simple Product]** dans la liste déroulante.
1. Saisissez les données requises et enregistrez-les.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**.
1. Sélectionnez **[!UICONTROL Bundle Product]** dans la liste déroulante.
1. Saisissez les données requises.
1. Dans Éléments groupés, cliquez sur **[!UICONTROL Add Option]**.
1. Ajoutez un titre à la nouvelle option, puis cliquez sur **[!UICONTROL Add Products to Option]**.
1. Sélectionnez le produit simple créé précédemment, puis **[!UICONTROL Add Selected Products]**.
1. Enregistrez le produit groupé.
1. Supprimez l’option de lot et enregistrez.

<u>Résultats attendus</u> :

1. L’option de lot a été supprimée.
1. Un message s’affiche si la suppression n’est pas autorisée.

<u>Résultats réels</u> :

1. L’option de lot reste active.
1. Aucune erreur ou notification n’est affichée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
