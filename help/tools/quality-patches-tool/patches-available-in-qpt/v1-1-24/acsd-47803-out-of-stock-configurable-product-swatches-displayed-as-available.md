---
title: 'ACSD-47803 : échantillons de produits configurables en rupture de stock affichés comme disponibles'
description: Appliquez le correctif ACSD-47803 pour résoudre le problème d’Adobe Commerce où des échantillons de produits configurables en rupture de stock s’affichaient comme disponibles.
feature: Configuration, Orders, Products
role: Admin
exl-id: c1b80949-65ed-4a44-8be4-25decda32142
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-47803 : échantillons de produits configurables en rupture de stock affichés comme disponibles

Le correctif ACSD-47803 corrige le problème d’affichage des échantillons de produits configurables en rupture de stock. Ce correctif est disponible lorsque la version 1.1.24 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47803. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Des échantillons de produits configurables en rupture de stock s’affichent selon la disponibilité.

<u>Procédure à suivre </u> :

>[!NOTE]
>
>Les étapes ci-dessous se rapportent à des exemples de données.

1. Dans [!UICONTROL Commerce] Admin, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** et définissez la **[!UICONTROL Display Out of Stock Products]** sur *Oui*.
1. À nouveau, dans l’Administration, accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et modifiez un produit configurable dans la page de modification du produit (par exemple, le SKU « WB04 », si vous utilisez des données d’exemple) :
   * Pour l’une des variantes de configuration, définissez la quantité sur *0* (par exemple, pour « WB04-M-Purple »).
1. Ouvrez maintenant le produit configurable sur le storefront.
1. Sélectionnez la taille de produit pour la variante configurable sans stock (c’est-à-dire « M »).

<u>Résultats attendus</u> :

Les options en rupture de stock sont désactivées et marquées comme [!UICONTROL Out of Stock].

<u>Résultats réels</u> :

Tous les échantillons de couleurs sont activés, même celui qui est [!UICONTROL Out of Stock].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
