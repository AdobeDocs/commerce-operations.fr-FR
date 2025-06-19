---
title: 'ACSD-64112 : l’exécution cron « indexer_update_all_views » échoue lorsque « MAGE_INDEXER_THREADS_COUNT » est défini'
description: Appliquez le correctif ACSD-64112 pour résoudre le problème d’Adobe Commerce en raison duquel l’exécution cron « indexer_update_all_views » échoue lorsque « MAGE_INDEXER_THREADS_COUNT » est défini.
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: c95f179d-5291-481f-b655-08a9db608513
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-64112 : l’exécution de `indexer_update_all_views` cron échoue lorsque `MAGE_INDEXER_THREADS_COUNT` est défini

>[!NOTE]
>
>Ce correctif a été remplacé par [ACP2E-3705](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3705-fixes-an-issue-where-the-indexer.md) pour les versions d’Adobe Commerce supérieures à la version 2.4.7.

Le correctif ACSD-64112 corrige le problème d’échec de l’exécution du cron `indexer_update_all_views` lorsque `MAGE_INDEXER_THREADS_COUNT` est défini. Ce correctif est disponible lorsque la version 1.1.59 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64112. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p10

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p10

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’exécution de la commande cron `indexer_update_all_views` échoue lorsque la `MAGE_INDEXER_THREADS_COUNT` est définie sur une valeur supérieure à 2, ce qui affecte spécifiquement l’indexeur [!UICONTROL Customer Segments] avec B2B activé.

<u>Procédure à suivre </u> :

1. Installez une instance propre avec B2B.
1. Activez **[!UICONTROL B2B Company]** et **[!UICONTROL Shared Catalog]**.
1. Créez une catégorie.
1. Créez quelques produits et affectez-les à la catégorie .
1. Exécutez une réindexation complète.
1. Définissez les indexeurs suivants sur **[!UICONTROL Update on Schedule]** :

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Accédez au serveur principal et chargez la catégorie que vous venez de créer.
1. Cliquez sur **[!UICONTROL Category Permissions]** et créez un **[!UICONTROL New Permission]** pour un groupe de clients existant.
1. Assurez-vous que l’indexeur `catalogpermissions_category` a une liste d’attente. Exécutez la commande suivante pour le vérifier :

   ```
   bin/magento indexer:status
   ```

1. Définissez le nombre de threads de l’indexeur suivant dans `env.php` :

   ```php
   'MAGE_INDEXER_THREADS_COUNT' => 8
   ```

1. Exécutez la tâche cron :

   ```
   bin/magento cron:run
   ```

<u>Résultats attendus</u> :

La tâche cron doit s’exécuter sans problème.

<u>Résultats réels</u> :

La tâche cron `indexer_update_all_views` rencontre l’erreur suivante :

```
report.CRITICAL: PDOException: There is no active transaction in /home/vendor/magento/zend-db/library/Zend/Db/Adapter/Pdo/Abstract.php:326
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Étapes supplémentaires requises après l’installation du correctif

(Cette section est facultative ; certaines étapes peuvent être nécessaires après l’application du correctif pour résoudre le problème.) 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
