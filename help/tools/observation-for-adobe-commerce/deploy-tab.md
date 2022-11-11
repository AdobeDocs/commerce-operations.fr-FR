---
title: "Le [!UICONTROL Deploy] tab"
description: En savoir plus sur les [!UICONTROL Deploy] de [!DNL Observation for Adobe Commerce].
source-git-commit: b95a35ee64cd8e844a51a9ff699eceb9c3a9266c
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 0%

---

# Le [!UICONTROL Deploy] tab

Cet onglet permet d’isoler rapidement les problèmes et les causes des problèmes de déploiement.

## [!UICONTROL Deploy log Deployment Troubleshooter]

![Déployer l’outil de dépannage du déploiement des journaux](../../assets/tools/observation-for-adobe-commerce/deploy-tab-1.jpg)

Le **[!UICONTROL Deploy log Deployment Troubleshooter]** affiche le nombre d’événements de journal de déploiement qui se sont produits au cours de la période sélectionnée. L’objectif est de fournir une vue d’ensemble de l’activité de déploiement et de déterminer la complexité du déploiement en fonction du nombre. Plus le nombre de messages consignés est élevé, plus le déploiement est complexe.

## [!UICONTROL Deploy State]

![État du déploiement](../../assets/tools/observation-for-adobe-commerce/deploy-tab-2.jpg)

Le **[!UICONTROL Deploy State]** cadre affiche les événements de déploiement qui se sont produits au cours de la période sélectionnée. L’analyseur de ce cadre recherche ces signaux spécifiques :

* &#39;%REMARQUE : Démarrage de generate command%) en tant que &#39;start_gen&#39;
* &quot;%git apply /app/vendor/magento/ece-tools/Correctifs%&quot;) as &#39;apply_Correctifs&#39;
* &#39;%Set flag : .static_content_deploy%) comme &quot;SCD&quot;
* &#39;%REMARQUE : Générer la commande completed%) en tant que &#39;gen_compl&#39;
* &#39;%REMARQUE : Démarrage du déploiement.%&#39;) comme &quot;start_deploy&quot;
* &#39;%REMARQUE : Déploiement terminé&quot;) comme &quot;deploy_compl&quot;
* &#39;%REMARQUE : Démarrage après le déploiement.%&#39;) comme &quot;start_pdeploy&quot;
* &#39;%REMARQUE : Le post-déploiement est terminé en %) comme &quot;déploiement&quot;
* &#39;%deploy-complete%&#39;) comme &#39;cl_deploy_compl&#39;

## [!UICONTROL Deploy Log Detail]

![Déployer les détails du journal](../../assets/tools/observation-for-adobe-commerce/deploy-tab-3.jpg)

Le **[!UICONTROL Deploy Log Detail]** cadre affiche les détails du résumé du message du journal de déploiement qui se sont produits au cours de la période sélectionnée. Le cadre analyse les chaînes suivantes dans les journaux de déploiement :

