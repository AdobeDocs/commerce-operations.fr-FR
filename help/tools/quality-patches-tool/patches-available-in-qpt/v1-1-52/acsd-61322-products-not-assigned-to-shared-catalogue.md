---
title: "ACSD-61322 : les produits non attribués à [!UICONTROL Shared Catalogue] sont inclus dans le plan de site XML"
description: Appliquez le correctif ACSD-61322 pour résoudre le problème Adobe Commerce en raison duquel les produits/catégories non affectés au groupe [!UICONTROL Shared Catalog] par défaut (général) sont toujours inclus dans le plan de site XML.
feature: Site Navigation, B2B
role: Admin, Developer
source-git-commit: 1eed4f1f6484112a0ec728659aa4b79855bf9612
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-61322 : les produits non attribués à [!UICONTROL Shared Catalogue] sont inclus dans le plan de site XML

Le correctif ACSD-61322 corrige le problème en raison duquel les produits/catégories non affectés au groupe [!UICONTROL Shared Catalog] par défaut (Général) sont toujours inclus dans le plan de site XML. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 est installé. L’ID de correctif est ACSD-61322. Veuillez noter que ce problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits/catégories non affectés au [!UICONTROL Shared Catalog] pour le groupe Par défaut (Général) sont toujours inclus dans le plan du site XML.

<u>Étapes à reproduire</u> :

1. Créez quelques catégories et ajoutez des produits (par exemple, Catégorie 1 avec Catégorie 2).
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** et activez *[!UICONTROL Company and Shared Catalog]*.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** et modifiez le catalogue par défaut.
1. Dans la liste déroulante **[!UICONTROL Select]**, sélectionnez **[!UICONTROL Set Pricing and Structure]**, puis cliquez sur **[!UICONTROL Configure]**.
1. Sous la catégorie *Catégorie 1 > Catégorie 2* , désélectionnez certains produits qui ne doivent pas se trouver dans la catégorie [!UICONTROL Shared Catalog].
1. Cliquez sur **[!UICONTROL Next]** et générez le catalogue.
1. Sur le storefront, créez un compte client.
1. Allez dans la catégorie *Catégorie 1 > Catégorie 2* . Il affiche uniquement les produits affectés à [!UICONTROL Shared Catalog].
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL Site Map]** et générez un nouveau plan du site.
1. Ouvrez le `sitemap.xml` sur le storefront.
1. Recherchez le ou les produits que vous n’avez pas inclus dans le [!UICONTROL Shared Catalog].

<u>Résultats attendus</u> :

Le plan de site ne contient pas de liens vers des produits et des catégories qui ne sont pas affectés à l’élément [!UICONTROL Shared Catalog].

<u>Résultats réels</u> :

Le plan du site contient des liens vers des produits et des catégories qui ne sont pas affectés à [!UICONTROL Shared Catalog].

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].