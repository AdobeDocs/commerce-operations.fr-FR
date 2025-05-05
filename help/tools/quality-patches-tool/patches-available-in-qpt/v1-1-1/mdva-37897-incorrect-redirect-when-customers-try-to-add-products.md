---
title: 'MDVA-37897 : Redirection incorrecte lors de l’ajout de produits de Récemment consultés'
description: Le correctif MDVA-37897 résout le problème de redirection incorrecte lorsque les utilisateurs tentent d’ajouter des produits avec des options à partir du widget Récemment consulté. Ce correctif est disponible lorsque [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1 est installé. L’ID de correctif est MDVA-37897. Veuillez noter que ce problème devrait être résolu dans la version 2.4.4 de Adobe Commerce.
feature: Products
role: Admin
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37897 : redirection incorrecte lors de l’ajout de produits de Récemment consultés

Le correctif MDVA-37897 résout le problème de redirection incorrecte lorsque les utilisateurs tentent d’ajouter des produits avec des options à partir du widget Récemment consulté. Ce correctif est disponible lorsque l’outil [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1 est installé. L’ID de correctif est MDVA-37897. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur notre infrastructure cloud 2.4.1

**Compatible avec les versions Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil Correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le `magento/quality-patches` package vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool]page](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) : Search des correctifs. Utilisez l’identifiant du correctif comme mot-clé de recherche pour localiser le correctif.

## Émettre

Lorsqu’un utilisateur tente d’ajouter un produit à partir de la section Récemment consultés qui a des options obligatoires à sélectionner, l’utilisateur est redirigé vers la page de liste de produits au lieu de la page de détails du produit.

<u>Étapes à reproduire</u> :

1. Créez un produit simple avec des options personnalisables (Type : bouton radio).
1. Configurez le widget Récemment consultés pour afficher les produits.
1. Visitez les produits qui disposent d’options personnalisables afin qu’ils s’affichent dans le widget Récemment consultés .
1. Cliquez sur **Ajouter au panier** sur l’un des produits du widget Récemment consultés.

<u>Résultats</u> attendus :

Vous êtes redirigé vers la page de détails du produit pour choisir les options.

<u>Résultats</u> réels :

Vous êtes redirigé vers la page des produits.

## Appliquez le patch

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce on-premise : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur notre infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Correctifs de qualité dans le [!DNL Quality Patches Tool] guide.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section Correctifs disponibles dans QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
