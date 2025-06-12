---
title: 'ACSD-49370 : l’attribut de produit est de type « FilterMatchTypeInput » dans le schéma GraphQL'
description: Appliquez le correctif ACSD-49370 pour résoudre le problème d’Adobe Commerce en raison duquel l’attribut de produit est de type « FilterMatchTypeInput » dans le schéma GraphQL.
feature: Admin Workspace, Attributes, GraphQL, Products
role: Admin
exl-id: 05cc6db6-6ea6-4eb7-8dc0-fcb9f479fd89
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-49370 : l’attribut de produit est de type `FilterMatchTypeInput` dans le schéma GraphQL

Le correctif ACSD-49370 corrige le problème en raison duquel l’attribut de produit possède un type `FilterMatchTypeInput` dans le schéma GraphQL. Ce correctif est disponible lorsque la version 1.1.28 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-49370. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’attribut de produit possède un type `FilterMatchTypeInput` dans le schéma GraphQL.

<u>Procédure à suivre </u> :

1. Créez l’attribut de produit *Date et heure*.

   * [!UICONTROL Type] : [!UICONTROL DateTime]
   * [!UICONTROL Default Label] : [!UICONTROL Date Time]
   * [!UICONTROL Use in Search] : [!UICONTROL Yes]
   * [!UICONTROL Visible in Advanced Search] : [!UICONTROL Yes]

1. Recherchez la définition de type de `ProductAttributeFilterInput` dans la documentation *API GQL*.
1. Observez le type d’entrée pour l’attribut créé.

<u>Résultats attendus</u> :

L’attribut *Date et heure* affiche le `FilterRangeTypeInput` de type d’entrée du filtre.

<u>Résultats réels</u> :

L’attribut *Date et heure* affiche le `FilterMatchInputType` de type d’entrée du filtre.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
