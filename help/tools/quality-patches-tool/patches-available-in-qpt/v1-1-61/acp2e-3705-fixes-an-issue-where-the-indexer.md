---
title: 'ACP2E-3705 : l’exécution cron « indexer_update_all_views » échoue lorsque « MAGE_INDEXER_THREADS_COUNT » est défini'
description: Appliquez le correctif ACP2E-3705 pour résoudre le problème d’Adobe Commerce en raison duquel l’exécution cron « indexer_update_all_views » échoue lorsque « MAGE_INDEXER_THREADS_COUNT » est défini.
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: 111325fa-8ed5-45f9-9e68-b52f4425d253
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACP2E-3705 : `indexer_update_all_views`’exécution cron échoue lorsque `MAGE_INDEXER_THREADS_COUNT` est définie

>[!NOTE]
>
>Ce correctif remplace le [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md) pour les versions 2.4.7 et ultérieures.

Le correctif ACP2E-3705 corrige le problème en raison duquel l’exécution de la commande cron `indexer_update_all_views` échoue lorsque la `MAGE_INDEXER_THREADS_COUNT` est définie. Ce correctif est disponible lorsque la version 1.1.61 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACP2E-3705. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’exécution de la commande cron `indexer_update_all_views` échoue lorsque la `MAGE_INDEXER_THREADS_COUNT` est définie sur une valeur supérieure à *2*, ce qui affecte spécifiquement l’indexeur [!UICONTROL Customer Segments] avec B2B activé.

<u>Procédure à suivre </u> :

1. Appliquez le correctif QPT [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md).
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Category permissions]**.
1. Activez **[!UICONTROL Category Permissions]**.
1. Définissez les indexeurs suivants sur le mode **[!UICONTROL Update on Schedule]** :

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Créez quelques produits et affectez-les à une catégorie.
1. Exécutez une réindexation complète.
1. Accédez à une catégorie et définissez des **[!UICONTROL Category Permissions]**.
1. Exécutez `indexer_update_all_views` tâche cron avec `MAGE_INDEXER_THREADS_COUNT` définie sur *8*.

<u>Résultats attendus</u> :

La réindexation s’est terminée sans erreur.

<u>Résultats réels</u> :

La tâche cron `indexer_update_all_views` rencontre l’erreur suivante :

```
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : mises à niveau et correctifs > Appliquer des correctifs dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
