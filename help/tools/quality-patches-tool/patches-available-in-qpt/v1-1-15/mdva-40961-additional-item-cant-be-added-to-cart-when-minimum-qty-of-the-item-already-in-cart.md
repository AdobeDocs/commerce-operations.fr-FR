---
title: 'MDVA-40961 : impossible d''ajouter un article supplémentaire au panier lorsque la quantité minimale de l''article est déjà dans le panier'
description: Le correctif MDVA-40961 corrige le problème en raison duquel un article supplémentaire ne peut pas être ajouté au panier lorsque la quantité minimale de l’article est déjà dans le panier. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15 est installé. L’ID du correctif est MDVA-40961. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Orders, Shopping Cart
role: Admin
exl-id: b5191919-062d-4ddd-84e2-a4801501724d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-40961 : impossible d&#39;ajouter un article supplémentaire au panier lorsque la quantité minimale de l&#39;article est déjà dans le panier

Le correctif MDVA-40961 corrige le problème en raison duquel un article supplémentaire ne peut pas être ajouté au panier lorsque la quantité minimale de l’article est déjà dans le panier. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15 est installé. L’ID du correctif est MDVA-40961. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un article supplémentaire ne peut pas être ajouté au panier lorsque la quantité minimale de l’article est déjà dans le panier.

<u>Procédure à suivre </u> :

1. Définissez un produit simple pour qu’il ait plus d’un **Quantité minimale autorisée dans le panier** (par exemple, deux).
1. Ouvrez le produit sur la vitrine et ajoutez-en deux au panier.
1. Restez sur la page du produit et ajoutez un autre de ces produits au panier.

<u>Résultats attendus</u> :

Le troisième produit peut être ajouté au panier, car il contient déjà la quantité minimale.

<u>Résultats réels</u> :

Vous obtenez le message d’erreur suivant : *Le moins que vous puissiez acheter est 2*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
