---
title: 'MDVA-40550 : Produits manquants sur le front-end après réindexation'
description: Le correctif MDVA-40550 résout le problème en raison duquel la réindexation entraîne l’absence de certains ou de tous les produits des catégories storefront. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID de correctif est MDVA-40550. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: Categories, Console, Products
role: Admin
exl-id: 5ce7e341-e165-4668-9de7-8e9ca3a70c70
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40550 : Produits manquants sur le front-end après réindexation

Le correctif MDVA-40550 résout le problème en raison duquel la réindexation entraîne l’absence de certains ou de tous les produits des catégories storefront. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID de correctif est MDVA-40550. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u> :

1. Créez un produit.
1. Basculez les indexeurs vers **Mise à jour par planning**.
   * Attribuez le produit à une catégorie.
1. Activez xdebug et effectuez le point d’arrêt xdebug dans `\Magento\Indexer\Model\Indexer::reindexAll` et `\Magento\Indexer\Model\IndexMutex::execute`.
1. Exécutez une **réindexation complète** de `catalog_category_product` avec la commande :

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * Attendez que l’exécution s’arrête sur le point d’arrêt `\Magento\Indexer\Model\Indexer::reindexAll`.

1. Dans une autre console, exécutez une **réindexation partielle** en parallèle avec la commande :

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Attendez que l’exécution s’arrête sur le point d’arrêt `\Magento\Indexer\Model\IndexMutex::execute`. Il verrouillera l’indexeur `catalog_category_product`.
1. Reprenez l’exécution de la réindexation complète de `catalog_category_product` et attendez un délai d’expiration du verrouillage (60 secondes).

<u>Résultats attendus</u> :

Aucun message d’erreur dans la console.

<u>Résultats réels</u> :

Vous obtenez l’erreur suivante :

*Impossible d’acquérir le verrou pour l’index : catalog_category_product.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
