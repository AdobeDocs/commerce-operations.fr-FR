---
title: Onglet [!UICONTROL MySQL]
description: En savoir plus sur l’onglet [!UICONTROL MySQL] de  [!DNL Observation for Adobe Commerce].
exl-id: 1d8dd07c-15fd-4ffd-ad10-0d886bf1579e
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 0%

---

# Onglet [!UICONTROL MySQL]

## [!UICONTROL MySQL% free storage by node]

![Stockage libre MySQL% par nœud](../../assets/tools/observation-for-adobe-commerce/mysql-tab-1.jpg)

De nombreux problèmes sont causés par le manque d&#39;espace de stockage de MySQL dans le stockage affecté à MySQL (`datadir` paramètre de configuration MySQL, la valeur par défaut est `/data/mysql`) ou le manque d&#39;espace de `tmpdir`. La `tmpdir` par défaut (paramètre MySQL) est `/tmp`. L’image **[!UICONTROL MySQL% free storage by node]** examine le `/, /tmp` (s’il est défini comme un montage distinct) et le pourcentage `/data/mysql` de stockage libre. À partir de la version 5.7 de MySQL (MariaDB version 10.2), les tables `tmp` décompressées sont écrites dans un espace disque logique `tmp` dans le répertoire `/data/mysql` du fichier (ibtmp1). Ce fichier se développe automatiquement sans limite par défaut. Comme il s’agit d’un tablespace, sa taille ne diminuera pas et sera réinitialisée à 12 Mo lors du redémarrage de MySQL.

## [!UICONTROL MySQL Connections by Node]

