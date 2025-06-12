---
title: 'ACSD-54111 : l’image miniature du produit ne s’affiche pas'
description: Appliquez le correctif ACSD-54111 pour résoudre le problème d’Adobe Commerce où toutes les images sont remplacées par l’image d’espace réservé de produit par défaut.
feature: Products
role: Admin, Developer
exl-id: 4615ebf6-aa68-4d49-8d91-e9756b3d4a05
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54111 : l’image miniature du produit ne s’affiche pas

Le correctif ACSD-54111 corrige le problème où toutes les images sont remplacées par l’image d’espace réservé de produit par défaut. Ce correctif est disponible lorsque la version 1.1.38 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54111. Notez que le problème a été résolu dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) : 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) : 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’image miniature du produit ne s’affiche pas.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]** > **[!UICONTROL Edit Theme]** > **[!UICONTROL Product Image Watermarks]** > **[!UICONTROL Thumbnail]**.
1. Chargez l’image avec une miniature et définissez la position de l’image sur *[!UICONTROL Center]*.
1. Cliquez sur **[!UICONTROL Save Configuration]**.
1. Effacez le cache.
1. Accédez au storefront en tant qu’invité/client.
1. Ajoutez un produit au panier.
1. Exécutez `bin/magento catalog:image:resize` à partir de la console.
1. Ouvrez le mini-panier sur le serveur frontal ou la grille de produit sur le serveur principal pour voir si les miniatures d’image sont visibles.

<u>Résultats attendus</u> :

Les images du produit ne sont pas remplacées par l’image d’espace réservé.

<u>Résultats réels</u> :

Les images du produit sont remplacées par l’image d’espace réservé du produit par défaut.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
