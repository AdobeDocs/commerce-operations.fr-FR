---
title: 'ACSD-61756 : Dégradation des performances des filtres "AdvancedSalesRule" en raison d’index de base de données manquants'
description: Appliquez le correctif ACSD-61756 pour résoudre le problème Adobe Commerce en raison duquel la requête "magento_salesrule_filter" exécute une analyse complète de la table sans utiliser d’index, ce qui entraîne une dégradation des performances lors de la gestion de gros volumes d’enregistrements. Ce correctif améliore les performances en ajoutant les index de base de données manquants pour les filtres "AdvancedSalesRule".
feature: Price Rules, Price Indexer
role: Admin, Developer
source-git-commit: 42a376d1a791a17d88bea68dfef178a7b2849ce2
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-61756 : dégradation des performances des filtres `AdvancedSalesRule` en raison d’index de base de données manquants

Appliquez le correctif ACSD-61756 pour améliorer les performances des filtres `AdvancedSalesRule` en ajoutant les index de base de données manquants. Ceci corrige le problème en raison duquel la requête `magento_salesrule_filter` effectue une analyse complète de la table sans utiliser les index, ce qui entraîne une dégradation des performances lorsqu’il y a de nombreux enregistrements dans la table. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.54 est installé. L’ID de correctif est ACSD-61756. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p9

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête `magento_salesrule_filter` effectue une analyse de table complète sans utiliser d’index, ce qui entraîne une dégradation des performances des filtres `AdvancedSalesRule` lorsqu’il y a de nombreux enregistrements dans la table.

<u>Étapes à reproduire</u> :

1. Achat avec plusieurs règles de vente actives.

<u>Résultats attendus</u> :

Amélioration des performances des règles de vente.

<u>Résultats réels</u> :

La requête effectue une analyse de table complète et n’utilise pas d’index, ce qui entraîne une dégradation des performances lorsqu’il y a de nombreux enregistrements dans la table.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