* &#39;%REMARQUE : Démarrage du déploiement.%&#39;) comme &quot;start_ply&quot;
* &#39;%INFO : Scénarios de démarrage : scenario/deploy.xml%) comme &quot;start_scénario&quot;
* &#39;%REMARQUE : Démarrage de pre-deploy%) en tant que &quot;start_predply&quot;
* &#39;% INFO : Restauration du fichier journal des correctifs (%) en tant que &quot;rstr_ptch_log&quot;
* &#39;%INFO : Mise à jour de la configuration du cache.%&#39;) comme &quot;updt_cach_config&quot;
* &#39;%INFO : Définissez Redis Secondaire connection%) comme &quot;redis_sec_conn_set&quot;
* &#39;%INFO : Le déploiement de contenu statique a été effectué pendant le crochet de génération, en nettoyant l’ancien contenu (&quot;scd_build_hk&quot;).
* &#39;%INFO : Effacement de pub/static%) en &quot;clr_pub_static&quot;
* &#39;%NFO : Effacement du cache des redis :%) en tant que &#39;clr_redis_cach&#39;
* &#39;%INFO : Effacement de var/cache directory%) en tant que &#39;clr_var_cach&#39;
* &#39;% AVIS : Activation du mode de maintenance%) comme &quot;enable_maint_mode&quot;
* &#39;%INFO : Désactiver cron%) comme &quot;disable_cron&quot;
* &#39;%INFO : Tentative de suppression des tâches cron en cours d’exécution et des processus des consommateurs (%) en tant que &quot;kill_cron_try&quot;
* &#39;%INFO : Les processus cron et consommateurs Magento en cours d’exécution sont introuvables.%&#39;) comme &#39;no_cron_fnd&#39;,
* %REMARQUE : Validation de la configuration%) en tant que &quot;validate_config&quot;
* &quot;%Les données d’administration suivantes sont requises pour créer un utilisateur administrateur lors de l’installation initiale&quot;) en tant que &quot;no_admin&quot;
* &quot;%version PHP recommandée satisfaisant la contrainte%&quot;) en tant que &quot;php_ver_constraint&quot;
* &#39;%WARNING: Correction de la configuration avec les suggestions données :%) comme &quot;fix_config_sugg&quot;
* &#39;%WARNING: [2003] La valeur de niveau d’imbrication de répertoire pour les rapports d’erreur n’a pas été configurée.%&#39;) as&#39;nest_err_reporting&#39;
* &#39;%REMARQUE : Fin de validation%) comme &quot;end_validation&quot;
* &#39;%REMARQUE : Démarrage de la mise à jour.%&#39;) comme &quot;start_update&quot;
* &#39;%INFO : Mise à jour de env.php.%&#39;) comme &quot;update_php_env&quot;
* &#39;%INFO : Mise à jour de la configuration de la connexion env.php DB.%&#39;) comme &quot;update_php_env_db&quot;
* &#39;%INFO : Mise à jour de la configuration AMQP env.php%) en tant que &quot;update_php_env_amqp&quot;
* &#39;%INFO : Définissez le moteur de recherche sur : élasticsearch7%) comme &quot;set_élastique7&quot;
* &quot;%élasticsearch 6.5.4 a dépassé EOL%&quot;) comme &quot;élastique_ver_EOL&quot;
* &#39;%INFO : Définissez le moteur de recherche sur : élasticsearch6%) comme &quot;set_élastique6&quot;
* &#39;%INFO : Mise à jour des URL sécurisées et non sécurisées (%) en tant que &quot;update_urls&quot;
* &#39;%INFO : Exécution de la mise à niveau de la configuration.%&#39;) comme &quot;setup_upgrade_run&quot;
* &#39;%INFO : crochet de postdéploiement activé. L’activation du cron, le nettoyage du cache et les opérations avant-guerre sont reportées%) en tant que &quot;post_hook_enabled&quot;
* &#39;%REMARQUE : Le mode de maintenance est désactivé.%) comme &quot;maint_mode_disabled&quot;
* &#39;%INFO : Scénario(s terminé(s)%) comme &quot;scénario_terminé&quot;
* &#39;%WARNING: Maintenance des commandes : l’activation s’est terminée avec une erreur. Création d’un fichier maintenanceflag (%) comme &#39;enable_maintenance_fail&#39;
* &quot;%Le serveur MySQL a disparu%&quot;) comme &quot;MySQL_has_gone_away&quot;

## [!UICONTROL Post Deploy Log Detail]

![Détails du journal de déploiement des publications](../../assets/tools/observation-for-adobe-commerce/deploy-tab-4.jpg)

Le **[!UICONTROL Post Deploy Log Detail]** Le cadre affiche les détails du journal de post-déploiement qui se sont produits au cours de la période sélectionnée. Ce cadre est axé sur des messages de journal spécifiques qui contiennent les chaînes suivantes :

