---
title: "MDVA-39181 : les règles de produit connexes affichent les produits de la catégorie non définie dans la règle"
description: Le correctif MDVA-39181 résout le problème en raison duquel les règles de produit associées affichent les produits d’une catégorie non définie dans la règle. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 est installé. L’ID de correctif est MDVA-39181. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Categories, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-39181 : les règles de produit connexes affichent les produits de la catégorie non définis dans la règle.

Le correctif MDVA-39181 résout le problème en raison duquel les règles de produit associées affichent les produits d’une catégorie non définie dans la règle. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 est installé. L’ID de correctif est MDVA-39181. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les règles de produit connexes affichent les produits des catégories qui ne sont pas définies dans la règle.

<u>Conditions préalables</u> :

Installez des exemples de données.

<u>Étapes à reproduire</u> :

1. Créez une marque d’attribut et ajoutez-la au **Top Attribute Set**.
1. Sélectionnez les vestes **Josie**, **Augusta** et **Ingrid** à ajouter à la marque à partir de **Women** > **Tops** > **Jackets category**.
1. Sélectionnez les vestes **Beaumont**, **Hyperion** et **Kenobi** à ajouter à la marque à partir de **Men** > **Tops** > **Jacket category**.
1. Créez un produit associé avec :

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * Produits à faire correspondre :

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * Produits à afficher :

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. Ouvrez la SKU WJ04 à partir du front-end et vérifiez les produits associés.
1. Mettez à jour l’ID de catégorie de **Women** > **Tops** > **Jackets** au cas où il serait différent de celui-ci.

<u>Résultats attendus</u> :

Seuls les produits de la même marque et de la même catégorie enfant sont affichés dans les produits associés.

<u>Résultats réels</u> :

Les produits associés sont affichés pour la même marque mais à partir d’une catégorie parente aléatoire.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
