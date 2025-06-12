---
title: 'MDVA-37897 : redirection incorrecte lors de l’ajout de produits provenant de la section Récemment consultés'
description: Le correctif MDVA-37897 résout le problème de redirection incorrecte lorsque les utilisateurs et utilisatrices tentent d’ajouter des produits avec des options du widget Récemment consultés . Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1 est installé. L’ID du correctif est MDVA-37897. Notez que le problème est planifié pour être corrigé dans la version 2.4.4 d’Adobe Commerce.
feature: Products
role: Admin
exl-id: d4d1d735-38e4-455e-9045-a2443ce33851
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37897 : redirection incorrecte lors de l’ajout de produits provenant de la section Récemment consultés

Le correctif MDVA-37897 résout le problème de redirection incorrecte lorsque les utilisateurs et utilisatrices tentent d’ajouter des produits avec des options du widget Récemment consultés . Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1 est installé. L’ID du correctif est MDVA-37897. Notez que le problème est planifié pour être corrigé dans la version 2.4.4 d’Adobe Commerce.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur notre infrastructure cloud 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsqu’un utilisateur ou une utilisatrice tente d’ajouter un produit à partir de la section Récemment consultés qui comporte des options qui doivent être sélectionnées, la personne est redirigée vers la page de liste des produits au lieu de la page des détails du produit.

<u>Procédure à suivre </u> :

1. Créez un produit simple avec des options personnalisables (type : bouton radio).
1. Configurez le widget Récemment consultés pour afficher les produits.
1. Accédez aux produits qui comportent des options personnalisables afin qu’ils s’affichent dans le widget Récemment consultés.
1. Cliquez sur **Ajouter au panier** sur l’un des produits du widget Récemment consultés.

<u>Résultats attendus</u> :

Vous êtes redirigé vers la page des détails du produit pour choisir les options.

<u>Résultats réels</u> :

Vous êtes redirigé vers la page de liste des produits.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce on-premise : [Guide de mise à jour logicielle > Application de correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur notre infrastructure cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs et développeuses.

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
