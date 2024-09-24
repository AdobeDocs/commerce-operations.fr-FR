---
title: 'MDVA-43232 : Le tri des produits dans le marchandisage visuel par Prix spécial au plus haut (ou au bas) provoque une erreur'
description: Le correctif MDVA-43232 corrige le problème en raison duquel le tri des produits dans le marchandiseur visuel par Prix spécial au haut (ou au bas) provoquait une erreur lors de l’enregistrement de la catégorie. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-43232. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-43232 : Le tri des produits dans le marchandisage visuel par Prix spécial au haut (ou au bas) provoque une erreur.

Le correctif MDVA-43232 corrige le problème en raison duquel le tri des produits dans le marchandiseur visuel par Prix spécial au haut (ou au bas) provoquait une erreur lors de l’enregistrement de la catégorie. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-43232. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le tri des produits dans le marchandiseur visuel par Prix spécial au plus haut (ou au bas) entraîne une erreur lors de l’enregistrement de la catégorie.

<u>Étapes à reproduire</u> :

1. Assurez-vous qu&#39;il y a deux sites web.
1. Accédez à **Magasins** > **Configuration** > **Catalogue** > **Prix** et définissez Portée du prix du catalogue = Site Web.
1. Encore une fois, accédez à **Magasins** > **Configuration** > **Catalogue** > **Marchandisage visuel** > **Attributs visibles pour les règles de catégorie** > et ajoutez Prix spécial.
1. Créez un produit simple et affectez-lui les deux sites web.
1. Ajoutez un prix spécial à la portée par défaut du produit.
1. Basculez vers la portée de l’autre magasin et remplacez le Prix et le Prix spécial de ce produit.
1. Effectuez une réindexation `catalog_product_price`.
1. Accédez à **Catalogue** > **Catégories** et créez une nouvelle catégorie.
1. Ajoutez une règle de catégorie pour filtrer les produits à prix spécial.
1. Enregistrez la catégorie.
1. Dans la section Produits de la catégorie, définissez Ordre de tri = Prix spécial sur le haut (ou le bas).
1. Enregistrez à nouveau la catégorie.

<u>Résultats attendus</u> :

La catégorie est enregistrée sans erreur.

<u>Résultats réels</u> :

Une exception est générée :

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
