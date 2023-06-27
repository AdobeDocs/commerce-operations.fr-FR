---
title: Le [!UICONTROL MySQL] tab
description: En savoir plus sur les [!UICONTROL MySQL] de [!DNL Observation for Adobe Commerce].
exl-id: 1d8dd07c-15fd-4ffd-ad10-0d886bf1579e
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '2030'
ht-degree: 0%

---

# Le [!UICONTROL MySQL] tab

## [!UICONTROL MySQL% free storage by node]

![Stockage gratuit de MySQL% par noeud](../../assets/tools/observation-for-adobe-commerce/mysql-tab-1.jpg)

De nombreux problèmes sont causés par le manque de stockage de MySQL dans le stockage affecté à MySQL (`datadir` Paramètre de configuration MySQL, la valeur par défaut est `/data/mysql`) ou le `tmpdir` manque d&#39;espace. La valeur par défaut `tmpdir` (paramètre MySQL) est `/tmp`. Le **[!UICONTROL MySQL% free storage by node]** regarde la `/, /tmp` (s’il est défini comme un montage distinct) et la variable `/data/mysql` pourcentage de stockage gratuit. À partir de la version 5.7 de MySQL (MariaDB version 10.2), sans compression `tmp` Les tableaux sont écrits dans une `tmp` tablespace dans le `/data/mysql` dans le fichier (ibtmp1). Par défaut, ce fichier se développe automatiquement sans limite. Comme il s’agit d’un tablespace, sa taille ne diminue pas et il est réinitialisé à 12 Mo au redémarrage de MySQL.

## [!UICONTROL MySQL Connections by Node]

![Connexions MySQL par noeud](../../assets/tools/observation-for-adobe-commerce/mysql-tab-2.jpg)

Le **[!UICONTROL MySQL Connections by Node]** frame indique les périodes de panne des noeuds de base de données ou un grand nombre de connexions.

## [!UICONTROL MySQL Node Summary]

![Résumé des noeuds MySQL](../../assets/tools/observation-for-adobe-commerce/mysql-tab-3.jpg)

Le **[!UICONTROL MySQL Node Summary]** Le tableau affiche les détails du noeud de base de données, tels que la version logicielle et le type d’instance (taille).

## [!UICONTROL Galera Number of Nodes in cluster]

![Nombre de noeuds Galera dans la grappe](../../assets/tools/observation-for-adobe-commerce/mysql-tab-4.jpg)

Le **[!UICONTROL Galera Number of Nodes in cluster]** frame affiche les informations des journaux MySQL. Lorsque les noeuds se rejoignent et quittent une grappe, seuls les messages relatifs à la période sélectionnée s’affichent. Si un noeud quitte la grappe avant la période, aucun message n’existera pendant cette période. Si vous pensez que la base de données manque peut-être d’un noeud, définissez la période sur une période plus longue pour voir si des informations supplémentaires s’affichent. S’il existe des informations au cours de la période qui indiquent moins que tous les noeuds de la variable [!DNL Galera] développez la grappe, développez la période pour voir si vous pouvez déterminer quand le noeud a quitté la grappe.

## [!UICONTROL MySQL shutdowns and starts]

![MySQL ferme et démarre](../../assets/tools/observation-for-adobe-commerce/mysql-tab-5.jpg)

Le **[!UICONTROL MySQL shutdowns and starts]** frame détecte lorsqu’un noeud est arrêté. Le [!DNL Galera] Les noeuds seront expulsés et seront expulsés de la propriété [!DNL Galera] noeud . Cela entraîne généralement un redémarrage du service MySQL.

## [!UICONTROL Galera log]

![Journal des galeries](../../assets/tools/observation-for-adobe-commerce/mysql-tab-6.jpg)

Le **[!UICONTROL Galera log]** frame affiche le nombre de signaux spécifiques provenant des journaux MySQL concernant [!DNL Galera] les noeuds, leurs états et les modifications d’état de la variable [!DNL Galera] grappe.

