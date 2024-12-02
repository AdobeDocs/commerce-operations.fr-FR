---
title: 'MDVA-43601 : les déclencheurs sont supprimés de la table "catalogrule_product_price" après la réindexation complète'
description: Le correctif MDVA-43601 corrige le problème en raison duquel les déclencheurs sont supprimés de la table "catalogrule_product_price" après une réindexation complète de "catalogrule_rule" ou "catalogrule_product". Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID de correctif est MDVA-43601. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Catalog Management, Orders, Products
role: Admin
exl-id: b9580806-ac35-4c86-8eee-c9f16d654171
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-43601 : les déclencheurs sont supprimés de la table &quot;catalogrule_product_price&quot; après la réindexation complète

Le correctif MDVA-43601 corrige le problème en raison duquel les déclencheurs sont supprimés de la table `catalogrule_product_price` après une réindexation complète de `catalogrule_rule` ou `catalogrule_product`. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID de correctif est MDVA-43601. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les déclencheurs sont supprimés de la table `catalogrule_product_price` après une réindexation complète de `catalogrule_rule` ou `catalogrule_product`.

<u>Étapes à reproduire</u> :

1. Définissez tous les indexeurs sur *Mettre à jour par planification*.
1. Vérifiez les déclencheurs créés pour la table `catalogrule_product_price` en exécutant la requête SQL suivante :

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Réindexez manuellement `catalogrule_rule` ou `catalogrule_product` en exécutant la commande suivante : `bin/magento indexer:reindex catalogrule_rule`
1. Vérifiez à nouveau les déclencheurs de la table `catalogrule_product_price`.

<u>Résultats attendus</u> :

Les déclencheurs de la table `catalogrule_product_price` sont conservés après une réindexation complète.

<u>Résultats réels</u> :

Aucun déclencheur n&#39;est trouvé pour la table `catalogrule_product_price`.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
