---
title: "MDVA-40961 : un article supplémentaire ne peut pas être ajouté au panier lorsque la quantité minimale d’article est déjà dans le panier"
description: Le correctif MDVA-40961 corrige le problème lorsqu’un article supplémentaire ne peut pas être ajouté au panier alors que la quantité minimale de l’article est déjà dans le panier. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 est installé. L’ID de correctif est MDVA-40961. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-40961 : Un article supplémentaire ne peut pas être ajouté au panier lorsque la quantité minimale d’article est déjà dans le panier.

Le correctif MDVA-40961 corrige le problème lorsqu’un article supplémentaire ne peut pas être ajouté au panier alors que la quantité minimale de l’article est déjà dans le panier. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 est installé. L’ID de correctif est MDVA-40961. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un article supplémentaire ne peut pas être ajouté au panier lorsque la quantité minimale de l’article est déjà dans le panier.

<u>Étapes à reproduire</u> :

1. Définissez un produit simple pour qu’il ait plus d’une **quantité minimale autorisée dans le panier** (par exemple, deux).
1. Ouvrez le produit sur Storefront et ajoutez-en deux au panier.
1. Restez sur la page des produits et ajoutez un autre de ce produit au panier.

<u>Résultats attendus</u> :

Le troisième produit peut être ajouté au panier, car il contient déjà le montant minimum.

<u>Résultats réels</u> :

Vous recevez le message d’erreur suivant : *Le moins élevé que vous puissiez acheter est 2*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].