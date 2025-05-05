---
title: 'ACSD-50817 : optimise la tâche cron sales_clean_citations pour une exécution plus rapide.'
description: Appliquez le correctif ACSD-50817 afin d’optimiser la tâche cron &grave;sales_clean_quotes&grave; pour s’exécuter plus rapidement en ajoutant un index composite sur les colonnes &grave;store_id&grave; et &grave;updated_at&grave; dans la table des guillemets.
feature: Quotes
role: Admin
exl-id: b6cd412f-2f37-438b-9abc-d45de6ed54d6
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-50817 : optimise la tâche cron `sales_clean_quotes` pour une exécution plus rapide.

Le correctif ACSD-50817 optimise l’exécution plus rapide de la tâche cron `sales_clean_quotes` en ajoutant un index composite sur les colonnes `store_id` et `updated_at` dans la table des guillemets. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.31 est installé. L’ID de correctif est ACSD-50817.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La tâche cron `sales_clean_quotes` est trop lente. Avec ce correctif, il a été optimisé pour s’exécuter plus rapidement en ajoutant un index composite sur les colonnes `store_id` et `updated_at` dans la table des guillemets.

<u>Étapes à reproduire</u> :

1. Générez 50 à 80 millions de guillemets dont `updated_at` est défini sur une période de &lt; 30 jours.
1. Exécutez la tâche cron `sales_clean_quotes` ou la requête suivante sur la table des guillemets :

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>Résultats attendus</u>

La tâche Cron `sales_clean_quotes` est optimisée pour s’exécuter plus rapidement en ajoutant un index composite sur les colonnes `store_id` et `updated_at` dans la table des guillemets.

<u>Résultats réels</u>

La requête est trop lente.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
