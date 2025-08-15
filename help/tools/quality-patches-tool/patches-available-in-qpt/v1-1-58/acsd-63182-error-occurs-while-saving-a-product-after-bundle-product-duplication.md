---
title: 'ACSD-63182 : une erreur se produit lors de l’enregistrement d’un produit après la duplication du bundle de produits'
description: Appliquez le correctif ACSD-63182 pour résoudre le problème d’Adobe Commerce en raison duquel une erreur se produit lors de l’enregistrement d’un produit après la duplication d’un produit groupé avec MSI activé.
feature: Inventory, Catalog Management
Role: Admin, Developer
exl-id: 2c664c89-e00e-40a8-9127-8c3f36c5bab9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-63182 : une erreur se produit lors de l’enregistrement d’un produit après la duplication du bundle de produits

Le correctif ACSD-63182 corrige le problème où un produit simple utilisé comme option de lot ne pouvait pas être enregistré après la duplication du produit du lot. Ce correctif est disponible lorsque la version 1.1.58 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63182. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur se produit lors de l’enregistrement d’un produit simple utilisé comme option de lot après la duplication du produit du lot.

<u>Procédure à suivre </u> :

1. Créez une source et un stock MSI.
1. Créez deux produits simples : **p1** et **p2**.
1. Créez un produit groupé **b1** avec **p1** et **p2** comme options groupées.
1. Modifiez le **produit groupé b1** et cliquez sur ***[!UICONTROL Save and Duplicate]***.
1. Modifiez le **produit simple p1** et cliquez sur **[!UICONTROL Save]**.

<u>Résultats attendus</u> :

Le produit est enregistré sans erreur.

<u>Résultats réels</u> :

L’erreur suivante s’affiche :
*Exception : l&#39;élément (Magento\Catalog\Model\Product\Interceptor) portant le même ID &#39;XXX&#39; existe déjà.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