* &quot;%1047 WSREP n’a pas encore préparé le noeud pour l’application use%&quot;) comme &quot;node_not_prep_for_use&quot;
* &#39;%\[ERROR\] WSREP: Échec de la lecture de : wsrep_sst_xtrabackup-v2%) en tant que &quot;xtrabackup_read_fail&quot;
* &#39;%\[ERROR\] WSREP: Processus terminé avec une erreur : wsrep_sst_xtrabackup-v2 %) en tant que &quot;xtrabackup_compl_w_err&quot;
* &#39;%\[ERROR\] WSREP: rbr write fail%) as &#39;rbr_write_fail&#39;
* &quot;%self-leave%&quot;) sous la forme &quot;usp_node&quot;
* &#39;%members = 3/3 (joint/total)%&#39;) as&#39;3of3&#39;
* &#39;%members = 2/3 (joint/total)%&#39;) as&#39;2of3&#39;
* &#39;%members = 2/2%) comme &quot;2of2&quot;
* &#39;%members = 1/2%&#39;) comme &quot;1of2&quot;
* &#39;%members = 1/3%&#39;) comme &quot;1of3&quot;
* &#39;%members = 1/1%) as &#39;1of1&#39;
* &#39;%\[Remarque\] /usr/sbin/mysqld (mysqld 10.%&#39;) as&#39;sql_restart&#39;
* &#39;%Quorum : Aucun noeud avec l’état complet :%) comme &quot;no_node_count&quot;
* &#39;%WSREP: Member 0%) as &#39;mem_0&#39;
* &#39;%WSREP: Member 1.0%) as &#39;mem_1&#39;
* &#39;%WSREP: Member 2%) as&#39;mem2&#39;
* &#39;%WSREP: Synchronisé avec le groupe, prêt pour les connexions %) comme &quot;prêt&quot;
* &#39;%/usr/sbin/mysqld, Version:%&#39;) comme &#39;mysql_restart_mysql.ralenti&#39;
* &#39;%\[Remarque\] WSREP : Nouvelle vue de grappe : état global :%) comme &quot;galera_cluster_view_chng&quot;

## [!UICONTROL Galera Log by Host]

![Journal Galera par hôte](../../assets/tools/observation-for-adobe-commerce/mysql-tab-7.jpg)

Le **[!UICONTROL Galera Log by Host]** est identique au **[!UICONTROL Galera log]** , mais il est divisé par noeud pour faciliter le dépannage.

## [!UICONTROL Database performance]

![Performances de la base](../../assets/tools/observation-for-adobe-commerce/mysql-tab-8.jpg)

