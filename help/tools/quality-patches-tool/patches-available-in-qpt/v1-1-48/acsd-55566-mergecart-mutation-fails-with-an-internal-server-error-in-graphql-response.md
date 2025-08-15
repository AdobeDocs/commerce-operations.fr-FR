---
title: 'ACSD-55566 : la mutation [!UICONTROL mergeCart] échoue avec une erreur de serveur interne dans la réponse [!DNL GraphQL] s'
description: Appliquez le correctif ACSD-55566 pour résoudre le problème d’Adobe Commerce où la mutation « mergeCart » échoue avec une erreur interne du serveur en réponse  [!DNL GraphQL]  la fusion des paniers source et de destination qui ont les mêmes éléments de lot.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84c6fbb9-73b3-4197-aff3-49743f0ebb2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-55566 : la mutation `mergeCart` échoue avec une erreur de serveur interne dans [!DNL GraphQL] réponse

Le correctif ACSD-55566 corrige le problème où la mutation `mergeCart` échoue avec une erreur de serveur interne dans [!DNL GraphQL] réponse. Ce correctif est disponible lorsque la version 1.1.48 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-55566. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`mergeCart` mutation échoue avec une erreur de serveur interne dans [!DNL GraphQL] réponse lors de la fusion des paniers source et de destination qui ont les mêmes éléments de lot.

<u>Procédure à suivre </u> :

1. Créez une source et un stock personnalisés.
1. Attribuez le stock créé au site web principal.
1. Créer un produit simple et lui affecter la source créée (qty=2).
1. Créez un produit groupé avec une option et un produit enfant (produit créé à l’étape 3).
1. Créez un panier d’invités via [!DNL GraphQL].
1. Ajoutez un produit groupé avec les deux options sélectionnées.
1. Enregistrez le *cartID*.
1. Créez un client et générez un jeton client.
1. Créez un panier client.
1. Ajoutez le même produit groupé avec la même configuration au panier.
1. Essayez de fusionner le panier d’invités avec le panier client.

<u>Résultats attendus</u> :

Le panier client contient des produits des deux paniers.

<u>Résultats réels</u> :

Vous obtenez une erreur interne.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
