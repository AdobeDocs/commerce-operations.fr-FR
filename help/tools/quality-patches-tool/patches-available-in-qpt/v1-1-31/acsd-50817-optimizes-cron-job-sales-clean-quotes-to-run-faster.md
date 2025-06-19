---
title: 'ACSD-50817 : optimise la tâche cron sales_clean_quotes pour une exécution plus rapide'
description: Appliquez le correctif ACSD-50817 pour optimiser l’exécution plus rapide de la tâche cron « sales_clean_quotes » en ajoutant un index composite sur les colonnes « store_id » et « updated_at » dans la table des devis.
feature: Quotes
role: Admin
exl-id: b6cd412f-2f37-438b-9abc-d45de6ed54d6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-50817 : optimise les `sales_clean_quotes` de tâche cron pour une exécution plus rapide

Le correctif ACSD-50817 optimise l’exécution plus rapide de la tâche cron `sales_clean_quotes` en ajoutant un index composite sur les colonnes `store_id` et `updated_at` dans la table des guillemets. Ce correctif est disponible lorsque la version 1.1.31 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-50817.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La `sales_clean_quotes` de la tâche cron est trop lente. Avec ce correctif, son exécution a été optimisée en ajoutant un index composite sur les colonnes `store_id` et `updated_at` dans la table des guillemets.

<u>Procédure à suivre </u> :

1. Générez 50 à 80 millions de devis avec une période de `updated_at` définie comme &lt; 30 jours.
1. Exécutez la tâche cron `sales_clean_quotes` ou la requête suivante sur la table des devis :

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>Résultats attendus</u>

La tâche cron `sales_clean_quotes` est optimisée pour s’exécuter plus rapidement en ajoutant un index composite sur les colonnes `store_id` et `updated_at` dans la table des guillemets.

<u>Résultats réels</u>

La requête est trop lente.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
