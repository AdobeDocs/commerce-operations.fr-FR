---
title: 'MDVA-40488 : produits configurables avec des produits enfants en rupture de stock non affichés dans la plage de prix correcte'
description: Le correctif MDVA-40488 résout le problème où les produits configurables avec des produits enfants en rupture de stock ne s'affichent pas dans leur plage de prix correcte. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID du correctif est MDVA-40488. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Configuration, Orders, Products
role: Admin
exl-id: 9a843d1b-88df-4bd7-a358-3aa34c436bdf
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# MDVA-40488 : produits configurables avec des produits enfants en rupture de stock non affichés dans la plage de prix correcte

Le correctif MDVA-40488 résout le problème où les produits configurables avec des produits enfants en rupture de stock ne s&#39;affichent pas dans leur plage de prix correcte. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID du correctif est MDVA-40488. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits configurables avec des produits enfants en rupture de stock ne sont pas affichés dans leur plage de prix correcte.

<u>Conditions préalables</u> :

Accédez à Commerce Admin > **stores** > **configuration** > **catalogue** > **Inventaire** > **options de stock** et définissez **Afficher les produits en rupture de stock** sur *Oui*.

<u>Procédure à suivre </u> :

1. Créez un produit configurable avec deux produits associés. Par exemple : produits simples rouge et brun.
1. Définissez l&#39;inventaire du produit simple sur Rouge, puis définissez le Statut du stock sur *En stock*, puis définissez le statut Activer le produit sur *Non*.
1. Définissez l&#39;inventaire du produit simple Brown, puis définissez le statut Activer le produit sur *Oui*.
1. Assurez-vous que le statut de stock du produit configurable est *En stock*.
1. Remplacez l’inventaire du produit simple Brown par 0 et définissez l’État du stock sur *En rupture de stock*.
1. À ce stade, le statut du stock de produit configurable est toujours *En stock*.
1. Effectuez la réindexation.
1. Vérifiez les `min_price` et `max_price` du produit configurable dans la table de base de données `catalog_product_index_price` ; les deux valeurs sont définies sur 0.
1. Mais si nous définissons l’état du stock du produit configurable sur *En rupture de stock* et effectuons une réindexation, nous pouvons voir des `min_price` non nulles et des valeurs `max_price` du produit configurable.

<u>Résultats attendus</u> :

Si tous les produits enfants sont *en rupture de stock* et que le produit configurable lui-même est également *en rupture de stock*, le prix est calculé en utilisant tous les produits enfants.

<u>Résultats réels</u> :

Les valeurs `min_price` et `max_price` pour le produit configurable dans la table de base de données `catalog_product_index_price` sont définies sur 0 lorsque le statut du stock configurable est *En stock*, mais s&#39;il est *En rupture de stock* elles deviennent des valeurs non nulles.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
