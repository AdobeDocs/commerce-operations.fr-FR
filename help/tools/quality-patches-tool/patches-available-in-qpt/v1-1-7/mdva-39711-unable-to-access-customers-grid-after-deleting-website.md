---
title: 'MDVA-39711 : impossible d’accéder à la grille des clients après la suppression du site web'
description: Le correctif MDVA-39711 corrige le problème en raison duquel l’utilisateur administrateur ne peut pas accéder à la grille des clients après avoir supprimé le site web. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7 est installé. L’ID de correctif est MDVA-39711. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
feature: Configuration
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-39711 : impossible d’accéder à la grille des clients après la suppression du site web

Le correctif MDVA-39711 corrige le problème en raison duquel l’utilisateur administrateur ne peut pas accéder à la grille des clients après avoir supprimé le site web. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7 est installé. L’ID de correctif est MDVA-39711. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7-p2, 2.3.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur administrateur ne peut pas accéder à la grille des clients après la suppression du site web.

<u>Étapes à reproduire</u> :

1. Créez un site web, un magasin et une vue de magasin.
1. Créez un client sur l’administrateur et associez-le au site web créé.
1. Accédez à **Magasins** > **Tous les magasins** et supprimez le site web créé.
1. Accédez à **Customers** > **Tous les clients**.

<u>Résultats attendus</u> :

* Aucun message d’erreur n’est affiché.
* Tous les clients sont visibles dans la grille.

<u>Résultats réels</u> :

* L’utilisateur reçoit un message d’erreur : *Le site web avec l’ID 2 demandé est introuvable. Vérifiez le site web et réessayez*
* Tous les clients ne sont pas affichés.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].