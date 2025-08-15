---
title: 'ACSD-53204 : erreur « Impossible d’enregistrer le produit » sur les demandes simultanées d’ajout d’images à la galerie'
description: Appliquez le correctif ACSD-53204 pour résoudre le problème Adobe Commerce où *Le produit ne peut pas être enregistré* une erreur est générée lors de requêtes simultanées pour ajouter des images à la galerie de produits à l’aide du point d’entrée rest/V1/products/&lt;sku&gt;/media.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: 7fdf41e5-46ef-4505-b8ce-c330bd899fa1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53204 : erreur « *Le produit ne peut pas être enregistré* » sur les demandes simultanées d’ajout d’images à la galerie

Le correctif ACSD-53204 corrige le problème où l’erreur « *Le produit ne peut pas être enregistré* » est générée lors de demandes simultanées d’ajout d’images à la galerie de produits à l’aide du point d’entrée `rest/V1/products/<sku>/media`. Ce correctif est disponible lorsque la version 1.1.39 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-53204. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’erreur « *Le produit ne peut pas être enregistré* » est générée lors de requêtes simultanées pour ajouter des images à la galerie de produits à l’aide du point d’entrée `rest/V1/products/<sku>/media`.

<u>Procédure à suivre </u> :

1. Connectez-vous au Panneau d’administration.
1. Créez un produit avec la SKU p1.
1. Envoyez plusieurs requêtes simultanées au point d’entrée `rest/V1/products/<sku>/media` pour charger plusieurs images simultanément.

<u>Résultats attendus</u> :

Les images sont enregistrées sans erreur.

<u>Résultats réels</u> :

L’erreur « *Le produit ne peut pas être enregistré* » est renvoyée de temps à autre.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
