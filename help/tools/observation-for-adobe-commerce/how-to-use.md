---
title: Utilisation du caractère  [!DNL Observation for Adobe Commerce] nerdlet
description: Découvrez comment utiliser le caractère  [!DNL Observation for Adobe Commerce] nerdlet.
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Comment utiliser le mini-servlet [!DNL Observation for Adobe Commerce]

## Approche générale de l’examen des problèmes

Vérifiez les états des ressources d’environnement :

* Examinez le pourcentage d’images **[!UICONTROL Storage Free and MySQL % free storage by node]**.

   * Suivez les liens dans l’en-tête du cadre si le stockage est faible.

* Examinez le pourcentage d’images **[!UICONTROL free system memory and Swap memory free in bytes]**.

   * Si ces états de mémoire sont très faibles, ils peuvent contribuer à des problèmes.

* Examinez l’image **[!UICONTROL Alerts during the timeframe]**.

   * Adobe Commerce sur l’infrastructure cloud fournit [!DNL Managed alerts]. Vous pouvez cliquer sur le lien dans l’en-tête pour afficher [!DNL Support Knowledge Base] articles qui vous aideront à déterminer les actions de votre part pour des alertes spécifiques.

* Examinez l’image **[!UICONTROL CPU % by host]** : si elle présente une utilisation élevée du processeur, vérifiez l’article [!DNL Support Knowledge Base] dans l’en-tête de l’image. Vérifiez également que les imports/exports de base de données ou les sauvegardes ne sont pas effectués pendant les périodes de pointe du trafic.

* Vérifiez l’image **[!UICONTROL Web Traffic volume compared to one week ago]** : si le trafic est beaucoup plus élevé que la semaine précédente au cours de la même période, peut-il être expliqué (campagne de vente ou nouveaux produits qui ont été commercialisés, par exemple) ?
   * S’il n’est pas possible d’expliquer l’augmentation du trafic, consultez la mesure Temps de réponse moyen (millisecondes) de l’environnement de production. Le trafic élevé contribue-t-il à un temps de réponse différent de ce qui est normal ? Développez la période pour voir s’il s’agit d’une anomalie.
   * L’augmentation du trafic a-t-elle un impact sur les transactions web ? Recherchez les erreurs dans l’image **[!UICONTROL Response Code]**. Si le site est en panne, vous pouvez cliquer sur le lien `Site Down?` dans l’en-tête du cadre. Le cadre identifie les erreurs qui se produisent et leur fréquence.
   * Quelqu’un a-t-il déployé les modifications sur votre site web ? L’image **[!UICONTROL Deployment Log Entries]** indique si des déploiements ont été effectués pendant la période du problème. Si le problème se produit immédiatement après le déploiement, il se peut que les activités de déploiement ajoutent une charge supplémentaire au site (mises en cache effacées, services redémarrés, etc.).
   * Une modification ou une réduction de taille s’est-elle produite ? Si votre site a été temporairement mis à niveau, il a peut-être été redéfini à sa taille de grappe d’origine. Si une demande a été faite pour augmenter la capacité du site, une modification de la taille peut se produire. Vérifiez l’image **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]**. Cette image détecte parfois une panne sur un noeud particulier. Si la taille diminue, cela peut indiquer un problème avec un ou plusieurs noeuds.

* L’onglet **[!UICONTROL IP Frequency]** identifie la fréquence des demandes provenant des adresses IP effectuées sur les serveurs d’origine (ce qui signifie que la demande n’a pas pu être diffusée à partir de [!DNL Fastly] car 74 elle n’a pas été mise en cache).

   * Pour tout problème [!DNL Fastly], vérifiez l’image **[!UICONTROL Fastly Cache]** et sélectionnez la facette Erreur pour afficher le pourcentage de requêtes qui sont des erreurs. Ils peuvent indiquer un problème de serveur principal s’ils correspondent à un chargement non web.
   * Si la charge ne semble pas être due au trafic web, il peut y avoir des erreurs ou une compilation de requêtes non-web, telles que des requêtes lentes ou [!DNL crons].

* Recherchez dans l’image **[!UICONTROL Database Errors]** les erreurs qui peuvent coïncider avec la chronologie des problèmes/problèmes.
* Vérifiez l’image **[!UICONTROL Database mysql-slow.log]** pour identifier les instructions SQL qui se produisent. Les commandes `INSERT`, `UPDATE` et `DELETE` peuvent prendre un certain temps si la requête n’est pas optimisée. Même les instructions `SELECT` peuvent être très inefficaces si elles sont effectuées sur des tables volumineuses.
* **[!UICONTROL PHP States]** et **[!UICONTROL PHP Errors]** images afficheront des problèmes potentiels avec PHP. L’image **[!UICONTROL PHP States]** affichera les terminations, les démarrages et lorsque le service atteint l’état prêt par noeud. L’image **[!UICONTROL PHP Errors]** peut aider à isoler l’emplacement du problème avec PHP, comme la taille de la mémoire, les programmes de travail ou le nombre de serveurs.
* Pour afficher la latence des transactions, la table Transactions - Avg, Max, Min peut être triée par colonne afin d&#39;afficher la durée de transaction la plus longue. Une grappe surchargée aura des durées latentes dans les transactions, mais elle affichera également des anomalies qui pourraient signaler un problème avec une méthode ou [!DNL cron].
* L’image **[!UICONTROL Cron error]** affichera des verrous [!DNL cron], des erreurs SQL qui peuvent être associées aux [!DNL cron] journaux et l’évaluation partagée [!DNL crons] qui peut être en cours d’exécution dans les environnements de production lorsqu’il y a un environnement d’évaluation dédié.
* L’image [!UICONTROL ElasticSearch Errors] affiche des erreurs qui peuvent indiquer des problèmes majeurs avec des requêtes, des données ou des index [!DNL Elasticsearch].
