---
title: 'ACSD-54067 : la vidéo du produit n’est pas lue sur l’appareil mobile'
description: Appliquez le correctif ACSD-54067 pour résoudre le problème d’Adobe Commerce en raison duquel une vidéo de produit n’est pas lue sur un appareil mobile.
feature: Media, Products
role: Admin, Developer
exl-id: 023e7cf7-c344-4e86-850d-741b85df87a9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 2%
---
# ACSD-54067 : la vidéo du produit n’est pas lue sur un appareil mobile

Le correctif ACSD-54067 corrige le problème en raison duquel une vidéo de produit n’est pas lue sur un appareil mobile. Ce correctif est disponible lorsque la version 1.1.41 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-54067. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une vidéo de produit n’est pas lue sur un appareil mobile.

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce.
1. Exécutez la commande :
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Accédez à **[!UICONTROL Admin product list]** page et filtrez par *[!UICONTROL SKU product_dynamic_120]*.
1. Ouvrez la page produit et accédez à **[!UICONTROL Images and Videos]** > ajouter une vidéo > remplissez l’URL : https://vimeo.com/347119375 et enregistrez.
1. Accédez à la vitrine et ouvrez la page produit pour *[!UICONTROL product_dynamic_120]*.
1. Définissez le navigateur sur *appareil mobile* avec une largeur de 320 *px* et actualisez-le.
1. Dans le curseur de la galerie, sélectionnez la vidéo et cliquez pour la lire.

<u>Résultats attendus</u> :

La vidéo du produit est lue.

<u>Résultats réels</u> :

La vidéo du produit n’est pas lue.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