![&#x200B; Connexions MySQL par nœud &#x200B;](../../assets/tools/observation-for-adobe-commerce/mysql-tab-2.jpg)

Le cadre **[!UICONTROL MySQL Connections by Node]** indique les périodes de panne des nœuds de la base de données ou les volumes élevés de connexions.

## [!UICONTROL MySQL Node Summary]

![Résumé du nœud MySQL](../../assets/tools/observation-for-adobe-commerce/mysql-tab-3.jpg)

Le tableau **[!UICONTROL MySQL Node Summary]** affiche les détails du nœud de base de données, tels que la version du logiciel et le type d’instance (taille).

## [!UICONTROL Galera Number of Nodes in cluster]

![Nombre de galères de nœuds dans le cluster](../../assets/tools/observation-for-adobe-commerce/mysql-tab-4.jpg)

Le cadre **[!UICONTROL Galera Number of Nodes in cluster]** affiche des informations provenant des journaux MySQL. Lorsque les nœuds rejoignent et quittent un cluster, seuls les messages de la période sélectionnée s’affichent. Si un nœud quitte le cluster avant la période, aucun message n’existera pendant cette période. Si vous pensez que la base de données est à court d’un nœud, étendez le délai à une période plus longue pour voir si vous pouvez voir des informations supplémentaires. S’il existe des informations pendant la période qui indiquent un nombre inférieur à tous les nœuds du cluster [!DNL Galera], développez le délai pour voir si vous pouvez déterminer quand le nœud a quitté le cluster.

## [!UICONTROL MySQL shutdowns and starts]

![Arrêts et démarrages de MySQL](../../assets/tools/observation-for-adobe-commerce/mysql-tab-5.jpg)

L’image **[!UICONTROL MySQL shutdowns and starts]** détecte un arrêt d’un nœud. Les nœuds [!DNL Galera] seront évincés et s’évinceront automatiquement du nœud [!DNL Galera]. Cela entraîne généralement un redémarrage du service MySQL.

## [!UICONTROL Galera log]

![Journal Galera](../../assets/tools/observation-for-adobe-commerce/mysql-tab-6.jpg)

La trame **[!UICONTROL Galera log]** affiche le nombre de signaux particuliers des logs MySQL concernant les nœuds [!DNL Galera], leurs états et les changements d&#39;état du cluster [!DNL Galera].

* &#39;%1047 WSREP n&#39;a pas encore préparé le nœud pour l&#39;utilisation de l&#39;application%&#39;) comme &#39;node_not_prep_for_use&#39;
* &#39;%\[ERROR\] WSREP : échec de la lecture depuis : wsrep_sst_xtrabackup-v2%&#39;) en tant que &#39;xtrabackup_read_fail&#39;
* &#39;%\[ERROR\] WSREP : processus terminé avec erreur : wsrep_sst_xtrabackup-v2 %&#39;) as &#39;xtrabackup_compl_w_err&#39;
* &#39;%\[ERROR\] WSREP : échec d’écriture rbr%&#39;) as &#39;rbr_write_fail&#39;
* &#39;%self-leave%&#39;) comme &#39;susp_node&#39;
* &#39;%members = 3/3 (joint/total)%&#39;) as&#39;3of3&#39;
* &#39;%members = 2/3 (joint/total)%&#39;) as&#39;2of3&#39;
* &#39;%members = 2/2%&#39;) as &#39;2of2&#39;
* &#39;%members = 1/2%&#39;) as &#39;1of2&#39;
* &#39;%members = 1/3%&#39;) comme &#39;1of3&#39;
* &#39;%members = 1/1%&#39;) comme &#39;1of1&#39;
* &#39;%\[Note\] /usr/sbin/mysqld (mysqld 10.%&#39;) as&#39;sql_restart&#39;
* &#39;%Quorum : aucun nœud avec l&#39;état complet :%&#39;) comme &#39;no_node_count&#39;
* &#39;%WSREP: Member 0%&#39;) as &#39;mem_0&#39;
* &#39;%WSREP: Member 1.0%&#39;) as &#39;mem_1&#39;
* &#39;%WSREP: Member 2%&#39;) as&#39;mem2&#39;
* &#39;%WSREP : synchronisé avec le groupe, prêt pour les connexions%&#39;) comme &#39;prêt&#39;
* &#39;%/usr/sbin/mysqld, Version:%&#39;) as &#39;mysql_restart_mysql.slow&#39;
* &#39;%\[Remarque\] WSREP : nouvelle vue de cluster : état global :%&#39;) as &#39;galera_cluster_view_chng&#39;

## [!UICONTROL Galera Log by Host]

![Journal Galera par hôte](../../assets/tools/observation-for-adobe-commerce/mysql-tab-7.jpg)

L’image **[!UICONTROL Galera Log by Host]** est identique à l’image **[!UICONTROL Galera log]**, à la différence qu’elle est divisée par nœud pour faciliter la résolution des problèmes.

## [!UICONTROL Database performance]

![Performances de la base de données](../../assets/tools/observation-for-adobe-commerce/mysql-tab-8.jpg)

Le cadre **[!UICONTROL Database performance]** affiche les performances de la base de données lors de requêtes spécifiques. Pour afficher chaque mesure, cliquez dessus dans les icônes de couleur situées sous le graphique. La plupart des mesures répertoriées dans [Surveillance des performances de la base de données MySQL avec New Relic](https://newrelic.com/blog/how-to-relic/how-to-monitor-mysql) se trouvent dans cet écran.

* average(query.queriesPerSecond)
* average(query.slowQueriesPerSecond)
* average(db.createdTmpDiskTablesPerSecond)
* average(db.createdTmpFilesPerSecond)
* average(db.tablesLocksWaitedPerSecond)
* average(db.innodb.rowLockTimeAvg)
* average(db.innodb.rowLockWaitsPerSecond)

## [!UICONTROL Transaction Database Call Count]

![Nombre d’appels de la base de données de transactions](../../assets/tools/observation-for-adobe-commerce/mysql-tab-9.jpg)

Le cadre **[!UICONTROL Transaction Database Call Count]** affiche le nombre d’appels à la base de données effectués par chaque facette de transaction. Cela semble être axé sur les lignes et non sur les déclarations.

## [!UICONTROL Cron_schedule table updates]

![Mises à jour de la table Cron_schedule](../../assets/tools/observation-for-adobe-commerce/mysql-tab-10.jpg)

Le cadre **[!UICONTROL Cron_schedule table updates]** affiche la durée maximale des mises à jour de la base de données dans la table cron_schedule pour la période sélectionnée.

## [!UICONTROL Slow Query Traces]

![Traces de requête lentes](../../assets/tools/observation-for-adobe-commerce/mysql-tab-11.jpg)

Le cadre **[!UICONTROL Slow Query Traces]** affiche la table et le type de requête où il existe des traces de requête lentes. Une trace de requête lente est créée pour les transactions de requête qui prennent plus de cinq secondes. Les requêtes de mise à jour sont importantes pour ce cadre. Si une table est mise à jour par des instructions `UPDATE`, `DELETE` et `INSERT`, elle peut être verrouillée pendant un certain temps.

Même les instructions `SELECT` peuvent verrouiller des lignes si elles sont utilisées avec FOR UPDATE.

## [!UICONTROL Datastore Operations tables]

![Tables des opérations du magasin de données](../../assets/tools/observation-for-adobe-commerce/mysql-tab-12.jpg)

## [!UICONTROL Cron table change]

![Modification du tableau Cron](../../assets/tools/observation-for-adobe-commerce/mysql-tab-13.jpg)

La trame **[!UICONTROL Cron table change]** recherche les messages d&#39;erreur « impossible d&#39;acquérir le verrou pour la tâche cron : », ainsi qu&#39;une erreur de mémoire PHP spécifique et des verrous impliquant la table `cron_schedule`. Si la table `cron_schedule` est verrouillée (par exemple, si une requête `DELETE` est exécutée sur celle-ci), cela empêchera l’exécution d’autres crons.

## [!UICONTROL Deadlocks]

![Blocages](../../assets/tools/observation-for-adobe-commerce/mysql-tab-14.jpg)

Le cadre **[!UICONTROL Deadlocks]** examine les chaînes suivantes analysées à partir des journaux MySQL :

* &#39;%PHP Erreur fatale : taille de la mémoire autorisée de%&#39;) comme php_mem_error
* &#39;%get lock; essayez de redémarrer la transaction, la requête était : DELETE FROM \`cron_schedule%&#39;) as cron_sched_lock_del
* &#39;% lock pour le traitement cron : indexer_reindex_all_invalid%&#39;) as &#39;lock_indexer_reindex_all_invalid%&#39;
* &#39;% lock pour le traitement cron : cron_schedule%&#39;) as &#39;lock_cron_schedule&#39;
* &#39;% lock pour le traitement cron :%&#39;) as &#39;total_cron_lock&#39;
* « %Erreur générale : le délai d&#39;attente du verrouillage 1205 a dépassé % ») en tant que « sql_1205_lock »
* &#39;%ERROR 1213 (40001) : interblocage détecté lors de la tentative d&#39;obtention du verrou%&#39;) en tant que &#39;sql_1213_lock&#39;
* &#39;%SQLSTATE[40001] : échec de sérialisation : 1213 blocage trouvé%&#39;) en tant que &#39;sql_1213_lock2&#39;
* &#39;% lock pour cron job : indexer_update_all_views%&#39;) as &#39;lock_indexer_update_all_views&#39;
* &#39;% lock pour le traitement cron : sales_grid_order_facture_async_insert%&#39;) as &#39;lock_sales_grid_order_facture_async_insert&#39;,
* « % de verrouillage pour la tâche cron : staging_remove_updates% ») comme « lock_staging_remove_updates »
* &#39;% lock pour le traitement cron : sales_grid_order_shipping_async_insert%&#39;) as &#39;lock_sales_grid_order_shipping_async_insert&#39;
* &#39;% lock pour le traitement cron : amazon_Payments_process_queued_refunds%&#39;) as &#39;lock_amazon_Payments_process_queued_refunds&#39;
* &#39;% de verrouillage pour le traitement cron : sales_send_order_shipping_emails%&#39;) as &#39;lock_sales_send_order_shipping_emails&#39;
* &#39;% de verrouillage pour le traitement cron : staging_synchronize_entities_period%&#39;) as &#39;lock_staging_synchronize_entities_period&#39;
* &#39;% lock pour la tâche cron : indexer_clean_all_changelogs%&#39;) as &#39;lock_indexer_clean_all_changelogs&#39;
* &#39;% lock pour le traitement cron : magento_targetrule_index_reindex%&#39;) as &#39;lock_magento_targetrule_index_reindex&#39;
* &#39;% de verrouillage pour la tâche cron : newsletter_send_all%&#39;) as &#39;lock_newsletter_send_all&#39;
* &#39;% de verrouillage pour la tâche cron : newsletter_send_all%&#39;) as &#39;lock_newsletter_send_all&#39;
* &#39;% de verrouillage pour le traitement cron : sales_send_order_emails%&#39;) as &#39;lock_sales_send_order_emails&#39;
* &#39;% de verrouillage pour le traitement cron : sales_send_order_creditmemo_emails%&#39;) as &#39;lock_sales_send_order_creditmemo_emails&#39;
* &#39;% lock pour le traitement cron : sales_grid_order_creditmemo_async_insert%&#39;) as &#39;lock_sales_grid_order_creditmemo_async_insert&#39;
* &#39;% lock pour la tâche cron : bulk_cleanup%&#39;) as &#39;lock_bulk_cleanup&#39;
* &#39;% lock pour le traitement cron : flush_preview_quotas%&#39;) as &#39;lock_flush_preview_quotas&#39;
* &#39;% de verrouillage pour le traitement cron : sales_send_order_facture_emails%&#39;) as &#39;lock_sales_send_order_facture_emails&#39;
* &#39;% de verrouillage pour le traitement cron : sales_send_order_facture_emails%&#39;) as &#39;lock_sales_send_order_facture_emails&#39;
* &#39;% lock pour le traitement cron : captcha_delete_expired_images%&#39;) as &#39;lock_captcha_delete_expired_images&#39;
* &#39;% de verrouillage pour la tâche cron : magento_newrelicreporting_cron%&#39;) as &#39;lock_magento_newrelicreporting_cron&#39;
* &#39;% lock pour cron job: outdated_authentication_failure_cleanup%&#39;) as &#39;lock_outdated_authentication_failure_cleanup&#39;
* &#39;% lock pour cron job: send_notification%&#39;) as &#39;lock_send_notification&#39;
* &#39;% lock pour le traitement cron : magento_giftcardaccount_generage_codes_pool%&#39;) as &#39;lock_magento_giftcardaccount_generage_codes_pool&#39;
* &#39;% lock pour la tâche cron : catalog_product_frontend_actions_flush%&#39;) as &#39;lock_catalog_product_frontend_actions_flush&#39;
* Verrouillage de % pour la tâche cron : mysqlmq_clean_messages%) en tant que « mysqlmq_clean_messages »
* &#39;% lock pour la tâche cron : catalog_product_attribute_value_synchronize%&#39;) as &#39;lock_catalog_product_attribute_value_synchronize&#39;
* &#39;% lock pour la tâche cron : ddg_automation_importer%&#39;) as &#39;lock_ddg_automation_importer&#39;
* « % de verrouillage pour la tâche cron : ddg_automation_review_and_wishlist% ») as « lock_ddg_automation_views_and_wishlist »
* &#39;% lock pour le traitement cron : captcha_delete_old_attempts%&#39;) as &#39;lock_captcha_delete_old_attempts&#39;
* &#39;% de verrouillage pour la tâche cron : catalog_product_outdated_price_values_cleanup%&#39;) as &#39;lock_catalog_product_outdated_price_values_cleanup&#39;
* « % de verrouillage pour la tâche cron : consumer_runner% ») en tant que « lock_consumer_runner »
* &#39;% lock pour la tâche cron : ddg_automation_customer_subscriber_guest_sync%&#39;) as &#39;lock_ddg_automation_customer_subscriber_guest_sync&#39;
* « % de verrouillage pour la tâche cron : get_amazon_capture_updates% ») sous la forme « lock_get_amazon_capture_updates »
* &#39;% lock pour le traitement cron : get_amazon_authorization_updates%&#39;) as &#39;lock_send_get_amazon_authorization_updates&#39;
* &#39;% lock pour le traitement cron : temando_process_platform_events%&#39;) as &#39;lock_temando_process_platform_events&#39;
* &#39;% lock pour la tâche cron : ddg_automation_status%&#39;) as &#39;lock_ddg_automation_status&#39;
* &#39;% lock pour la tâche cron : ddg_automation_status%&#39;) as &#39;lock_ddg_automation_status&#39;
* &#39;% lock pour le traitement cron : sales_clean_orders%&#39;) as &#39;lock_sales_clean_orders&#39;
* &#39;% de verrouillage pour la tâche cron : catalog_index_refresh_price%&#39;) as &#39;lock_catalog_index_refresh_price&#39;
* &#39;% de verrouillage pour le traitement cron : magento_reward_balance_warning_notification%&#39;) as &#39;lock_magento_reward_balance_warning_notification&#39;
* « % de verrouillage pour la tâche cron : analytics_update% ») en tant que « lock_analytics_update »
* &#39;% lock pour le traitement cron : messagequeue_clean_outdated_locks%&#39;) as &#39;lock_messagequeue_clean_outdated_locks&#39;
* &#39;% lock pour le traitement cron : messagequeue_clean_outdated_locks%&#39;) as &#39;lock_messagequeue_clean_outdated_locks&#39;
* « % de verrouillage pour la tâche cron : staging_apply_version% ») comme « lock_staging_apply_version »
* &#39;% de verrouillage pour la tâche cron : magento_reward_expire_points%&#39;) as &#39;lock_magento_reward_expire_points&#39;
* &#39;% lock pour le traitement cron : yotpo_yotpo_orders_sync%&#39;) as &#39;lock_yotpo_yotpo_orders_sync&#39;
* « % de verrouillage pour la tâche cron : catalog_event_status_checker% ») as « lock_catalog_event_status_checker »
* &#39;% lock pour le traitement cron : ddg_automation_campaign%&#39;) as &#39;lock_ddg_automation_campaign&#39;
* « % de verrouillage pour la tâche cron : visitor_clean% ») en tant que « lock_visitor_clean »
* &#39;% lock pour le traitement cron : scconnector_verify_website%&#39;) as &#39;lock_scconnector_verify_website&#39;
* &#39;% lock pour la tâche cron : ddg_automation_email_templates%&#39;) as &#39;lock_ddg_automation_email_templates&#39;
* &#39;% lock pour le traitement cron : aggregate_sales_report_order_data%&#39;) as &#39;lock_aggregate_sales_report_order_data&#39;
* &#39;% lock pour la tâche cron : ddg_automation_catalog_sync%&#39;) as &#39;lock_ddg_automation

