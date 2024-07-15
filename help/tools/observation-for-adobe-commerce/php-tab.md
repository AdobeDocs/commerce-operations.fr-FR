---
title: Onglet [!UICONTROL PHP]
description: Découvrez l’onglet [!UICONTROL PHP] de [!DNL Observation for Adobe Commerce].
exl-id: 0989a7f5-75b0-4fb5-ac5e-2618603bf548
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Onglet [!UICONTROL PHP]

L’onglet **PHP** présente les problèmes de processus PHP afin de fournir une analyse plus approfondie des problèmes PHP.

## [!UICONTROL PHP active process details]

![Détails du processus actif PHP](../../assets/tools/php-active-process-details.jpg)

L’image **[!UICONTROL PHP active process details]** montre les processus PHP, y compris php-fpm, pendant la période sélectionnée.

## [!UICONTROL PHP process load (# of PHP processes and % of CPU load)]

![Charge du processus PHP](../../assets/tools/php-process-load.jpg)

L’image **[!UICONTROL PHP process load (# of PHP processes and % of CPU load)]** montre la charge du processeur des processus PHP-FPM pendant la période sélectionnée.

## [!UICONTROL PHP Memory detail]

![Détails de mémoire PHP](../../assets/tools/php-memory-detail.jpg)

L’image **[!UICONTROL PHP Memory detail]** montre l’utilisation de la mémoire des processus PHP pendant la période sélectionnée.

## [!UICONTROL PHP CPU Utilization]

![Utilisation de l’unité centrale PHP](../../assets/tools/php-cpu-utilization.jpg)

L’image **[!UICONTROL PHP CPU Utilization]** indique le pourcentage d’utilisation du processeur des processus PHP sur la période sélectionnée.

## [!UICONTROL PHP Process states]

![État du processus PHP](../../assets/tools/php-process-states-image-1.jpg)

L’image **[!UICONTROL PHP Process states]** présente les états du processus PHP sur la période sélectionnée. Il s’affiche lorsque les processus PHP s’arrêtent et redémarrent. Attention aux processus PHP terminés qui n’affichent pas de redémarrages.

* &#39;%NOTICE : Arrêt de ...%&#39;) en tant que &#39;terme_php&#39;
* &#39;% AVERTISSEMENT : quitte, bye-bye !%&#39;) comme &quot;php_exit&quot;
* &#39;% AVERTISSEMENT : fpm is running, pid%&#39;) as &#39;fpm_start&#39;
* &#39;%NOTICE : prêt à gérer les connexions%&#39;) comme &#39;php_ready&#39;

## [!UICONTROL PHP Errors]

![Erreurs PHP](../../assets/tools/php-errors-image-1.jpg)

L’image **[!UICONTROL PHP Errors]** indique le nombre d’erreurs de programme de travail PHP pendant la période sélectionnée. Les messages d’erreur analysés et affichés sont les suivants :

* &#39;%worker_connections n’est pas suffisant%&#39;) comme &#39;worker&#39;
* &#39;%PHP Erreur fatale : taille de la mémoire autorisée !%&#39;) comme &quot;mem_size&quot;
* &#39;%exited sur le signal 11 (SIGSEGV)%&#39;) en tant que &#39;sig_11&#39;
* &#39;%exited sur le signal 7 (SIGBUS%&#39;) en tant que &#39;sig_7&#39;
* &#39;%augmentation pm.start_servers%&#39;) en tant que &#39;pmstart_Servan&#39;
* &#39;%max_children%&#39;) comme &#39;max_children_cnt&#39;
* &quot;%PHP Erreur fatale : taille de mémoire autorisée de %&quot;) comme &quot;mem_exhst_coun&quot;
* &quot;%Impossible d’allouer de la mémoire pour pool%&quot;) en tant que &quot;opc_mem_count&quot;
* &#39;%Warning Interned string buffer overflow%&#39;) as &#39;opc_str_buf&#39;
* &#39;%Chaîne non autorisée offsetl%&#39;) comme &#39;opc_sv_comments&#39;
* &#39;%PHP Erreur fatale : RedisException non interceptée : erreur de lecture sur la connexion%&#39;) en tant que &#39;php_exc&#39;

## [!UICONTROL PHP processes count]

![Nombre de processus PHP](../../assets/tools/php-processes-count.jpg)

L’image **[!UICONTROL PHP processes count]** présente un nombre de processus PHP sur la période sélectionnée.

## [!UICONTROL Database Errors]

![Erreurs de base de données](../../assets/tools/php-tab-database-errors.jpg)

L’image **[!UICONTROL Database Errors]** affiche des erreurs de base de données pendant la période sélectionnée. Erreurs analysées :

