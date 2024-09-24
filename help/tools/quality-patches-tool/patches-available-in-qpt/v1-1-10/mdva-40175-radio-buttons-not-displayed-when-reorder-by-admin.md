---
title: 'MDVA-40175 : Boutons radio non affichés lors de la réorganisation'
description: Le correctif MDVA-40175 résout le problème en raison duquel les boutons radio ne s’affichent pas lorsque les utilisateurs tentent de les réorganiser. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 est installé. L’ID de correctif est MDVA-40175. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-40175 : Boutons radio non affichés lors d’une réorganisation

Le correctif MDVA-40175 résout le problème en raison duquel les boutons radio ne s’affichent pas lorsque les utilisateurs tentent de les réorganiser. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 est installé. L’ID de correctif est MDVA-40175. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les boutons radio ne s’affichent pas dans la section Informations de paiement et d’expédition lorsque les utilisateurs tentent de procéder à une nouvelle commande.

<u>Conditions préalables</u> :

1. Un compte client avec une adresse de livraison et une adresse de facturation est créé.
1. Un produit simple est créé.
1. Plusieurs méthodes de diffusion sont configurées.
1. Au moins une commande est créée.

<u>Étapes à reproduire</u> :

1. Accédez au panneau d’administration > **Ventes** > **Commandes**.
1. Sélectionnez l’ordre créé.
1. Cliquez sur le lien **Afficher** .
1. Cliquez sur le bouton **Réorganiser** .
1. Faites défiler la page jusqu’à la section **Informations de paiement et d’expédition**.
1. Cliquez sur **Cliquez pour modifier la méthode d’expédition**.

<u>Résultats attendus</u> :

La liste des méthodes de diffusion avec boutons radio s&#39;affiche.

<u>Résultats réels</u> :

La liste des méthodes de diffusion sans bouton radio s&#39;affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
