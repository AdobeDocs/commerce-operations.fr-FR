---
title: Onglet  [!DNL Cron]
description: En savoir plus sur l’onglet  [!DNL Cron] de [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Onglet [!DNL Cron]

Cet onglet permet d’isoler rapidement les problèmes et les causes de problèmes [!DNL cron].

## [!UICONTROL Cron transaction duration in seconds]

![Durée de transaction Cron en secondes](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

L’image **[!UICONTROL Cron transaction duration in seconds]** affiche [!DNL crons] durée de transaction en secondes. Cela affichera les transactions qui ont de longs exécutions. Un examen plus approfondi du modèle de gestion des actifs numériques (APM) donnera plus de détails sur la requête que la transaction/opération peut exécuter.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![MySQL non dormant Threads par noeud](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

L’image **[!UICONTROL MySQL Non-Sleeping Threads by Node]** affiche les threads MySQL non endormis par noeud pendant la période sélectionnée.

## [!UICONTROL SQL Trace count by path]

![ Nombre de traces SQL par chemin](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

L’image **[!UICONTROL SQL Trace count by path]** examine le nombre de traces MySQL par chemin d’accès, ce qui peut aider à suivre les instructions SQL sur une période sélectionnée.

## [!UICONTROL Cron database call]

![Appel de base de données Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

L’image **[!UICONTROL Cron database call]** examine le nombre d’appels [!DNL crons] à la base de données au cours d’une période sélectionnée.

## [!UICONTROL Cron schedule table locks]

![Verrouillages de table de planification Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

L’image **[!UICONTROL Cron schedule table locks]** examine la table de planification [!DNL cron] verrouillée sur une période sélectionnée.

## [!UICONTROL Cron schedule clean cron fired]

![Verrouillages de table de planification Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

L’image **[!UICONTROL Cron schedule clean cron fired]** examine le nombre de [!DNL crons] nettoyés au cours d’une période sélectionnée. Si aucune donnée n’est affichée dans ce cadre, cela peut indiquer un problème lié à l’exécution correcte de [!DNL crons]. Si le planning de la tâche [!DNL cron] n&#39;est pas nettoyé, [!DNL crons] ne s&#39;exécutera pas de manière optimale et peut prendre plus de temps à s&#39;exécuter.

## [!UICONTROL Cron schedule clean records details table]

![Table des détails des enregistrements de nettoyage de la planification Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

La table **[!UICONTROL Cron schedule clean records details table]** fournit des détails sur la tâche de nettoyage des enregistrements de la table `cron_schedule` pendant une période sélectionnée.

## [!UICONTROL cron_schedule table updates]

![Mises à jour de la table cron_schedule](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

L’image **[!UICONTROL cron_schedule table updates]** examine le nombre de [!DNL cron] mises à jour de table planifiées au cours d’une période sélectionnée. Une activité élevée lors de la suppression ou de la mise à jour de cette table peut indiquer un problème avec [!DNL crons]. En outre, [!DNL crons] mettez à jour cette table lorsqu&#39;elle s&#39;exécute et se termine. Par conséquent, si aucune activité n&#39;est présente sur cette table et qu&#39;il y a [!DNL crons] configuré, il peut y avoir un problème avec [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![Tables des opérations de l’entrepôt de données](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

**[!UICONTROL Datastore Operations Tables]** examine les opérations de table de base de données, y compris `SELECT`, `DELETE` et `UPDATE` sur une période sélectionnée. Ce cadre affiche les tables de la base avec la fréquence d&#39;opération la plus élevée par rapport à elles.
