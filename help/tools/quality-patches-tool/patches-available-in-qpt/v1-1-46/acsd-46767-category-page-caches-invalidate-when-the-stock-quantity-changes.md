---
title: 'ACSD-46767 : les caches de page [!UICONTROL Category] sont invalidés lorsque la quantité de stock change'
description: Appliquez le correctif ACSD-46767 pour résoudre le problème d’Adobe Commerce en raison duquel la page [!UICONTROL Category] est mise en cache et invalide lorsque la quantité de stock change, même si le produit est toujours en stock.
feature: Cache, Products, Inventory
role: Admin, Developer
exl-id: 5872dca7-fdef-47ad-8718-bf343cd3a42a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-46767 : les caches de page [!UICONTROL Category] sont invalidés lorsque la quantité de stock change

Le correctif ACSD-46767 corrige le problème en raison duquel la page [!UICONTROL Category] est mise en cache et invalide lorsque la quantité de stock change, même si le produit est toujours en stock. Ce correctif est disponible lorsque la version 1.1.46 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-46767. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les caches de page [!UICONTROL Category] sont invalidés lorsque la quantité de stock change.

<u>Procédure à suivre </u> :

1. Créer quelques produits et les ajouter à la même catégorie.
1. Ouvrez la page *[!UICONTROL Category]* sur le storefront pour vous assurer qu’elle est mise en cache.
1. Passez la commande avec l&#39;un des produits de la catégorie *(la quantité de produit a changé, mais le produit est toujours en stock)*.
1. Ouvrez à nouveau la page [!UICONTROL Category] sur le storefront.

<u>Résultats réels</u> :

La page ne se charge pas à partir du cache. Il est généré de nouveau.

<u>Résultats attendus</u> :

La page se charge à partir du cache.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