## [!UICONTROL DB Statistics]

![Statistiques BD](../../assets/tools/observation-for-adobe-commerce/mysql-tab-15.jpg)

Le cadre **[!UICONTROL DB Statistics]** affiche les suppressions, les écritures, les lignes lues, les mises à jour et les requêtes lentes par seconde.

## [!UICONTROL Request frequency]

![Fréquence des demandes](../../assets/tools/observation-for-adobe-commerce/mysql-tab-16.jpg)

## [!UICONTROL Database Errors]

![&#x200B; Erreurs de base de données &#x200B;](../../assets/tools/observation-for-adobe-commerce/mysql-tab-17.jpg)

Le cadre de **[!UICONTROL Database Errors]** présente diverses [avertissements et erreurs](https://mariadb.com/kb/en/mariadb-error-codes/) de base de données :

* La taille de la mémoire allouée à la table temporaire est supérieure à 20 % de innodb_buffer_pool_size% en tant que &#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP : échec d’écriture rbr%&#39;) as &#39;rbr_write_fail&#39;
* &#39;%mysqld: Disque plein%&#39;) comme &#39;disk_full&#39;
* &#39;%Error number 28%&#39;) as &#39;err_28&#39;
* &#39;%rollback%&#39;) comme &#39;rollback&#39;
* &#39;%Foreign key_constraint échoue pour la table%&#39;) en tant que &#39;foreign_key_constraint&#39;
* &#39;%Error_code: 1114%&#39;) as &#39;sql_1114_full&#39;&#39;%CRITICAL: SQLSTATE[HY000] [2006] MySQL server has gone%&#39;) as &#39;sql_gone&#39;
* &#39;%SQLSTATE[HY000] [1040] Trop de connexions%&#39;) comme &#39;sql_1040&#39;
* &#39;%CRITICAL : SQLSTATE[HY000] [2002]%&#39;) as &#39;sql_2002&#39;
* &#39;%SQLSTATE[08S01]:%&#39;) as &#39;sql_1047&#39;
* &#39;%[Warning] Abandon de la connexion%&#39;) comme &#39;aborted_conn&#39;
* &#39;%SQLSTATE[23000] : violation de contrainte d&#39;intégrité :%&#39;) as &#39;sql_23000&#39;
* &#39;%1205 Verrouiller le délai d&#39;attente%&#39;) comme &#39;sql_1205&#39;
* &#39;%SQLSTATE[HY000] [1049] Base de données inconnue%&#39;) en tant que &#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02] : table ou vue de base introuvable :%&#39;) comme &#39;sql_42S02&#39;
* « %Erreur générale : 1114 % ») comme « sql_1114 »
* &#39;%SQLSTATE[40001]%&#39;) comme &#39;sql_1213&#39;
* &#39;%SQLSTATE[42S22] : colonne introuvable : 1054 colonne inconnue (%) en tant que &#39;sq1_1054&#39;
* &#39;%SQLSTATE[42000] : erreur de syntaxe ou violation d&#39;accès :%&#39;) as&#39;sql_42000&#39;
* &#39;%SQLSTATE[21000] : violation de cardinalité :%&#39;) as &#39;sql_1241&#39;
* &#39;%SQLSTATE[22003]:%&#39;) comme &#39;sql_22003&#39;
* &#39;%SQLSTATE[HY000] [9000] Client avec adresse IP%&#39;) sous la forme &#39;sql_9000&#39;
* &#39;%SQLSTATE[HY000] : erreur générale : 2014%&#39;) en tant que &#39;sql_2014&#39;
* &#39;%1927 Connexion interrompue%&#39;) en tant que &#39;sql_1927&#39;
* &#39;%1062 \[ERROR\] InnoDB:%&#39;) as &#39;sql_1062_e&#39;
* &#39;&#39;%[Remarque ] WSREP : vidage du mappage de mémoire sur le disque...%&#39;) en tant que &#39;mem_map_flush&#39;
* &#39;%Code d&#39;erreur interne MariaDB : 1146%&#39;) as &#39;sql_1146&#39;
* &#39;%Code d&#39;erreur interne MariaDB : 1062%&#39;) comme &#39;sql_1062&#39; * &#39;%1062 [Avertissement] InnoDB :%&#39;) comme &#39;sql_1062_w&#39;
* &#39;%Code d&#39;erreur interne MariaDB : 1064%&#39;) as &#39;sql_1064&#39;
* &#39;%InnoDB : échec de l&#39;assertion dans le fichier%&#39;) en tant que &#39;assertion_err&#39;
* &#39;%mysqld_safe Nombre de processus en cours d&#39;exécution : 0%&#39;) comme &#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld a obtenu le signal%&#39;) en tant que &#39;mysql_sigterm&#39;
* &#39;%1452 Impossible d&#39;ajouter%&#39;) en tant que &#39;sql_1452&#39;
* &#39;%ERROR 1698%&#39;) as &#39;sql_1698&#39;
* &#39;%SQLSTATE[HY000] : erreur générale : 3%&#39;) en tant que &#39;cnt_write_tmp&#39;
* &#39;%Erreur générale : 1 %&#39;) comme &#39;sql_syntax&#39;
* &#39;%42S22%&#39;) comme &#39;sql_42S22&#39;
* &#39;%InnoDB : erreur (clé en double)%&#39;) en tant que &#39;innodb_dup_key&#39; À PARTIR DES SÉRIES CHRONOLOGIQUES du journal

## [!UICONTROL DB Error Table]

![Tableau d’erreurs DB](../../assets/tools/observation-for-adobe-commerce/mysql-tab-18.jpg)

Le cadre **[!UICONTROL DB Error Table]** affiche les mêmes informations que le cadre **[!UICONTROL Database Errors]**, mais vous pouvez les voir par nœud et au format tableau. Voir [Codes d’erreur MariaDB](https://mariadb.com/kb/en/mariadb-error-codes/) pour plus d’informations.

## [!UICONTROL Database Traces]

![Traces de base de données](../../assets/tools/observation-for-adobe-commerce/mysql-tab-19.jpg)

Le cadre **[!UICONTROL Database Traces]** affiche les traces de la base de données par type sur la chronologie sélectionnée.

## [!UICONTROL Database processes]

![Processus de base de données](../../assets/tools/observation-for-adobe-commerce/mysql-tab-20.jpg)

Le cadre **[!UICONTROL Database processes]** affiche les processus de base de données, les environnements et les identifiants de nœud.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![Threads MySQL non mise en veille par nœud](../../assets/tools/observation-for-adobe-commerce/mysql-tab-21.jpg)

Le cadre **[!UICONTROL MySQL Non-Sleeping Threads by Node]** affiche les threads de connexion à la base de données. Cette image présente les threads actifs.

## [!UICONTROL MySQL Running and Sleeping Threads by environment]

![MySQL Running and Sleeping Threads par environnement](../../assets/tools/observation-for-adobe-commerce/mysql-tab-22.jpg)

Le cadre **[!UICONTROL MySQL Running and Sleeping Threads by environment]** affiche les connexions actives et en veille à la base de données. S’il existe des connexions à la base de données pour lesquelles les requêtes lentes ont été mises en veille, il y aura des connexions en veille. Les connexions en veille peuvent être des requêtes de base de données bloquées par des lignes ou des tables verrouillées. Ces connexions dormantes contiennent également des connexions de programme de travail PHP.

## [!UICONTROL MySQL mem used by node]

![Mémoire MySQL utilisée par le nœud &#x200B;](../../assets/tools/observation-for-adobe-commerce/mysql-tab-23.jpg)

L’image **[!UICONTROL MySQL mem used by node]** affiche l’utilisation de la mémoire par MySQL sur les nœuds. Sur les sites de plus grande taille, cette trame peut être constituée de barres continues dont la mémoire est de l&#39;ordre de Go.

## [!UICONTROL Database mysql-slow.log]

![Base de données mysql-slow.log](../../assets/tools/observation-for-adobe-commerce/mysql-tab-24.jpg)

Le cadre **[!UICONTROL Database mysql-slow.log]** affiche les types d&#39;instructions de requête qui se trouvaient dans le fichier `mysql-slow.log` pendant la période sélectionnée.
