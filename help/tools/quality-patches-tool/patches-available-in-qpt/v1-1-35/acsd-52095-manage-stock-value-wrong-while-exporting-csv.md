---
title: 'ACSD-52095 : la gestion de la valeur boursière est incorrecte lors de l’exportation du fichier CSV'
description: Appliquez le correctif ACSD-52095 pour résoudre le problème d’Adobe Commerce en raison duquel la valeur du stock de gestion de produit est incorrecte lors de l’exportation du fichier CSV.
feature: Inventory, Products
role: Admin, Developer
exl-id: 1f8415aa-23c6-480a-b54d-37b2b2d3199a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-52095 : la valeur [!UICONTROL Manage Stock] est incorrecte lors de l’exportation du fichier CSV

Le correctif ACSD-52095 corrige le problème en raison duquel la valeur de `manage_stock` de produit est incorrecte lors de l’exportation du fichier CSV. Ce correctif est disponible lorsque la version 1.1.35 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-52095. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La valeur `manage_stock` est incorrectement définie sur 0 dans le fichier CSV après l’exportation du produit.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** et définissez **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. Créez un nouveau produit et enregistrez-le.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. Sélectionnez *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* et exportez les produits.
1. Vérifiez le fichier CSV généré : `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Accédez à nouveau à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]**, puis définissez **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. Accédez à **Système** > **Exporter**.
Sélectionnez *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. Vérifiez le fichier CSV généré : `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Ouvrez le produit dans l’interface d’administration, accédez à **[!UICONTROL Advanced Inventory]** et vérifiez la valeur **[!UICONTROL Manage Stock]**.

<u>Résultats attendus</u>

La valeur **[!UICONTROL Manage Stock]** est *1* lorsqu’elle est activée pour les produits.

<u>Résultats réels</u>

La valeur **[!UICONTROL Manage Stock]** est *0* lorsqu’elle est activée pour les produits.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le guide de [!DNL Quality Patches Tool].