Le **[!UICONTROL Database performance]** cadre affiche les performances de la base de données lors de requêtes spécifiques. Vous pouvez afficher chaque mesure en cliquant dessus dans les icônes colorées situées sous le graphique. La plupart des mesures mentionnées dans [Surveillance des performances de la base de données MySQL avec New Relic](https://newrelic.com/blog/how-to-relic/how-to-monitor-mysql) se trouvent dans ce cadre.

* average(query.queryPerSecond)
* average(query.lentQueriesPerSecond)
* average(db.createdTmpDiskTablesPerSecond)
* average(db.createdTmpFilesPerSecond)
* average(db.tablesLocksWaitedPerSecond)
* average(db.innodb.rowLockTimeAvg)
* average(db.innodb.rowLockWaitsPerSecond)

## [!UICONTROL Transaction Database Call Count]

![Nombre d’appels de la base de données de transactions](../../assets/tools/observation-for-adobe-commerce/mysql-tab-9.jpg)

Le **[!UICONTROL Transaction Database Call Count]** frame indique le nombre d’appels de base de données effectués par chaque facette des transactions. Cela semble être axé sur les lignes et non sur les déclarations.

## [!UICONTROL Cron_schedule table updates]

![Mises à jour des tables Cron_schedule](../../assets/tools/observation-for-adobe-commerce/mysql-tab-10.jpg)

Le **[!UICONTROL Cron_schedule table updates]** frame affiche la durée maximale des mises à jour de la base de données dans la table cron_schedule pour la période sélectionnée.

## [!UICONTROL Slow Query Traces]

![Traces de requête lentes](../../assets/tools/observation-for-adobe-commerce/mysql-tab-11.jpg)

Le **[!UICONTROL Slow Query Traces]** frame affiche le tableau et le type de requête où il existe des traces de requête lentes. Une trace de requête lente est créée pour les transactions de requête qui prennent plus de cinq secondes. Les requêtes de mise à jour sont importantes pour ce cadre. Si un tableau est mis à jour par `UPDATE`, `DELETE`, et `INSERT` , ils peuvent verrouiller des tables pendant une période donnée.

Même `SELECT` Les instructions peuvent verrouiller des lignes si elles sont utilisées avec FOR UPDATE.

## [!UICONTROL Datastore Operations tables]

![Tables des opérations de banque de données](../../assets/tools/observation-for-adobe-commerce/mysql-tab-12.jpg)

## [!UICONTROL Cron table change]

![Modification de tableau Cron](../../assets/tools/observation-for-adobe-commerce/mysql-tab-13.jpg)

Le **[!UICONTROL Cron table change]** frame recherche les messages d’erreur &quot;impossible d’acquérir lock for cron job:&quot;, ainsi qu’une erreur de mémoire PHP spécifique et des verrous impliquant la tâche cron. `cron_schedule` table. Si la variable `cron_schedule` est verrouillée (par exemple, par un `DELETE` s’exécutant contre), elle bloquera l’exécution d’autres crons.

## [!UICONTROL Deadlocks]

![Deadlocks](../../assets/tools/observation-for-adobe-commerce/mysql-tab-14.jpg)

Le **[!UICONTROL Deadlocks]** frame examine les chaînes suivantes analysées à partir des journaux MySQL :

* &#39;%PHP Erreur fatale : Taille de mémoire autorisée de %&#39;) en tant que php_mem_error
* &#39;%get lock; essayer de redémarrer la transaction, la requête était : DELETE DE \`cron_schedule%&#39;) en tant que cron_sched_lock_del
* &#39;% lock pour la tâche cron : indexer_reindex_all_invalid%) comme &quot;lock_indexer_reindex_all_invalid%&quot;
* &#39;% lock pour la tâche cron : cron_schedule%) en tant que &quot;lock_cron_schedule&quot;
* &#39;% lock pour la tâche cron:%&#39;) comme &#39;total_cron_lock&#39;
* &#39;%General error: 1205 Délai d’attente de verrouillage dépassé%) en tant que &#39;sql_1205_lock&#39;
* ’%ERROR 1213 (40001) : Déverrouillage détecté lors de la tentative de verrouillage (%) en tant que &quot;sql_1213_lock&quot;
* &#39;%SQLSTATE[40001]: Échec de la sérialisation : 1213 Deadlock found%) as &#39;sql_1213_lock2&#39;
* &#39;% lock pour la tâche cron : indexer_update_all_views%) comme &quot;lock_indexer_update_all_views&quot;
* &#39;% lock pour la tâche cron : sales_grid_order_facture_async_insert%) en tant que &#39;lock_sales_grid_order_facture_async_insert&#39;,
* &#39;% lock pour la tâche cron : staging_remove_update%) en tant que &quot;lock_staging_remove_updated&quot;
* &#39;% lock pour la tâche cron : sales_grid_order_shipping_async_insert%) en tant que &quot;lock_sales_grid_order_shipping_async_insert&quot;
* &#39;% lock pour la tâche cron : amazon_payments_process_file_remboursements%) en tant que &quot;lock_amazon_payments_process_file_remboursements&quot;
* &#39;% lock pour la tâche cron : sales_send_order_shipping_emails%) en tant que &quot;lock_sales_send_order_shipping_emails&quot;
* &#39;% lock pour la tâche cron : staging_synchronize_entities_period%) en tant que &quot;lock_staging_synchronize_entities_period&quot;
* &#39;% lock pour la tâche cron : indexer_clean_all_changelogs%) en tant que &quot;lock_indexer_clean_all_changelogs&quot;
* &#39;% lock pour la tâche cron : magento_targetrule_index_reindex%) en tant que &quot;lock_magento_targetrule_index_reindex&quot;
* &#39;% lock pour la tâche cron : newsletter_send_all%) comme &quot;lock_newsletter_send_all&quot;
* &#39;% lock pour la tâche cron : newsletter_send_all%) comme &quot;lock_newsletter_send_all&quot;
* &#39;% lock pour la tâche cron : sales_send_order_emails%) en tant que &quot;lock_sales_send_order_emails&quot;
* &#39;% lock pour la tâche cron : sales_send_order_creditmemo_emails%) as &#39;lock_sales_send_order_creditmemo_emails&#39;
* &#39;% lock pour la tâche cron : sales_grid_order_creditmemo_async_insert%) en tant que &quot;lock_sales_grid_order_creditmemo_async_insert&quot;
* &#39;% lock pour la tâche cron : bulk_cleanup%) as &#39;lock_bulk_cleanup&#39;
* &#39;% lock pour la tâche cron : flush_preview_Quotas%) en tant que &quot;lock_flush_preview_Quotas&quot;
* &#39;% lock pour la tâche cron : sales_send_order_facture_emails%) en tant que &quot;lock_sales_send_order_factures_emails&quot;
* &#39;% lock pour la tâche cron : sales_send_order_facture_emails%) en tant que &quot;lock_sales_send_order_factures_emails&quot;
* &#39;% lock pour la tâche cron : captcha_delete_expirée_images%) en tant que &#39;lock_captcha_delete_expirée_images&#39;
* &#39;% lock pour la tâche cron : magento_newrelicreporting_cron%) en tant que &quot;lock_magento_newrelicreporting_cron&quot;
* &#39;% lock pour la tâche cron : obsolète_authentication_failures_cleanup%) en tant que &quot;lock_outdate_authentication_failures_cleanup&quot;
* &#39;% lock pour la tâche cron : send_notification%) comme &quot;lock_send_notification&quot;
* &#39;% lock pour la tâche cron : magento_giftcardaccount_generage_codes_pool%) en tant que &quot;lock_magento_giftcardaccount_generage_codes_pool&quot;
* &#39;% lock pour la tâche cron : catalog_product_frontend_actions_flush%) en tant que &quot;lock_catalog_product_frontend_actions_flush&quot;
* &#39;% lock pour la tâche cron : mysqlmq_clean_messages%) comme &quot;mysqlmq_clean_messages&quot;
* &#39;% lock pour la tâche cron : catalog_product_attribute_value_synchronize%) en tant que &quot;lock_catalog_product_attribute_synchronize&quot;
* &#39;% lock pour la tâche cron : ddg_automatisation_importer%) en tant que &quot;lock_ddg_automatisation_importer&quot;
* &#39;% lock pour la tâche cron : ddg_automatisation_review_and_vole_list%) en tant que &quot;lock_ddg_automatisation_review_and_vole_list&quot;
* &#39;% lock pour la tâche cron : captcha_delete_old_tries%) en tant que &#39;lock_captcha_delete_old_tries&#39;
* &#39;% lock pour la tâche cron : catalog_product_obsolète_price_values_cleanup%) en tant que &quot;lock_catalog_product_obsolète_price_values_cleanup&quot;
* &#39;% lock pour la tâche cron : consumer_runner%) en tant que &quot;lock_consumer_runner&quot;
* &#39;% lock pour la tâche cron : ddg_automatisation_customer_subscriber_guest_sync%) en tant que &quot;lock_ddg_automatisation_customer_subscriber_guest_sync&quot;
* &#39;% lock pour la tâche cron : get_amazon_capture_update%) en tant que &quot;lock_get_amazon_capture_update&quot;
* &#39;% lock pour la tâche cron : get_amazon_authorization_releases%) en tant que &quot;lock_send_get_amazon_authorization_releases&quot;
* &#39;% lock pour la tâche cron : temando_process_platform_events%) en tant que &quot;lock_temando_process_platform_events&quot;
* &#39;% lock pour la tâche cron : ddg_automatisation_status%) en tant que &quot;lock_ddg_automatisation_status&quot;
* &#39;% lock pour la tâche cron : ddg_automatisation_status%) en tant que &quot;lock_ddg_automatisation_status&quot;
* &#39;% lock pour la tâche cron : sales_clean_orders%) en tant que &quot;lock_sales_clean_orders&quot;
* &#39;% lock pour la tâche cron : catalog_index_refresh_price%) en tant que &quot;lock_catalog_index_refresh_price&quot;
* &#39;% lock pour la tâche cron : magento_récompense_balance_warning_notification%) en tant que &quot;lock_magento_react_balance_warning_notification&quot;
* &#39;% lock pour la tâche cron : analytics_update%) en tant que &quot;lock_analytics_update&quot;
* &#39;% lock pour la tâche cron : messagequeue_clean_outdate_locks%) en tant que &quot;lock_messagequeue_clean_outdate_locks&quot;
* &#39;% lock pour la tâche cron : messagequeue_clean_outdate_locks%) en tant que &quot;lock_messagequeue_clean_outdate_locks&quot;
* &#39;% lock pour la tâche cron : staging_apply_version%) en tant que &quot;lock_staging_apply_version&quot;
* &#39;% lock pour la tâche cron : magento_récompense_expire_points%) en tant que &quot;lock_magento_récompento_expire_points&quot;
* &#39;% lock pour la tâche cron : yotpo_yotpo_orders_sync%) en tant que &quot;lock_yotpo_orders_sync&quot;
* &#39;% lock pour la tâche cron : catalog_event_status_checker%) en tant que &quot;lock_catalog_event_status_checker&quot;
* &#39;% lock pour la tâche cron : ddg_automatisation_campaign%) en tant que &quot;lock_ddg_automatisation_campaign&quot;
* &#39;% lock pour la tâche cron : visitor_clean%) comme &quot;lock_visitor_clean&quot;
* &#39;% lock pour la tâche cron : scconnector_verify_website%) en tant que &#39;lock_connector_verify_website&#39;
* &#39;% lock pour la tâche cron : ddg_automatisation_email_templates%) en tant que &quot;lock_ddg_automatisation_email_templates&quot;
* &#39;% lock pour la tâche cron : aggregate_sales_report_order_data%) en tant que &quot;lock_aggregate_sales_report_order_data&quot;
* &#39;% lock pour la tâche cron : ddg_automatisation_catalog_sync%) en tant que &quot;lock_ddg_automatisation&quot;

## [!UICONTROL DB Statistics]

![Statistiques DB](../../assets/tools/observation-for-adobe-commerce/mysql-tab-15.jpg)

Le **[!UICONTROL DB Statistics]** frame affiche des suppressions, écritures, lignes lues, mises à jour et requêtes lentes par seconde.

## [!UICONTROL Request frequency]

![Fréquence des demandes](../../assets/tools/observation-for-adobe-commerce/mysql-tab-16.jpg)

## [!UICONTROL Database Errors]

![Erreurs de base de données](../../assets/tools/observation-for-adobe-commerce/mysql-tab-17.jpg)

Le **[!UICONTROL Database Errors]** cadre affiche une grande variété de base de données [avertissements et erreurs](https://mariadb.com/kb/en/mariadb-error-codes/):

* La taille de mémoire allouée à la table temporaire est de plus de 20 % de innodb_buffer_pool_size% en tant que &#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%) as &#39;rbr_write_fail&#39;
* &#39;%mysqld: Disk full%) as &#39;disk_full&#39;
* &quot;%Error number 28%&quot;) as &#39;err_28&#39;
* &quot;%rollback%&quot;) comme &quot;rollback&quot;
* &quot;%Contrainte de clé étrangère échoue pour table%&quot;) en tant que &quot;contrainte_clé_étrangère&quot;
* ’%Error_code: 1114%) comme &quot;sql_1114_full&quot;%CRITICAL : SQLSTATE[HY000] [2006] Le serveur MySQL a disparu&quot;) comme &quot;sql_gone&quot;
* &#39;%SQLSTATE[HY000] [1040] Trop de connexions%) comme &#39;sql_1040&#39;
* &#39;%CRITICAL: SQLSTATE[HY000] [2002]%&#39;) comme &quot;sql_2002&quot;
* &#39;%SQLSTATE[08S01]:%) comme &quot;sql_1047&quot;
* &#39;%[Avertissement] Abandon de la connexion%) en tant que &quot;aborted_conn&quot;
* &#39;%SQLSTATE[23 000]: Violation de contrainte d’intégrité :%) en tant que &quot;sql_23000&quot;
* &quot;%1205 Verrouillage Délai d’attente d’attente %&quot;) en tant que &quot;sql_1205&quot;
* &#39;%SQLSTATE[HY000] [1049] Base de données inconnue%) en tant que &#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02]: Table ou vue de base introuvable :%) en tant que &#39;sql_42S02&#39;
* &#39;%General error: 1114%) en tant que &#39;sql_1114&#39;
* &#39;%SQLSTATE[40001]%&#39;) comme &quot;sql_1213&quot;
* &#39;%SQLSTATE[42S22]: Colonne introuvable : 1054 Unknown column%) as &#39;sq1_1054&#39;
* &#39;%SQLSTATE[42000]: Erreur de syntaxe ou violation d’accès :%&#39;) as&#39;sql_42000&#39;
* &#39;%SQLSTATE[21 000]: Violation de cardinalité :%) comme &#39;sql_1241&#39;
* &#39;%SQLSTATE[2003]:%) comme &quot;sql_22003&quot;
* &#39;%SQLSTATE[HY000] [9 000] Client avec l’adresse IP%) comme &quot;sql_9000&quot;
* &#39;%SQLSTATE[HY000]: Erreur générale : 2014%) en tant que &quot;sql_2014&quot;
* &quot;%1927 La connexion a été tuée%&quot;) en tant que &quot;sql_1927&quot;
* &#39;%1062 \[ERROR\] InnoDB:%&#39;) en tant que &#39;sql_1062_e&#39;
* &#39;&#39;%[Remarque] WSREP : Purge de la carte mémoire sur le disque...%) comme &quot;mem_map_flush&quot;
* Code d’erreur ‘%Internal MariaDB : 1146%) en tant que &#39;sql_1146&#39;
* Code d’erreur ‘%Internal MariaDB : 1062%) comme &quot;sql_1062&quot; * ’%1062 [Avertissement] InnoDB:%) en tant que &#39;sql_1062_w&#39;
* Code d’erreur ‘%Internal MariaDB : 1064%) comme &quot;sql_1064&quot;
* ’%InnoDB: Échec de l’affirmation dans le fichier%) en tant que &quot;assertion_err&quot;
* ’%mysqld_safe Nombre de processus en cours d’exécution : 0%) comme &quot;mysql_oom&quot;
* &#39;%\[ERROR\] mysqld a reçu signal%&#39;) comme &#39;mysql_sigterm&#39;
* &quot;%1452 Impossible d’ajouter%&quot;) en tant que &quot;sql_1452&quot;
* &#39;%ERROR 1698%&#39;) en tant que &#39;sql_1698&#39;
* &#39;%SQLSTATE[HY000]: Erreur générale : 3 %) comme &quot;cnt_write_tmp&quot;
* &#39;%General error: 1 %&#39;) comme &#39;sql_syntaxe&#39;
* &#39;%42S22%&#39;) en tant que &#39;sql_42S22&#39;
* ’%InnoDB: Erreur (clé en double)%) en tant que ’innodb_dup_key’ DES HORODATAGES DU journal

