---
title: 'ACSD-54965 : [!UICONTROL Visual Merchandising] grille n''affiche pas le bon stock'
description: Appliquez le correctif ACSD-54965 pour résoudre le problème d’Adobe Commerce où la grille de [!UICONTROL Visual Merchandising] n’affiche pas le stock correct lorsqu’un produit est affecté au stock personnalisé.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: bd8a3547-1d84-4a17-b006-b35d92256211
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-54965 : [!UICONTROL Visual Merchandising] grille n&#39;affiche pas le bon stock

Le correctif ACSD-54965 corrige le problème où la grille de [!UICONTROL Visual Merchandising] n’affiche pas le stock correct lorsqu’un produit est affecté à un stock personnalisé. Ce correctif est disponible lorsque la version 1.1.45 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54965. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La grille de [!UICONTROL Visual Merchandising] n’affiche pas le stock correct lorsqu’un produit est affecté à un stock personnalisé.

<u>Procédure à suivre </u> :

1. Créez une nouvelle source.
1. Créez un nouveau stock.
1. Créez deux produits :
   * Un seul produit avec le stock personnalisé uniquement.
   * Un produit avec le stock par défaut uniquement.
1. Ajoutez ces produits à une catégorie.
1. Accédez à la grille de [!UICONTROL visual Merchandising] (*[!UICONTROL Products in Category]*).

<u>Résultats réels</u> :

Dans les portées de *[!UICONTROL All Store Views]*, le produit avec stock personnalisé n’affiche aucune quantité. Ce n’est que lorsque la portée de la *[!UICONTROL Default Store View]* est sélectionnée que le stock personnalisé affiche la quantité du produit.

<u>Résultats attendus</u> :

La grille affiche toutes les informations sur le stock si la portée est *[!UICONTROL All Store Views]*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
