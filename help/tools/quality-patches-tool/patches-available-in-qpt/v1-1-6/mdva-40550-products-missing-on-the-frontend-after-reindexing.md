---
title: 'MDVA-40550 : produits manquants sur le serveur frontal après la réindexation'
description: Le correctif MDVA-40550 résout le problème où la réindexation entraîne la perte de certains produits ou de tous les produits des catégories de storefront. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID du correctif est MDVA-40550. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Categories, Console, Products
role: Admin
exl-id: 5ce7e341-e165-4668-9de7-8e9ca3a70c70
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40550 : produits manquants sur le serveur frontal après la réindexation

Le correctif MDVA-40550 résout le problème où la réindexation entraîne la perte de certains produits ou de tous les produits des catégories de storefront. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID du correctif est MDVA-40550. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Procédure à suivre </u> :

1. Créez un produit.
1. Basculez les indexeurs sur **Mettre à jour selon le planning**.
   * Affectez le produit à une catégorie.
1. Activez xdebug et faites de xdebug un point d’arrêt dans `\Magento\Indexer\Model\Indexer::reindexAll` et `\Magento\Indexer\Model\IndexMutex::execute`.
1. Exécutez une **réindexation complète** de `catalog_category_product` avec la commande :

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * Attendez que l’exécution s’arrête au point d’arrêt `\Magento\Indexer\Model\Indexer::reindexAll`.

1. Dans une autre console, exécutez une **réindexation partielle** en parallèle avec la commande :

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Attendez que l’exécution s’arrête au point d’arrêt `\Magento\Indexer\Model\IndexMutex::execute`. Cela verrouille l’indexeur de `catalog_category_product`.
1. Reprenez l’exécution de la réindexation complète de `catalog_category_product` et attendez la fin du délai de verrouillage (60 secondes).

<u>Résultats attendus</u> :

Aucun message d’erreur dans la console.

<u>Résultats réels</u> :

Vous obtenez l’erreur suivante :

*Impossible d’acquérir le verrou de l’index : catalog_category_product.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
