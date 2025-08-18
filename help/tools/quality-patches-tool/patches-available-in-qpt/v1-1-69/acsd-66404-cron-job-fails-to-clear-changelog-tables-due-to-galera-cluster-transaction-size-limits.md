---
title: 'ACSD-66404 : la tâche Cron ne parvient pas à effacer les tables de journal des modifications en raison  [!DNL Galera Cluster]  limites de taille des transactions'
description: Appliquez le correctif ACSD-66404 pour résoudre le problème d'Adobe Commerce où la tâche cron ne supprime pas les tables de logs des modifications et provoque des problèmes en cas  [!DNL Galera Cluster]  grande quantité de données dans ces tables.
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 42bd5934782ca65b891a36f61102083356c92e59
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ACSD-66404 : la tâche Cron ne parvient pas à effacer les tables de journal des modifications en raison des limites de taille de transaction [!DNL Galera Cluster]

Le correctif ACSD-66404 corrige le problème en raison duquel la tâche cron ne parvient pas à effacer les tables de journal des modifications, ce qui entraîne des problèmes de [!DNL Galera Cluster] lors de la gestion de grandes quantités de données. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66404. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p6, 2.4.7-p6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La tâche cron n&#39;efface pas les tables du journal des modifications et entraîne des problèmes de [!DNL Galera Cluster] en cas de grande quantité de données dans ces tables.

<u>Procédure à suivre </u> :

1. Générez de nombreux produits à l’aide de profils de performances.
1. Effectuez une mise à jour en bloc pour tous les produits du système. Il y a donc beaucoup d&#39;entrées dans `inventory_cl` table DB.
1. Exécutez la tâche cron `indexer_clean_all_changelogs`.

<u>Résultats attendus</u> :

La tâche cron `indexer_clean_all_changelogs` peut effectuer un nettoyage du journal des modifications sur un journal des modifications volumineux (10 Go ou plus) dans plusieurs requêtes de suppression, sans causer de problèmes de [!DNL Galera Cluster].

<u>Résultats réels</u> :

La tâche cron `indexer_clean_all_changelogs` effectue un nettoyage du journal des modifications sur un journal des modifications volumineux (10 Go ou plus) dans une seule requête de suppression, ce qui entraîne des problèmes de [!DNL Galera Cluster].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [ Mises à niveau et correctifs > Appliquer des correctifs ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
