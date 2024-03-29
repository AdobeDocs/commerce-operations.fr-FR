---
title: La variable [!DNL Cron] tab
description: En savoir plus sur les [!DNL Cron] de [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# La variable [!DNL Cron] tab

Cet onglet permet d’isoler rapidement les problèmes et les causes de [!DNL cron] problèmes.

## [!UICONTROL Cron transaction duration in seconds]

![Durée de transaction du cron en secondes](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

La variable **[!UICONTROL Cron transaction duration in seconds]** affichage des images [!DNL crons] durée de la transaction en secondes. Cela affichera les transactions qui ont de longs exécutions. Un examen plus approfondi du modèle de gestion des actifs numériques (APM) donnera plus de détails sur la requête que la transaction/opération peut exécuter.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![Threads non dormantes MySQL par noeud](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

La variable **[!UICONTROL MySQL Non-Sleeping Threads by Node]** Le cadre affiche les threads MySQL non endormis par noeud pendant la période sélectionnée.

## [!UICONTROL SQL Trace count by path]

![Nombre de traces SQL par chemin](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

La variable **[!UICONTROL SQL Trace count by path]** frame examine le nombre de traces MySQL par chemin, ce qui peut aider à suivre les instructions SQL sur une période sélectionnée.

## [!UICONTROL Cron database call]

![Appel de base de données Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

La variable **[!UICONTROL Cron database call]** frame examine le nombre de [!DNL crons] appel à la base de données pendant une période sélectionnée.

## [!UICONTROL Cron schedule table locks]

![Verrouillements du tableau de planification cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

La variable **[!UICONTROL Cron schedule table locks]** images [!DNL cron] le tableau planning se verrouille sur une période sélectionnée.

## [!UICONTROL Cron schedule clean cron fired]

![Verrouillements du tableau de planification cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

La variable **[!UICONTROL Cron schedule clean cron fired]** frame examine le nombre de [!DNL crons] nettoyé pendant une période sélectionnée. Si aucune donnée n’est affichée dans ce cadre, cela peut indiquer un problème avec [!DNL crons] s’exécutant correctement. Si la variable [!DNL cron] le planning de traitement n&#39;est pas nettoyé, [!DNL crons] ne s’exécute pas de manière optimale et peut prendre plus de temps à s’exécuter.

## [!UICONTROL Cron schedule clean records details table]

![Tableau des détails des enregistrements de nettoyage du planning cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

La variable **[!UICONTROL Cron schedule clean records details table]** fournit des détails sur la tâche de nettoyage des enregistrements de la `cron_schedule` tableau pendant une période sélectionnée.

## [!UICONTROL cron_schedule table updates]

![Mises à jour de la table cron_schedule](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

La variable **[!UICONTROL cron_schedule table updates]** frame examine le nombre de [!DNL cron] les mises à jour du tableau planifié pendant une période sélectionnée. Une activité élevée lors de la suppression ou de la mise à jour de ce tableau peut indiquer un problème avec [!DNL crons]. En outre, [!DNL crons] mettre à jour cette table lorsqu’elle est en cours d’exécution et qu’elle est terminée. Par conséquent, s’il n’y a aucune activité sur cette table et qu’il y a [!DNL crons] configuré, il peut y avoir un problème avec [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![Tables des opérations de banque de données](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

La variable **[!UICONTROL Datastore Operations Tables]** examine les opérations de table de base de données, notamment `SELECT`, `DELETE`, et `UPDATE` sur une période sélectionnée. Ce cadre affiche les tables de la base avec la fréquence d&#39;opération la plus élevée par rapport à elles.
