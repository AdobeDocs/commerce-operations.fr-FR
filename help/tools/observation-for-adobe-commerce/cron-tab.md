---
title: 'Onglet  [!DNL Cron] '
description: En savoir plus sur l [!DNL Cron] onglet de  [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Onglet [!DNL Cron]

Cet onglet permet d’isoler rapidement les problèmes et les causes des problèmes [!DNL cron].

## [!UICONTROL Cron transaction duration in seconds]

![Durée de la transaction Cron en secondes](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

La période **[!UICONTROL Cron transaction duration in seconds]** affiche [!DNL crons] durée de transaction en secondes. Cette option affiche les transactions dont les durées d’exécution sont longues. Un examen plus approfondi d’APM affichera plus de détails sur la requête que la transaction/opération peut exécuter.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![MySQL Non Sleeping Threads par nœud](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

Le cadre **[!UICONTROL MySQL Non-Sleeping Threads by Node]** affiche les threads MySQL non mis en veille par nœud sur la période sélectionnée.

## [!UICONTROL SQL Trace count by path]

![Nombre de traces SQL par chemin](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

Le cadre **[!UICONTROL SQL Trace count by path]** examine les nombres de traces MySQL par chemin d’accès, ce qui peut aider à suivre les instructions SQL sur une période sélectionnée.

## [!UICONTROL Cron database call]

![Appel de base de données Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

Le cadre de **[!UICONTROL Cron database call]** examine le nombre de [!DNL crons] appelant la base de données sur une période sélectionnée.

## [!UICONTROL Cron schedule table locks]

![Verrous de table de planification cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

L’intervalle de **[!UICONTROL Cron schedule table locks]** examine [!DNL cron] verrous de table de planification sur un intervalle de temps sélectionné.

## [!UICONTROL Cron schedule clean cron fired]

![Verrous de table de planification cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

L’intervalle de **[!UICONTROL Cron schedule clean cron fired]** examine le nombre de [!DNL crons] nettoyés sur une période sélectionnée. Si aucune donnée n’est affichée dans ce cadre, cela peut indiquer un problème d’exécution correcte du [!DNL crons]. Si le planning de tâche [!DNL cron] n’est pas nettoyé, [!DNL crons] ne s’exécutera pas de manière optimale et peut prendre plus de temps.

## [!UICONTROL Cron schedule clean records details table]

![Tableau des détails des enregistrements nettoyés planifiés par Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

Le tableau **[!UICONTROL Cron schedule clean records details table]** fournit des détails sur la tâche de nettoyage des enregistrements du tableau `cron_schedule` sur une période sélectionnée.

## [!UICONTROL cron_schedule table updates]

![mises à jour de la table cron_schedule](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

L&#39;intervalle de **[!UICONTROL cron_schedule table updates]** examine le nombre de mises à jour [!DNL cron] du tableau planifié sur une période sélectionnée. Une activité élevée lors de la suppression ou de la mise à jour de ce tableau peut indiquer un problème lié à [!DNL crons]. En outre, [!DNL crons] mettez à jour ce tableau lorsqu’il s’exécute et se termine. Par conséquent, s’il n’y a aucune activité sur ce tableau et qu’il n’y a [!DNL crons] de configurés, un problème peut se produire avec [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![Tables d’opérations du magasin de données](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

Le **[!UICONTROL Datastore Operations Tables]** examine les opérations sur les tables de la base de données, y compris les `SELECT`, les `DELETE` et les `UPDATE` sur une période sélectionnée. Cette image montre les tables de base de données avec la fréquence d&#39;opération la plus élevée par rapport à elles.
