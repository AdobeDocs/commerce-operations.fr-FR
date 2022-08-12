---
title: '"Le [!UICONTROL Cron] tab"'
description: En savoir plus sur les [!UICONTROL Cron] de [!DNL Observation for Adobe Commerce].
source-git-commit: 3c1e50b3bff1bd2b2760e2e763173275161b0044
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# Le [!UICONTROL Cron] tab

Cet onglet permet d’isoler rapidement les problèmes et les causes des problèmes cron.

## [!UICONTROL Cron transaction duration in seconds]

![Durée de transaction du cron en secondes](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

Le **[!UICONTROL Cron transaction duration in seconds]** frame affiche la durée des transactions des crons en secondes. Cela affichera les transactions qui ont de longs exécutions. Un examen plus approfondi du modèle de gestion des actifs numériques (APM) donnera plus de détails sur la requête que la transaction/opération peut exécuter.

## [!UICONTROL MySql Non-Sleeping Threads by Node]

![Threads non dormantes MySql par noeud](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

Le **[!UICONTROL MySql Non-Sleeping Threads by Node]** Le cadre affiche les threads MySql Non-Sleeping par noeud pendant la période sélectionnée.

## [!UICONTROL SQL Trace count by path]

![Nombre de traces SQL par chemin](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

Le **[!UICONTROL SQL Trace count by path]** frame examine le nombre de traces MySql par chemin, ce qui peut aider à suivre les instructions SQL pendant une période sélectionnée.

## [!UICONTROL Cron database call]

![Appel de base de données Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

Le **[!UICONTROL Cron database call]** frame examine le nombre de crons appelant à la base de données au cours d’une période sélectionnée.

## [!UICONTROL Cron schedule table locks]

![Verrouillements du tableau de planification cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

Le **[!UICONTROL Cron schedule table locks]** frame examine le verrouillage du tableau de planification cron sur une période sélectionnée.

## [!UICONTROL Cron schedule clean cron fired]

![Verrouillements du tableau de planification cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

Le **[!UICONTROL Cron schedule clean cron fired]** frame examine le nombre de crons nettoyés au cours d’une période sélectionnée. Si aucune donnée n’est affichée dans ce cadre, cela peut indiquer un problème de fonctionnement correct des crons. Si le planning de la tâche cron n’est pas nettoyé, les crons ne s’exécuteront pas de manière optimale et peuvent prendre plus de temps à s’exécuter.

## [!UICONTROL Cron schedule clean records details table]

![Tableau des détails des enregistrements de nettoyage du planning cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

Le **[!UICONTROL Cron schedule clean records details table]** fournit des détails sur la tâche de nettoyage des enregistrements de la `cron_schedule` tableau pendant une période sélectionnée.

## [!UICONTROL cron_schedule table updates]

![Mises à jour de la table cron_schedule](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

Le **[!UICONTROL cron_schedule table updates]** frame examine le nombre de mises à jour de table planifiées cron pendant une période sélectionnée. Une activité élevée lors de la suppression ou de la mise à jour de ce tableau peut indiquer un problème avec les crons. En outre, les crons mettent à jour cette table lorsqu’ils s’exécutent et se terminent. Par conséquent, s’il n’y a aucune activité sur cette table et que des crons sont configurés, il peut y avoir un problème avec les crons.

## [!UICONTROL Datastore Operations Tables]

![Tables des opérations de banque de données](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

Le **[!UICONTROL Datastore Operations Tables]** examine les opérations de table de base de données, notamment `SELECT`, `DELETE`, et `UPDATE` sur une période sélectionnée. Ce cadre affiche les tables de la base avec la fréquence d&#39;opération la plus élevée par rapport à elles.
