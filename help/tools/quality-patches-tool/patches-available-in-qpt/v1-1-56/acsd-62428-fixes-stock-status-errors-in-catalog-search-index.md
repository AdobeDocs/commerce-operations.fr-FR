---
title: 'ACSD-62428 : erreurs d’état des stocks dans l’index de recherche de catalogue'
description: Appliquez le correctif ACSD-62428 pour résoudre le problème où la valeur « is_out_of_stock » dans l’index de recherche catalogue est incorrectement définie lorsque le SKU n’est pas un attribut consultable.
feature: Inventory, Catalog Management
role: Admin, Developer
exl-id: 4b9d7e4c-f522-4d75-8fc9-dcf14287d02a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62428 : erreurs d’état des stocks dans l’index de recherche de catalogue

Le correctif ACSD-62428 corrige le problème où les valeurs de `is_out_of_stock` dans l’index de recherche catalogue sont définies sur une valeur incorrecte lorsque l’attribut de SKU n’est pas défini comme indexable. Ce correctif est disponible avec la version 1.1.56 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). L’ID du correctif est ACSD-62428. Notez que le problème devait être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p5

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La valeur `is_out_of_stock` de l’index de recherche catalogue est définie sur une valeur incorrecte lorsque le SKU n’est pas configuré en tant qu’attribut consultable, ce qui entraîne une représentation boursière inexacte.

<u>Procédure à suivre </u> :

1. Créez un [!UICONTROL Source] et un [!UICONTROL Stock] personnalisés.
1. Créez trois produits simples et affectez leur inventaire au [!UICONTROL Source] personnalisé. Affectez ces produits à une catégorie.
1. Définissez le *[!UICONTROL Inventory (MSI) Indexer]* sur *[!UICONTROL Update on Save]* pour une réplication plus facile.
1. Définissez la *[!UICONTROL Source Item Status]* sur *[!UICONTROL In Stock]* et attribuez-lui un *[!UICONTROL Quantity]*.
1. Enregistrez le produit.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**, puis ouvrez l’attribut **[!UICONTROL SKU]** .
1. Définissez *[!UICONTROL Use In]* sur *[!UICONTROL No]*.
1. Modifiez la quantité de produit (assurez-vous qu&#39;elle n&#39;est pas définie sur 0).
1. Enregistrez le produit.

<u>Résultats attendus</u> :

La valeur `is_out_of_stock` reflète précisément l’état du stock du produit, même si le SKU n’est pas un attribut consultable.

<u>Résultats réels</u> :

La valeur `is_out_of_stock` est incorrectement définie sur 1 et l’attribut SKU est absent des données indexées.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