* &#39;%Mode de maintenance désactivé%&#39;) comme &#39;disabled_maint_mode&#39;
* &#39;%INFO : Scénarios de démarrage : scenario/post-deploy.xml%) comme &quot;start_pstdply_scénario&quot;
* &#39;% AVIS : Validation de la configuration%) en tant que &quot;val_config&quot;
* &#39;% AVIS : Fin de validation%) comme &quot;end_val_config&quot;
* &#39;%INFO : Activer cron%) comme &quot;cron_enabled&quot;
* &#39;% INFO : Créez une sauvegarde des fichiers importants.%&#39;) comme &quot;file_backup&quot;
* &#39;%INFO : Création réussie de la sauvegarde (%) en tant que &quot;file_backup_success&quot;
* &#39;%INFO : Démarrage de la page se réchauffant %) en tant que &quot;pg_chauffup_start&quot;
* &#39;%INFO : Page réchauffée :%) en tant que &#39;warming_up_pg&#39;
* ’%ERROR: Échec du réveil :%) en tant que &#39;réchauffé_up_pg_err&#39;
* &#39;% INFO : Scénario(s terminé(s)%) comme &quot;scénario_terminé&quot;

## [!UICONTROL Cloud Log Detail]

![Détails du journal cloud](../../assets/tools/observation-for-adobe-commerce/deploy-tab-5.jpg)

Le **[!UICONTROL Cloud Log Detail]** image affiche les détails du journal cloud qui se sont produits au cours de la période sélectionnée. Les chaînes suivantes sont analysées et renvoyées avec l’étiquette &quot;AS&quot; ci-dessous :