* &quot;%Taille de mémoire allouée à la table temporaire est supérieure à 20 % de innodb_buffer_pool_size%&quot;) en tant que &quot;temp_tbl_buff_pool&quot;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) comme &#39;rbr_write_fail&#39;
* &#39;%mysqld : disque plein%&#39;) comme &#39;disque_plein&#39;
* &quot;%Error number 28%&quot;) as &#39;err_28&#39;
* &quot;%rollback%&quot;) comme &quot;rollback&quot;
* &quot;%Contrainte de clé étrangère échoue pour table%&quot;) en tant que &quot;contrainte_clé_étrangère&quot;
* &#39;%Error_code: 114%&#39;) as &#39;sql_1114_full&#39;
* &#39;%CRITICAL : SQLSTATE[HY00] [2006] Le serveur MySQL a disparu%&#39;) comme &#39;sql_gone&#39;
* &#39;%SQLSTATE[HY00] [1040] Trop de connexions%&#39;) comme &#39;sql_1040&#39;
* &#39;%CRITICAL : SQLSTATE[HY00] [2002]%&#39;) en tant que &#39;sql_2002&#39;
* &#39;%SQLSTATE[08S01]:%&#39;) en tant que &#39;sql_1047&#39;
* &#39;%[Avertissement] Connexion abandonnée%&#39;) en tant que &#39;aborted_conn&#39;
* &#39;%SQLSTATE[23000] : violation de contrainte d’intégrité :%&#39;) en tant que &#39;sql_23000&#39;
* &quot;%1205 Verrouillage Délai d’attente d’attente %&quot;) en tant que &quot;sql_1205&quot;
* &#39;%SQLSTATE[HY00] [1049] Base de données inconnue%&#39;) en tant que &#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02] : table ou vue de base introuvable :%&#39;) en tant que &#39;sql_42S02&#39;
* &#39;%Erreur générale : 114%&#39;) en tant que &#39;sql_1114&#39;
* &#39;%SQLSTATE[4001]%&#39;) en tant que &#39;sql_1213&#39;
* &#39;%SQLSTATE[42S22] : Colonne introuvable : 1054 Unknown column%&#39;) en tant que &#39;sq1_1054&#39;
* &#39;%SQLSTATE[42000] : Erreur de syntaxe ou violation d’accès :%&#39;) en tant que &#39;sql_42000&#39;
* &#39;%SQLSTATE[21000] : violation de cardinalité :%&#39;) en tant que &#39;sql_1241&#39;
* &#39;%SQLSTATE[22003]:%&#39;) en tant que &#39;sql_22003&#39;
* &#39;%SQLSTATE[HY00] [9000] Client avec adresse IP%&#39;) en tant que &#39;sql_9000&#39;
* &#39;%SQLSTATE[HY00] : Erreur générale : 2014%&#39;) en tant que &#39;sql_2014&#39;
* &quot;%1927 La connexion a été tuée%&quot;) en tant que &quot;sql_1927&quot;
* &#39;%1062 \[ERROR\] InnoDB:%&#39;) en tant que &#39;sql_1062_e&#39;
* &#39;%[Remarque] WSREP : vidage de la carte mémoire sur le disque..%&#39;) comme &#39;mem_map_flush&#39;
* &#39;%Code d’erreur interne MariaDB : 1146%&#39;) en tant que &#39;sql_1146&#39;
* &#39;%Code d’erreur interne MariaDB : 1062%&#39;) comme &#39;sql_1062&#39; * &#39;%1062 [Warning] InnoDB:%&#39;) comme &#39;sql_1062_w&#39;
* &#39;%Code d’erreur interne MariaDB : 1064%&#39;) en tant que &#39;sql_1064&#39;
* &#39;%InnoDB : échec de l’affirmation dans le fichier%&#39;) en tant que &#39;assertion_err&#39;
* &#39;%mysqld_safe Nombre de processus en cours d’exécution : 0 %&#39;) en tant que &#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld a reçu signal%&#39;) comme &#39;mysql_sigterm&#39;
* &quot;%1452 Impossible d’ajouter%&quot;) comme &quot;sql_1452&quot;
* &#39;%ERROR 1698%&#39;) en tant que &#39;sql_1698&#39;
* &#39;%SQLSTATE[HY000] : Erreur générale : 3%&#39;) en tant que &#39;cnt_write_tmp&#39;
* &#39;%Erreur générale : 1 %&#39;) en tant que &#39;sql_syntaxe&#39;
* &#39;%42S22%&#39;) en tant que &#39;sql_42S22&#39;
* &#39;%InnoDB : erreur (clé en double)%&#39;) en tant que &#39;innodb_dup_key&#39;

## [!UICONTROL Database traces]

![trace de base de données](../../assets/tools/php-tab-database-traces.jpg)

L’image **[!UICONTROL Database traces]** affiche les informations de suivi de la base de données. Ce cadre s’aligne sur la vue Synthèse des transactions de l’APM pour la chronologie sélectionnée.

## [!UICONTROL Database mysql-slow.log]

![ Base de données mysql-lent.log](../../assets/tools/php-tab-database-mysql-slow-log.jpg)

L’image **[!UICONTROL Database mysql-slow.log]** affiche les types d’instructions de requête qui se trouvaient dans le fichier `mysql-slow.log` au cours de la période sélectionnée.
