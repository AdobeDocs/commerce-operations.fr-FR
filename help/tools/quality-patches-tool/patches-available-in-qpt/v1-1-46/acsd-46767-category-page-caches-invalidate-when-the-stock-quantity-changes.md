---
title: 'ACSD-46767: [!UICONTROL Category] les caches de page invalident lorsque la quantité de stock change'
description: Appliquez le correctif ACSD-46767 pour résoudre le problème Adobe Commerce où la page [!UICONTROL Category] est mise en cache invalide lorsque la quantité de stock change, même si le produit est toujours en stock.
feature: Cache, Products, Inventory
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-46767 : [!UICONTROL Category] les caches de page invalident lorsque la quantité de stock change

Le correctif ACSD-46767 corrige le problème de mise en cache de la page [!UICONTROL Category] lorsque la quantité de stock change, même si le produit est toujours en stock. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.46 est installé. L’ID de correctif est ACSD-46767. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les caches de page [!UICONTROL Category] sont invalidés lorsque la quantité de stock change.

<u>Étapes à reproduire</u> :

1. Créez quelques produits et ajoutez-les à la même catégorie.
1. Ouvrez la page *[!UICONTROL Category]* sur le storefront pour vous assurer que la page est mise en cache.
1. Passez la commande avec l’un des produits de la catégorie *(la quantité du produit est modifiée, mais le produit est toujours en stock)*.
1. Ouvrez à nouveau la page [!UICONTROL Category] sur le storefront.

<u>Résultats réels</u> :

La page ne se charge pas à partir du cache. Il est regénéré.

<u>Résultats attendus</u> :

La page se charge à partir du cache.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
