---
title: 'MDVA-42237 : Prix spécial du produit configurable non mis à jour'
description: Le correctif MDVA-42237 corrige le problème en raison duquel le prix spécial du produit configurable n’est pas mis à jour après modification du prix de son sous-produit. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 est installé. L’ID de correctif est MDVA-42237. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Admin Workspace, Configuration, Orders, Personalization, Products
role: Admin
exl-id: 1bae9a14-d6c1-4ee3-85aa-5d80ef479385
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-42237 : Prix spécial du produit configurable non mis à jour

Le correctif MDVA-42237 corrige le problème en raison duquel le prix spécial du produit configurable n’est pas mis à jour après modification du prix de son sous-produit. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 est installé. L’ID de correctif est MDVA-42237. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le prix spécial du produit configurable n’est pas mis à jour après modification du prix de son sous-produit.

<u>Étapes à reproduire</u> :

1. Accédez à **Admin** > **Système** > **Gestion des index** et définissez **Mode d’index** sur **Mettre à jour par planification** pour tous les index.
1. Créez un produit configurable avec un produit simple et définissez un prix spécial pour le sous-produit.
1. Vérifiez que le prix spécial est répercuté sur le Storefront.
1. Supprimez le prix spécial à l’aide de GraphQL et vérifiez à nouveau le prix du produit sur le storefront.

<u>Résultats attendus</u> :

Le prix spécial n&#39;est plus affiché sur le storefront.

<u>Résultats réels</u> :

Le prix n’est pas mis à jour sur le storefront.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
