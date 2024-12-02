---
title: 'MDVA-37115 : un avis "Seulement 0 gauche" s’affiche sur la page du produit.'
description: Le correctif MDVA-37115 résout le problème en raison duquel l’avis inutile *Seul 0 gauche* s’affiche sur la page du produit configurable. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID de correctif est MDVA-37115. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
feature: Configuration, Products, Orders
role: Admin
exl-id: ba94b2fd-6a7d-4194-afd8-798854431b57
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# MDVA-37115 : un avis &quot;Seulement 0 gauche&quot; s’affiche sur la page du produit.

Le correctif MDVA-37115 résout le problème en raison duquel l’avis inutile *Uniquement 0 left* s’affiche sur la page du produit configurable. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID de correctif est MDVA-37115. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (tous les types de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (tous les types de déploiement) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un avis *Seul 0 gauche* superflu s’affiche sur la page du produit configurable.

<u>Conditions préalables</u> :

Les modules d’inventaire sont installés.

<u>Étapes à reproduire</u> :

1. Créez un produit configurable avec peu d’options.
1. Allez au front-end.
1. Ouvrez la page de produit configurable et sélectionnez n’importe quelle option.

<u>Résultats attendus</u> :

Aucun avis *Seul 0 de gauche* s’affiche sur la page du produit.

<u>Résultats réels</u> :

*Seul 0 de gauche* s’affiche sur la page du produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [Outil de correctifs de qualité publié : un nouvel outil pour appliquer des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
