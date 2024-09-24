---
title: 'MDVA-26005 : impossible de sélectionner une catégorie dans l’arborescence pour les conditions des règles de prix du panier'
description: Le correctif MDVA-26005 résout le problème en raison duquel les utilisateurs ne peuvent pas sélectionner une catégorie dans l’arborescence de catégories pour les conditions de la règle Prix du panier. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 est installé. L’ID de correctif est MDVA-26005. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.6.
feature: Categories, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-26005 : impossible de sélectionner une catégorie dans l’arborescence pour les conditions des règles de prix du panier.

Le correctif MDVA-26005 résout le problème en raison duquel les utilisateurs ne peuvent pas sélectionner une catégorie dans l’arborescence de catégories pour les conditions de la règle Prix du panier. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 est installé. L’ID de correctif est MDVA-26005. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Impossible de sélectionner une catégorie dans l’arborescence de catégories pour les conditions des règles Prix du panier.

<u>Étapes à reproduire</u> :

1. Créez ou modifiez une règle Prix du panier existante.
1. Accédez à la section Action et sélectionnez la catégorie dans Condition.
1. Effectuez le rendu de l’arborescence des catégories et essayez de choisir une catégorie.

<u>Résultats attendus</u> :

Vous pouvez sélectionner une catégorie.

<u>Résultats réels</u> :

Vous ne pouvez pas sélectionner de catégorie en raison d’une erreur JS.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
