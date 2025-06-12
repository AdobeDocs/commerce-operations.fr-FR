---
title: 'MDVA-43601 : les triggers sont supprimés de la table « catalogrule_product_price » après une réindexation complète'
description: Le correctif MDVA-43601 corrige le problème où les déclencheurs sont supprimés de la table « catalogrule_product_price » après une réindexation complète de « catalogrule_rule » ou « catalogrule_product ». Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-43601. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Catalog Management, Orders, Products
role: Admin
exl-id: b9580806-ac35-4c86-8eee-c9f16d654171
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-43601 : les triggers sont supprimés de la table « catalogrule_product_price » après une réindexation complète

Le correctif MDVA-43601 corrige le problème où les déclencheurs sont supprimés `catalogrule_product_price` tableau après une réindexation complète de `catalogrule_rule` ou `catalogrule_product`. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-43601. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les Triggers sont supprimés `catalogrule_product_price` tableau après une réindexation complète de `catalogrule_rule` ou `catalogrule_product`.

<u>Procédure à suivre </u> :

1. Définissez tous les indexeurs sur *Mettre à jour selon le calendrier*.
1. Vérifiez les déclencheurs créés pour `catalogrule_product_price` table en exécutant la requête SQL suivante :

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Réindexez manuellement `catalogrule_rule` ou `catalogrule_product` en exécutant la commande suivante : `bin/magento indexer:reindex catalogrule_rule`
1. Vérifiez à nouveau les déclencheurs `catalogrule_product_price` tableau.

<u>Résultats attendus</u> :

Les Triggers `catalogrule_product_price` tableau sont conservés après une réindexation complète.

<u>Résultats réels</u> :

Aucun déclencheur trouvé pour `catalogrule_product_price` table.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
