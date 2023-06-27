---
title: Comment utiliser la variable [!DNL Observation for Adobe Commerce] nerdlet
description: Découvrez comment utiliser le [!DNL Observation for Adobe Commerce] le petit oiseau.
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Comment utiliser la variable [!DNL Observation for Adobe Commerce] nerdlet

## Approche générale de l’examen des problèmes

Vérifiez les états des ressources d’environnement :

* Examiner le pourcentage de **[!UICONTROL Storage Free and MySQL % free storage by node]** images.

   * Suivez les liens dans l’en-tête du cadre si le stockage est faible.

* Examiner le pourcentage de **[!UICONTROL free system memory and Swap memory free in bytes]** images.

   * Si ces états de mémoire sont très faibles, ils peuvent contribuer à des problèmes.

* Examinez les **[!UICONTROL Alerts during the timeframe]** cadre.

   * Adobe Commerce sur l’infrastructure cloud fournit [!DNL Managed alerts]. Vous pouvez cliquer sur le lien dans l’en-tête pour afficher [!DNL Support Knowledge Base] des articles qui vous aideront à déterminer les actions de votre part pour des alertes spécifiques.

* Examinez les **[!UICONTROL CPU % by host]** frame : Si l’utilisation du processeur est élevée, vérifiez la variable [!DNL Support Knowledge Base] article dans l’en-tête du cadre. Vérifiez également que les imports/exports de base de données ou les sauvegardes ne sont pas effectués pendant les périodes de pointe du trafic.

* Vérifiez les **[!UICONTROL Web Traffic volume compared to one week ago]** frame : Si le trafic est beaucoup plus élevé que la semaine précédente au cours de la même période, peut-il être expliqué (campagne de vente ou nouveaux produits qui ont été commercialisés, par exemple) ?
   * S’il n’est pas possible d’expliquer l’augmentation du trafic, consultez la mesure Temps de réponse moyen (millisecondes) de l’environnement de production. Le trafic élevé contribue-t-il à un temps de réponse différent de ce qui est normal ? Développez la période pour voir s’il s’agit d’une anomalie.
   * L’augmentation du trafic a-t-elle un impact sur les transactions web ? Vérifiez les **[!UICONTROL Response Code]** cadre pour les erreurs. Si le site est en panne, vous pouvez cliquer sur la variable `Site Down?` dans l’en-tête du cadre. Le cadre identifie les erreurs qui se produisent et leur fréquence.
   * Quelqu’un a-t-il déployé les modifications sur votre site web ? Le **[!UICONTROL Deployment Log Entries]** cadre indique si des déploiements ont été effectués pendant la période du problème. Si le problème se produit immédiatement après le déploiement, il se peut que les activités de déploiement ajoutent une charge supplémentaire au site (mises en cache effacées, services redémarrés, etc.).
   * Une modification ou une réduction de taille s’est-elle produite ? Si votre site a été temporairement mis à niveau, il a peut-être été redéfini à sa taille de grappe d’origine. Si une demande a été faite pour augmenter la capacité du site, une modification de taille peut se produire. Vérifiez les **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** cadre. Cette image détecte parfois une panne sur un noeud particulier. Si la taille diminue, cela peut indiquer un problème avec un ou plusieurs noeuds.

* Le **[!UICONTROL IP Frequency]** identifie la fréquence des demandes provenant d’adresses IP effectuées sur les serveurs d’origine (ce qui signifie que la demande n’a pas pu être diffusée à partir de [!DNL Fastly] comme 74, il n’a pas été mis en cache).

   * Pour tout [!DNL Fastly] problèmes connexes, vérifiez les **[!UICONTROL Fastly Cache]** et sélectionnez la facette Erreur pour afficher le pourcentage de requêtes qui sont des erreurs. Ils peuvent indiquer un problème de serveur principal s’ils correspondent à un chargement non web.
   * Si la charge ne semble pas être due au trafic web, il peut y avoir des erreurs ou une compilation de requêtes non-web, telles que des requêtes lentes ou [!DNL crons].

* Vérifiez les **[!UICONTROL Database Errors]** cadre pour les erreurs qui peuvent coïncider avec la chronologie des problèmes/problèmes.
* Vérifiez les **[!UICONTROL Database mysql-slow.log]** image pour identifier les instructions SQL qui se produisent. `INSERT`, `UPDATE`, et `DELETE` peut prendre un certain temps si la requête n’est pas optimisée. Même `SELECT` Les instructions peuvent être très inefficaces si elles sont effectuées sur des tables volumineuses.
* **[!UICONTROL PHP States]** et **[!UICONTROL PHP Errors]** Les images présenteront des problèmes potentiels avec PHP. Le **[!UICONTROL PHP States]** frame affiche les mises en fin de processus PHP, les démarrages et lorsque le service atteint l’état prêt par noeud. Le **[!UICONTROL PHP Errors]** Frame peut aider à isoler l’emplacement du problème avec PHP, comme la taille de la mémoire, les programmes de travail ou le nombre de serveurs.
* Pour afficher la latence des transactions, la table Transactions - Avg, Max, Min peut être triée par colonne afin d&#39;afficher la durée de transaction la plus longue. Une grappe surchargée aura des durées latentes dans les transactions, mais affichera également des anomalies qui pourraient signaler un problème avec une méthode ou [!DNL cron].
* Le **[!UICONTROL Cron error]** l’image s’affiche. [!DNL cron] verrous, erreurs SQL pouvant être associées à [!DNL cron] journaux et évaluation partagée [!DNL crons] qui peut être exécuté sur des environnements de production lorsqu’il existe un environnement d’évaluation dédié.
* Le [!UICONTROL ElasticSearch Errors] frame affiche des erreurs qui peuvent indiquer des problèmes majeurs avec [!DNL Elasticsearch] requêtes, données ou index.
