---
title: 'ACSD-49129 : attribut « Content » non renvoyé dans les réponses de l’API de média du produit'
description: Appliquez le correctif ACSD-49129 pour résoudre le problème d’Adobe Commerce en raison duquel l’attribut *content* (*code d’image base64*) n’est pas renvoyé dans les réponses de l’API de média de produit « rest/V1/products/sku/media ».
feature: REST, Attributes, Media, Page Content, Products
role: Admin
exl-id: 5235b7d1-4ebf-4cfb-8605-47614306a122
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-49129 : attribut « Content » non renvoyé dans les réponses de l’API de média du produit

Le correctif ACSD-49129 corrige le problème où l’attribut *content* (*[!UICONTROL base64 image code]*) n’est pas renvoyé dans les réponses de l’API de média du produit `rest/V1/products/sku/media`. Ce correctif est disponible lorsque la version 1.1.30 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-49129. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’attribut *content* (*[!UICONTROL base64 image code]*) n’est pas renvoyé dans les réponses de l’API de média du produit `rest/V1/products/sku/media`.

<u>Procédure à suivre </u> :

1. Créez un produit avec une image.
1. Envoyez la requête *API REST GET* à `rest/V1/products/<sku>/media` et `rest/V1/products/<sku>/media/<entryId>`.
1. Vérifiez les réponses de l’API.

<u>Résultats attendus</u>

L’attribut *content* avec les données est disponible via l’API REST.

<u>Résultats réels</u>

L’attribut *content* n’est pas présent dans les réponses de l’API.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
