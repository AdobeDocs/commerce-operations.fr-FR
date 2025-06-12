---
title: 'MDVA-43232 : le tri des produits dans le marchandiseur visuel par Prix spécial en haut (ou en bas) provoque une erreur'
description: Le correctif MDVA-43232 corrige le problème en raison duquel le tri des produits dans le marchandiseur visuel par Prix spécial en haut (ou en bas) provoque une erreur lors de l’enregistrement de la catégorie. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-43232. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
exl-id: c977bec8-f99c-4799-abce-26aad49b77e8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-43232 : le tri des produits dans le marchandiseur visuel par Prix spécial en haut (ou en bas) provoque une erreur

Le correctif MDVA-43232 corrige le problème en raison duquel le tri des produits dans le marchandiseur visuel par Prix spécial en haut (ou en bas) provoque une erreur lors de l’enregistrement de la catégorie. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-43232. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le tri des produits dans le marchandiseur visuel par Prix spécial en haut (ou en bas) provoque une erreur lors de l’enregistrement de la catégorie.

<u>Procédure à suivre </u> :

1. Assurez-vous qu’il existe deux sites web.
1. Accédez à **Magasins** > **Configuration** > **Catalogue** > **Prix** et définissez la Portée du prix du catalogue = Site Web.
1. Accédez à nouveau à **Magasins** > **Configuration** > **Catalogue** > **Marchandiseur visuel** > **Attributs visibles pour les règles de catégorie** > et ajoutez un prix spécial.
1. Créez un produit simple et affectez les produits aux deux sites web.
1. Ajoutez un prix spécial à la portée par défaut du produit.
1. Basculez vers la portée de l’autre magasin et remplacez le Prix et le Prix spécial de ce produit.
1. Effectuez une réindexation `catalog_product_price`.
1. Accédez à **Catalogue** > **Catégories** et créez une catégorie.
1. Ajoutez une règle de catégorie pour filtrer les produits ayant un prix spécial.
1. Enregistrez la catégorie.
1. Dans la section Produits dans la catégorie , définissez Ordre de tri = Prix spécial en haut (ou en bas).
1. Enregistrez à nouveau la catégorie.

<u>Résultats attendus</u> :

La catégorie est enregistrée sans erreur.

<u>Résultats réels</u> :

Une exception est générée :

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