## [!UICONTROL DB Error Table]

![Tableau d’erreurs DB](../../assets/tools/observation-for-adobe-commerce/mysql-tab-18.jpg)

Le **[!UICONTROL DB Error Table]** Le cadre affiche les mêmes informations que le **[!UICONTROL Database Errors]** , mais vous pouvez le voir par noeud et dans un format de tableau. Voir [Codes d’erreur MariaDB](https://mariadb.com/kb/en/mariadb-error-codes/) pour plus d’informations.

## [!UICONTROL Database Traces]

![Traces de base de données](../../assets/tools/observation-for-adobe-commerce/mysql-tab-19.jpg)

Le **[!UICONTROL Database Traces]** affiche les traces de la base de données par type dans la chronologie sélectionnée.

## [!UICONTROL Database processes]

![Processus de base de données](../../assets/tools/observation-for-adobe-commerce/mysql-tab-20.jpg)

Le **[!UICONTROL Database processes]** frame affiche les processus de base de données, les environnements et les identifiants de noeud.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![Threads non dormantes MySQL par noeud](../../assets/tools/observation-for-adobe-commerce/mysql-tab-21.jpg)

Le **[!UICONTROL MySQL Non-Sleeping Threads by Node]** Le cadre affiche les threads de connexion à la base de données. Ce cadre affiche les principaux threads.

## [!UICONTROL MySQL Running and Sleeping Threads by environment]

![Exécution et dormage de MySQL par environnement](../../assets/tools/observation-for-adobe-commerce/mysql-tab-22.jpg)

Le **[!UICONTROL MySQL Running and Sleeping Threads by environment]** frame affiche les connexions principales et endormies à la base de données. S&#39;il y a des connexions à la base de données où des requêtes lentes sont mises en veille, il y aura des connexions de sommeil. Les connexions persistantes peuvent être des requêtes de base de données bloquées par des lignes ou des tables verrouillées. Ces connexions endormies maintiennent aussi des connexions de travail PHP.

## [!UICONTROL MySQL mem used by node]

![Mem MySQL utilisé par le noeud](../../assets/tools/observation-for-adobe-commerce/mysql-tab-23.jpg)

Le **[!UICONTROL MySQL mem used by node]** frame affiche l’utilisation de la mémoire par les noeuds par MySQL. Sur les sites plus volumineux, cette image peut être composée de barres continues avec une valeur en Go de mémoire utilisée.

## [!UICONTROL Database mysql-slow.log]

![Base de données mysql-lent.log](../../assets/tools/observation-for-adobe-commerce/mysql-tab-24.jpg)

Le **[!UICONTROL Database mysql-slow.log]** Le cadre affiche les types d’instructions de requête qui se trouvaient dans la variable `mysql-slow.log` sur la période sélectionnée.
