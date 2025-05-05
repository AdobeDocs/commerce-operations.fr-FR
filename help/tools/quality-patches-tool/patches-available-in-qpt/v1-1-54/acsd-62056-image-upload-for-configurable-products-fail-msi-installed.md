---
title: 'ACSD-62056 : Échec du chargement des images pour un produit configurable si MSI est installé'
description: Appliquez le correctif ACSD-62056 pour résoudre le problème Adobe Commerce en raison duquel les images pour les produits configurables ne sont pas ajoutées si MSI est installé.
feature: Products, Media
role: Admin, Developer
source-git-commit: 9c186e936492ebcab3903949f40d73745d2a28d3
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# ACSD-62056 : Échec du chargement des images pour un produit configurable si MSI est installé

Le correctif ACSD-62056 corrige le problème en raison duquel les images pour les produits configurables ne sont pas ajoutées si MSI est installé. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 est installé. L’ID de correctif est ACSD-62056. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de la modification d’un produit configurable avec [!UICONTROL Inventory Management/MSI] activé, les options d’ajout d’images ne fonctionnent pas. Cela affecte les options [!UICONTROL Apply a single set of images to all SKUs] et [!UICONTROL Apply unique images by attribute to each SKU].

<u>Conditions préalables</u> :

Les modules [!UICONTROL Inventory Management/MSI] sont installés et activés.

<u>Étapes à reproduire</u> :

1. Créez une source.
1. Créez un nouveau stock et affectez la nouvelle source.
1. Modifiez un produit configurable.
1. Cliquez sur **[!UICONTROL Edit Configurations]** > **[!UICONTROL Next]** > **[!UICONTROL Next]**.
1. Sélectionnez l’une des options suivantes et ajoutez une image.

   * [!UICONTROL Apply a single set of images to all SKUs]
   * [!UICONTROL Apply unique images by attribute to each SKU]

<u>Résultats attendus</u> :

Les images sont ajoutées.

<u>Résultats réels</u> :

Les images ne sont pas ajoutées.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
