---
title: 'MDVA-39181 : les règles de produits associés affichent les produits de la catégorie non définie dans la règle'
description: Le correctif MDVA-39181 résout le problème où les règles de produit associées affichent des produits d’une catégorie non définie dans la règle. Ce correctif est disponible lorsque l’[Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 est installé. L’ID du correctif est MDVA-39181. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Categories, Products
role: Admin
exl-id: 98f65b7d-2cb3-49ff-95ef-c23a922e49f2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-39181 : les règles de produits associés affichent les produits de la catégorie non définie dans la règle

Le correctif MDVA-39181 résout le problème où les règles de produit associées affichent des produits d’une catégorie non définie dans la règle. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 est installé. L’ID du correctif est MDVA-39181. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les règles de produits associés affichent les produits des catégories non définies dans la règle.

<u>Conditions préalables</u> :

Installez des données d’exemple.

<u>Procédure à suivre </u> :

1. Créez une marque d’attribut et ajoutez-la au **Jeu d’attributs le plus élevé**.
1. Choisissez les vestes **Josie**, **Augusta** et **Ingrid** à ajouter à Brand Kitty depuis **Women** > **Tops** > **Jackets category**.
1. Choisissez les vestes **Beaumont**, **Hyperion** et **Kenobi** à ajouter à la marque Kitty depuis **Men** > **Tops** > **Jacket category**.
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

1. Ouvrez le SKU WJ04 à partir du front-end et vérifiez les produits associés.
1. Mettez à jour l’ID de catégorie de **Femmes** > **Tops** > **Vestes** au cas où il serait différent de celui-ci.

<u>Résultats attendus</u> :

Seuls les produits de la même marque et de la même catégorie enfant s’affichent dans les produits associés.

<u>Résultats réels</u> :

Les produits associés sont affichés de la même marque mais d’une catégorie parent aléatoire.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
