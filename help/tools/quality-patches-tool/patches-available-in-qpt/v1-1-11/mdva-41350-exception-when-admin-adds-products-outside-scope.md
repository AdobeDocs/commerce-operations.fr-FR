---
title: 'MDVA-41350 : exception lorsque l’administrateur ajoute des produits en dehors de leur accès'
description: Le correctif MDVA-41350 corrige le problème lorsqu’une erreur d’exception est générée au lieu d’une notification d’accès limitée lorsqu’un utilisateur administrateur ajoute un produit dans la commande par SKU qui est hors de son accès. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 est installé. L’ID de correctif est MDVA-41350. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Admin Workspace, Products
role: Admin
exl-id: 4dc5ee5c-bd93-42e1-9c63-93ffb8e5f21c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-41350 : exception lorsque l’administrateur ajoute des produits en dehors de leur accès

Le correctif MDVA-41350 corrige le problème lorsqu’une erreur d’exception est générée au lieu d’une notification d’accès limitée lorsqu’un utilisateur administrateur ajoute un produit dans la commande par SKU qui est hors de son accès. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 est installé. L’ID de correctif est MDVA-41350. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsqu’un utilisateur administrateur disposant d’un accès restreint ajoute un produit par SKU en dehors de son accès dans l’ordre, une exception se produit au lieu d’un message l’informant de son accès limité.

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur en tant qu’utilisateur ayant accès à un site web spécifique uniquement.
1. Accédez à **Sales** > **Commandes** et cliquez sur **Create New Order** (Créer une commande).
1. Sélectionnez un client et une vue de magasin.
1. Cliquez sur **Ajouter des produits par SKU**.
1. Recherchez un SKU qui n’est affecté à aucun site web ou qui n’est pas affecté au site web auquel vous avez accès.
1. Cliquez sur **Ajouter à la commande**.

<u>Résultats attendus</u> :

Un message d’erreur approprié s’affiche.

<u>Résultats réels</u> :

Une exception se produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
