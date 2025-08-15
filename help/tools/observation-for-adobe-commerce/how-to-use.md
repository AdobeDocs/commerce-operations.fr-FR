---
title: 'Comment utiliser l’ [!DNL Observation for Adobe Commerce] '
description: Découvrez comment utiliser l’ [!DNL Observation for Adobe Commerce] .
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Comment utiliser l’aiguille [!DNL Observation for Adobe Commerce]

## Approche générale d’examen des questions

Vérifiez les états des ressources d’environnement :

* Examinez le pourcentage d’images **[!UICONTROL Storage Free and MySQL % free storage by node]**.

   * Suivez les liens de l&#39;en-tête du cadre si vous constatez un stockage faible.

* Examinez le pourcentage d’images **[!UICONTROL free system memory and Swap memory free in bytes]**.

   * Si ces derniers présentent un état de mémoire très faible, ils peuvent contribuer à des problèmes.

* Examinez le cadre de **[!UICONTROL Alerts during the timeframe]**.

   * Adobe Commerce sur les infrastructures cloud fournit des [!DNL Managed alerts]. Vous pouvez cliquer sur le lien de l’en-tête pour afficher [!DNL Support Knowledge Base] articles qui vous aideront à déterminer les actions à entreprendre par vous-même pour des alertes spécifiques.

* Examinez l’image **[!UICONTROL CPU % by host]** : si elle présente une utilisation élevée du CPU, vérifiez l’article [!DNL Support Knowledge Base] dans l’en-tête pour l’image. Vérifiez également que les imports/exports de base de données ou les sauvegardes ne sont pas effectués pendant les périodes de trafic élevé.

* Vérifiez la période **[!UICONTROL Web Traffic volume compared to one week ago]** : Si le trafic est beaucoup plus important que la semaine précédente sur la même période, peut-il être expliqué (campagne de vente ou nouveaux produits qui ont été commercialisés, par exemple) ?
   * Si une augmentation du trafic ne peut pas être expliquée, regardez le Temps de réponse moyen (millisecondes) pour l’environnement de production. Le trafic plus élevé contribue-t-il à un temps de réponse différent de ce qui est normal ? Étendez la période pour voir s’il s’agit d’une anomalie.
   * L’augmentation du trafic a-t-elle une incidence sur les transactions web ? Recherchez des erreurs dans la période de **[!UICONTROL Response Code]**. Si le site est en panne, vous pouvez cliquer sur le lien `Site Down?` dans l’en-tête du cadre. La trame identifiera toutes les erreurs qui se produisent et leur fréquence.
   * Quelqu’un a-t-il déployé les modifications sur votre site web ? La période de **[!UICONTROL Deployment Log Entries]** indique si des déploiements ont été effectués au cours de la période de problème. Si le problème survient immédiatement après le déploiement, il se peut que les activités de déploiement ajoutent une charge supplémentaire au site (caches effacés, services redémarrés, etc.).
   * Y a-t-il eu un upsize ou un downsize ? Si votre site a été temporairement mis à niveau, il se peut qu’il ait retrouvé sa taille d’origine. Si une demande a été faite pour augmenter la capacité du site, une upsize peut se produire. Vérifiez le cadre **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]**. Cette trame détecte parfois une panne sur un nœud particulier. Si la taille diminue, cela peut indiquer un problème avec un ou plusieurs nœuds.

* L’onglet **[!UICONTROL IP Frequency]** identifie la fréquence des requêtes à partir des adresses IP créées par rapport aux serveurs d’origine (ce qui signifie que la requête n’a pas pu être traitée à partir de [!DNL Fastly], car 74 elle n’a pas été mise en cache).

   * Pour tout problème lié au [!DNL Fastly], vérifiez le cadre de **[!UICONTROL Fastly Cache]**, puis sélectionnez la facette Erreur afin d’afficher le pourcentage de requêtes en erreur. Elles peuvent indiquer un problème de serveur principal si elles coïncident avec un chargement non web.
   * Si la charge ne semble pas due au trafic web, des erreurs peuvent se produire ou des requêtes non web peuvent se produire, telles que des requêtes lentes ou des [!DNL crons].

* Vérifiez la période de **[!UICONTROL Database Errors]** pour détecter les erreurs qui pourraient coïncider avec la chronologie du problème.
* Vérifiez le cadre de **[!UICONTROL Database mysql-slow.log]** pour identifier les instructions SQL en cours. Les commandes `INSERT`, `UPDATE` et `DELETE` peuvent prendre un certain temps si la requête n’est pas optimisée. Même les instructions `SELECT` peuvent s’avérer très inefficaces si elles sont appliquées à des tables volumineuses.
* Les cadres **[!UICONTROL PHP States]** et **[!UICONTROL PHP Errors]** montreront des problèmes potentiels avec PHP. Le cadre **[!UICONTROL PHP States]** affiche les terminaisons de processus PHP, les démarrages, et quand le service atteint l&#39;état ready par nœud. La trame **[!UICONTROL PHP Errors]** peut aider à isoler où est le problème avec PHP, comme la taille de la mémoire, les programmes de travail, ou le nombre de serveurs.
* Pour afficher la latence des transactions, le tableau Transactions - Moyenne, Max, Min peut être trié par colonne pour afficher la durée de transaction la plus longue. Un cluster surchargé aura des durées latentes dans les transactions, mais il affichera également les anomalies qui pourraient indiquer un problème avec une méthode ou une [!DNL cron].
* Le cadre de **[!UICONTROL Cron error]** affiche les verrous [!DNL cron], les erreurs SQL qui peuvent être associées aux journaux [!DNL cron] et les [!DNL crons] d’évaluation partagées qui peuvent s’exécuter sur les environnements de production lorsqu’il existe un environnement d’évaluation dédié.
* L&#39;image [!UICONTROL ElasticSearch Errors] affiche les erreurs qui peuvent indiquer des problèmes majeurs avec les requêtes, les données ou les index [!DNL Elasticsearch].
