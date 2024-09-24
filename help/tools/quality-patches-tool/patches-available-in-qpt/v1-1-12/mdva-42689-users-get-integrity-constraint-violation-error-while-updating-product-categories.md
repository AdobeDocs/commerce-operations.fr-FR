---
title: 'MDVA-42689 : les utilisateurs reçoivent une erreur de violation de contrainte d’intégrité lors de la mise à jour des catégories de produits lors de l’importation'
description: Le correctif MDVA-42689 résout le problème de non-respect des contraintes d’intégrité des utilisateurs lors de la mise à jour des catégories de produits lors de l’importation. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-42689. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-42689 : les utilisateurs reçoivent une erreur de violation de contrainte d’intégrité lors de la mise à jour des catégories de produits lors de l’importation

Le correctif MDVA-42689 résout le problème de non-respect des contraintes d’intégrité des utilisateurs lors de la mise à jour des catégories de produits lors de l’importation. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-42689. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Adobe Commerce renvoie une erreur de violation de contrainte d’intégrité lors de la mise à jour des catégories de produits lors de l’importation.

<u>Étapes à reproduire</u> :

1. Configurez deux sites web.
1. Créez des sous-catégories sous la catégorie racine jusqu’à deux niveaux sur la page de catégorie. Par exemple, Catégorie racine > **Gear** > **Watches**.
1. Créez deux produits simples et affectez les deux produits à la même catégorie **Gear** > **Watches** .
1. Attribuez un produit simple aux deux sites web.
1. Enregistrez le produit.
1. Préparez un fichier CSV à importer. Il doit y avoir deux enregistrements de produit avec des vues de magasin différentes. L’un des produits doit appartenir à ces deux vues de magasin.
1. Importez maintenant le fichier CSV en accédant à **Système** > **Importer** > **Type d’entité** (Produits).

<u>Résultats attendus</u> :

Le fichier CSV est importé sans erreur.

<u>Résultats réels</u> :

Adobe Commerce renvoie l’erreur suivante :

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
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
