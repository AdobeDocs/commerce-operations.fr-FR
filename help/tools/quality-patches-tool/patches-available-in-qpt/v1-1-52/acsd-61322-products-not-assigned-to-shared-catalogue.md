---
title: 'ACSD-61322 : les produits non affectés à [!UICONTROL Shared Catalogue] sont inclus dans le plan de site XML'
description: Appliquez le correctif ACSD-61322 pour résoudre le problème d’Adobe Commerce où les produits/catégories non affectés au [!UICONTROL Shared Catalog] pour le groupe par défaut (Général) sont toujours inclus dans le plan de site XML.
feature: Site Navigation, B2B
role: Admin, Developer
exl-id: 4698ba5a-673e-4bf0-b36c-39f6122dab26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-61322 : les produits non affectés à [!UICONTROL Shared Catalogue] sont inclus dans le plan de site XML

Le correctif ACSD-61322 corrige le problème où les produits/catégories non affectés au [!UICONTROL Shared Catalog] pour le groupe par défaut (Général) sont toujours inclus dans le plan de site XML. Ce correctif est disponible lorsque la version 1.1.52 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-61322. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits/catégories non affectés au [!UICONTROL Shared Catalog] pour le groupe Par défaut (Général) sont toujours inclus dans le plan de site XML.

<u>Procédure à suivre </u> :

1. Créez quelques catégories et ajoutez des produits (par exemple, la catégorie 1 avec la catégorie 2).
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** et activez *[!UICONTROL Company and Shared Catalog]*.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** et modifiez le catalogue par défaut.
1. Dans la liste déroulante **[!UICONTROL Select]**, sélectionnez **[!UICONTROL Set Pricing and Structure]**, puis cliquez sur **[!UICONTROL Configure]**.
1. Sous la catégorie *Catégorie 1 > Catégorie 2*, désélectionnez certains produits qui ne doivent pas se trouver dans la [!UICONTROL Shared Catalog].
1. Cliquez sur **[!UICONTROL Next]** et générez le catalogue.
1. Sur Storefront, créez un compte client.
1. Accédez à la catégorie *Catégorie 1 > Catégorie 2*. Elle affiche uniquement les produits qui ont été affectés au [!UICONTROL Shared Catalog].
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL Site Map]** et générez un nouveau plan du site.
1. Ouvrez le `sitemap.xml` sur la vitrine.
1. Recherchez le ou les produits que vous n’avez pas inclus dans le [!UICONTROL Shared Catalog].

<u>Résultats attendus</u> :

Le plan du site ne contient pas de liens vers des produits et des catégories qui ne sont pas affectés au [!UICONTROL Shared Catalog].

<u>Résultats réels</u> :

Le plan du site contient des liens vers des produits et des catégories qui ne sont pas affectés au [!UICONTROL Shared Catalog].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