* ’%DEBUG: /bin/bash -c &quot;set -o pipefail; php ./bin/magento setup:upgrade%) en tant que &#39;start_update&#39;
* &#39;%Création/mises à jour de schéma :%&#39;) comme &#39;mises à jour_de_schéma&#39;
* &#39;%Rien à importer.%&#39;) comme &quot;mod_import_end&quot;
* &#39;%REMARQUE : Fin de la mise à jour.%&#39;) comme &quot;update_finished&quot;
* ’%DEBUG: Étape en cours d’exécution : deploy-static-content%) comme &quot;scd_run&quot;
* &#39;% AVIS : Ignorer le déploiement de contenu statique. SCD à la demande est activé.%&#39;) comme &quot;scd_ondemand&quot;
* &#39;%INFO : Clearing%&#39;) as&#39;clr_dirs&#39;
* ’%DEBUG: Étape &quot;deploy-static-content finished%&quot;) comme &quot;scd_finished&quot;
* &#39;%REMARQUE : Ignorer la compression de contenu statique. SCD à la demande est activé.%&#39;) comme &quot;scd_compression_run&quot;,
* &#39;%INFO : Effacement de var/cache directory%) en tant que &#39;clr_var_cach&#39;
* ’%DEBUG: Étape &quot;compress-static-content finished%&quot;) comme &quot;scd_compression_finished&quot;
* ’%DEBUG: Étape en cours d’exécution : deploy-complete%) comme &quot;deploy_finished&quot;
* &#39;%INFO : crochet de postdéploiement activé. L’activation du cron, le nettoyage du cache et les opérations de préréchauffement sont reportés à l’étape de post-déploiement.%&#39;) comme &quot;Post_deploy_hook_enabled&quot;
* &#39;%REMARQUE : Le mode de maintenance est désactivé.%) comme &quot;maint_mode_disabled&quot;
* &#39;%INFO : Scénario(s terminé(s)%) comme &quot;scénario_terminé&quot;
* &#39;%post-deploy.xml%&#39;) en tant que &#39;post_deploy_start&#39;
* &#39;%REMARQUE : Validation de la configuration%) en tant que &quot;validate_config&quot;
* &#39;%WARNING: [2003] La valeur de niveau d’imbrication de répertoire pour les rapports d’erreur n’a pas été configurée.%&#39;) as&#39;nest_err_reporting&#39;
* &#39;%REMARQUE : Fin de validation%) comme &quot;end_validation&quot;
* &#39;%INFO : Activer cron%) comme &quot;enable_cron&quot;
* &#39;%INFO : Créer une sauvegarde des fichiers importants (%) en tant que &quot;create_backup&quot;
* ’%DEBUG: Étape &quot;sauvegarde&quot; terminée%) comme &quot;sauvegarde_terminée&quot;
* &#39;%INFO : Démarrage de la page se réchauffant (%) en tant que &quot;chauffe_démarrer&quot;
* ’%ERROR: Échec du réveil :%) en tant que &#39;réchauffé_up_fail&#39;
* ’%DEBUG: Étape &quot;chauffement&quot; terminé%) comme &quot;chauffe-air_terminé&quot;
* &#39;% DEBUG: Étape &quot;time-to-first-byte finished%&quot;) en tant que &quot;ttfb_finished&quot;
* &#39;%INFO : Scénario(s terminés%) en tant que &quot;post_deploy_finished&quot;
* ’%DEBUG: Étape en cours d’exécution : pre-build%) comme &quot;run_pre-build&quot;
* ’%DEBUG: Flag.static_content_deploy a déjà été supprimé%) en &quot;scd_flag_del&quot;
* ’%DEBUG: Étape &quot;pré-build&quot; terminée%&quot;) comme &quot;pre-build_completed&quot;
* &#39;%REMARQUE : Appliquer les correctifs%) comme &quot;apply_patches&quot;
* &quot;%a été appliqué%&quot;) comme &quot;Correctifs_appliqués&quot;
* ’%DEBUG: Étape &quot;apply-patches terminé%&quot;) comme &quot;apply_patches_complete&quot;
* &quot;%Deploy using quick strategy%&quot;) en tant que &quot;quick_strategy_deploy&quot;
* &#39;% AVIS : Exécution de la compilation ID%) comme &quot;di_compliation_start&quot;
* &#39;%REMARQUE : Fin de l’exécution de la compilation ID%) en tant que &quot;di_compliation_finished&quot;
* &#39;%REMARQUE : Générer du contenu statique neuf %) en tant que &quot;gen_frsh_static_content&quot;
* Configuration de ’%magento:static-content:deploy%) comme &quot;scd_execution&quot;
* &#39;%REMARQUE : Fin de la génération du contenu statique neuf %) en tant que &quot;gen_frsh_static_cont_finished&quot;
* &#39;%INFO : Scénarios de démarrage : scenario/build/transfer.xml%) comme &quot;start_transfer xml&quot;
* &#39;%INFO : Tenter de tuer les tâches cron en cours d&#39;exécution (%) en tant que &quot;kill_crons&quot;
* &#39;%INFO : Effacement du cache des redis :%) en tant que &#39;clear_redis_cache&#39;
* &#39;%INFO : Vérification de l’existence de la base de données et de la présence des tables (%) en tant que &quot;db_check&quot;
* &#39;%WARNING: [2010] Le service Elasticsearch est installé sur la couche d’infrastructure, mais n’est pas utilisé comme moteur de recherche.%&#39;) as&#39;es_not_used&#39;
* &#39;%REMARQUE : Démarrage de la mise à jour.%&#39;) comme &quot;starting_update&quot;
* &#39;%INFO : Définissez le moteur de recherche sur : mysql%) comme &quot;mysql_search&quot;
* &#39;%SQLSTATE[HY000] [2006] Le serveur MySQL a disparu&quot;) en tant que &quot;mysql_gone&quot;

## [!UICONTROL Count of modules imported during deploy]

![Nombre de modules importés pendant le déploiement](../../assets/tools/observation-for-adobe-commerce/deploy-tab-6.jpg)

Le **[!UICONTROL Count of modules imported during deploy]** cadre indique le nombre de modules importés au cours du déploiement sur la période sélectionnée.

## [!UICONTROL Deployed module list]

![Liste des modules déployés](../../assets/tools/observation-for-adobe-commerce/deploy-tab-7.jpg)

Le **[!UICONTROL Deployed module list]** cadre affiche les modules déployés pendant la période sélectionnée.

