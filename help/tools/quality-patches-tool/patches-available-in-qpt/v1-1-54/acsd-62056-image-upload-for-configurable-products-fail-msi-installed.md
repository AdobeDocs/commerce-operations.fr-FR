---
title: 'ACSD-62056 : le chargement d’images pour le produit configurable échoue si MSI est installé'
description: Appliquez le correctif ACSD-62056 pour résoudre le problème d’Adobe Commerce en raison duquel les images pour les produits configurables ne sont pas ajoutées si MSI est installé.
feature: Products, Media
role: Admin, Developer
exl-id: bab8e617-d80c-4456-8ade-bdc6b4294d26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# ACSD-62056 : le chargement d’images pour le produit configurable échoue si MSI est installé

Le correctif ACSD-62056 corrige le problème où les images pour les produits configurables ne sont pas ajoutées si MSI est installé. Ce correctif est disponible lorsque la version 1.1.54 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62056. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de la modification d’un produit configurable avec [!UICONTROL Inventory Management/MSI] activé, les options permettant d’ajouter des images ne fonctionnent pas. Cela affecte à la fois les options [!UICONTROL Apply a single set of images to all SKUs] et [!UICONTROL Apply unique images by attribute to each SKU].

<u>Conditions préalables</u> :

Les modules [!UICONTROL Inventory Management/MSI] sont installés et activés.

<u>Procédure à suivre </u> :

1. Créez une nouvelle source.
1. Créez un nouveau stock et affectez la nouvelle source.
1. Modifier un produit configurable.
1. Cliquez sur **[!UICONTROL Edit Configurations]** > **[!UICONTROL Next]** > **[!UICONTROL Next]**.
1. Sélectionnez l’une des options suivantes et ajoutez une image.

   * [!UICONTROL Apply a single set of images to all SKUs]
   * [!UICONTROL Apply unique images by attribute to each SKU]

<u>Résultats attendus</u> :

Les images sont ajoutées.

<u>Résultats réels</u> :

Les images ne sont pas ajoutées.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
