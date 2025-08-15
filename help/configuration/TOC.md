---
user-guide-title: Guide de configuration
user-guide-description: Configurez les fonctionnalités et services de votre application Adobe Commerce.
feature: Configuration
source-git-commit: 1850301e0b7f1abbc54613209940dd63d16ef145
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 1%

---


# Guide de configuration {#configuration-guide}

+ [Vue d’ensemble](overview.md)
+ Configuration générale {#setup}
   + [Initialisation et amorçage de l&#39;application](bootstrap/initialization.md)
   + [Modes d’application](bootstrap/application-modes.md)
   + [Paramètres de Bootstrap](bootstrap/set-parameters.md)
   + [Profilage](bootstrap/mage-profiler.md)
   + [Chemins d’accès aux répertoires de base](bootstrap/mage-directory.md)
+ Déploiement {#deployment}
   + [Présentation du déploiement](deployment/overview.md)
   + [Déploiement sur un seul ordinateur](deployment/single-machine.md)
   + [Déploiement du pipeline](deployment/technical-details.md)
   + [Conditions préalables](deployment/prerequisites.md)
   + [Configuration du système de développement](deployment/development-system.md)
   + [Configuration du système de build](deployment/build-system.md)
   + [Configuration du système de production](deployment/production-system.md)
   + [Autorisations d’accès aux systèmes de fichiers](deployment/file-system-permissions.md)
   + Exemples {#examples}
      + [Utilisation d’une configuration partagée](deployment/example-shared-configuration.md)
      + [Utilisation des commandes de l’interface de ligne de commande](deployment/example-using-cli.md)
      + [Utilisation de variables d’environnement](deployment/example-environment-variables.md)
+ Cache {#cache}
   + [Présentation de la mise en cache](cache/caching-overview.md)
   + [Types de cache](cache/cache-types.md)
   + [Options de cache](cache/cache-options.md)
   + [Cache L2](cache/level-two-cache.md)
   + Redis {#redis}
      + [Configurer Redis](cache/config-redis.md)
      + [Utiliser Redis pour le cache par défaut](cache/redis-pg-cache.md)
      + [Utilisation de Redis pour le stockage de session](cache/redis-session.md)
   + Valkey {#valkey}
      + [Configurer Valkey](cache/config-valkey.md)
      + [Utiliser Valkey pour le cache par défaut](cache/valkey-pg-cache.md)
      + [Utiliser Valkey pour le stockage de session](cache/valkey-session.md)
   + Vernis {#varnish}
      + [Présentation du vernis](cache/config-varnish.md)
      + [Installer le vernis](cache/config-varnish-install.md)
   + [Serveur Web](cache/config-varnish-server.md)
   + [Configuration de l’application Commerce](cache/configure-varnish-commerce.md)
   + [Configuration avancée du vernis](cache/config-varnish-advanced.md)
   + [Effacement du cache](cache/use-varnish-cache.md)
   + [Effacement du cache de plusieurs instances Varnish](cache/use-multiple-varnish-cache.md)
   + [Vérifier la configuration du vernis](cache/config-varnish-final.md)
   + [Bloc d&#39;ESI vernis](cache/use-varnish-esi.md)
   + [Cache de contenu statique](cache/static-content-signing.md)
+ Ligne de commande {#cli}
   + [Outil de ligne de commande](cli/config-cli.md)
   + [Commandes communes](cli/common-cli-commands.md)
   + [Activer la journalisation](cli/enable-logging.md)
   + [Gérer le cache](cli/manage-cache.md)
   + [Gestion des indexeurs](cli/manage-indexers.md)
   + [Configuration des tâches cron](cli/configure-cron-jobs.md)
   + [Compiler le code](cli/code-compiler.md)
   + [Mode de fonctionnement](cli/set-mode.md)
   + [Démarrer les consommateurs des files d’attente de messages](cli/start-message-queues.md)
   + [Surligneur URN](cli/urn-highlighter.md)
   + [Rapports de dépendance](cli/dependency-reports.md)
   + [Localisation](cli/localization.md)
   + Gestion de la configuration {#configuration-management}
      + [Définir les valeurs](cli/set-configuration-values.md)
      + [Paramètres d’exportation](cli/export-configuration.md)
      + [Importer des données](cli/import-configuration.md)
   + Vue statique {#static-view}
      + [Stratégies de déploiement](cli/static-view-file-strategy.md)
      + [Déploiement de fichiers de vue statiques](cli/static-view-file-deployment.md)
   + [Créer des liens symboliques](cli/create-symlinks.md)
   + [Exécuter des tests unitaires](cli/unit-tests.md)
   + [Convertir les fichiers de disposition](cli/convert-layout-files.md)
   + [Générer des données pour les tests de performance](cli/generate-data.md)
   + [Exécution des utilitaires d’assistance (Commerce uniquement)](cli/run-support-utilities.md)
+ Fichiers de configuration {#files}
   + [Fichiers de configuration pour le déploiement](reference/deployment-files.md)
   + [Types de configuration](reference/config-create-types.md)
   + [Fichiers de module](reference/module-files.md)
   + [Sortie de module](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [ignorer](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ Chemins de configuration {#paths}
   + [Général](reference/config-reference-general.md)
   + [Extension B2B](reference/config-reference-b2b.md)
   + [Catalogue](reference/config-reference-catalog.md)
   + [Clients](reference/config-reference-customers.md)
   + [Modes de paiement](reference/config-reference-payment.md)
   + [Ventes](reference/config-reference-sales.md)
   + [Services tertiaires](reference/config-reference-services.md)
   + [Paramètres sensibles et spécifiques au système](reference/config-reference-sens.md)
   + [Remplacer les paramètres de configuration](reference/override-config-settings.md)
+ Tâches cron {#crons}
   + [Traitements et groupes cron](cron/custom-cron.md)
   + [Personnalisation de la référence crons](cron/custom-cron-reference.md)
   + [Configuration d’une tâche cron personnalisée](cron/custom-cron-tutorial.md)
+ Logs {#logs}
   + [Journaux personnalisés](logs/custom-logging.md)
   + [Interface de l’enregistreur](logs/logger-interface.md)
   + [Consigner l&#39;activité de la base de données](logs/database-activity.md)
   + [Écrire dans un fichier journal personnalisé](logs/custom-log-files.md)
+ Files d&#39;attente des messages {#message-queues}
   + [Framework de file d’attente des messages](queues/message-queue-framework.md)
   + [Gérer les files d&#39;attente de messages](queues/manage-message-queues.md)
   + [Configuration d’Amazon MQ](queues/aws-mq.md)
   + [Consommateurs](queues/consumers.md)
+ Plusieurs sites {#multi-sites}
   + [Plusieurs sites et vues](multi-sites/ms-overview.md)
   + [Identifiant d&#39;incrément de l&#39;entité de base de données](multi-sites/change-increment-id.md)
   + [Configuration dans l’administration](multi-sites/ms-admin.md)
   + [Configurer avec Nginx](multi-sites/ms-nginx.md)
   + [Configuration d’avec Apache](multi-sites/ms-apache.md)
+ Moteur de recherche {#search}
   + [Présentation des moteurs de recherche](search/overview-search.md)
   + [Configuration du moteur de recherche](search/configure-search-engine.md)
   + [Filtrer avec des mots vides](search/search-stopwords.md)
+ Sécurité {#security}
   + [Présentation de la sécurité](security/overview.md)
   + [Hachage du mot de passe](security/password-hashing.md)
   + [Empoisonnement du cache](security/cache-poisoning.md)
   + [Secure cron PHP](security/secure-cron-php.md)
   + [TXT de sécurité](security/security-txt.md)
   + [Exploitations de détournement de clic](security/xframe-options.md)
+ Stockage {#storage}
   + [Profileur de base de données](storage/db-profiler.md)
   + Stockage à distance {#remote-storage}
      + [Module de stockage à distance](remote-storage/remote-storage.md)
      + [Compartiment AWS S3](remote-storage/remote-storage-aws-s3.md)
      + [Redimensionnement de l’image](remote-storage/remote-storage-image-resize.md)
      + [Stockage à distance pour le cloud](remote-storage/cloud-support.md)
   + Stockage de session {#session-storage}
      + [Emplacement de stockage de la session](storage/sessions.md)
      + [memcached pour le stockage de session](storage/memcached.md)
      + [memcached sur CentOS](storage/memcache-centos.md)
      + [memcached sur Ubuntu](storage/memcache-ubuntu.md)
   + Fractionner la base de données {#split-db}
      + [Présentation de la base de données partagée](storage/multi-master.md)
      + [Configuration automatique](storage/multi-master-masterdb.md)
      + [Configuration manuelle](storage/multi-master-manual.md)
      + [Vérifier la base de données fractionnée](storage/multi-master-verify.md)
      + [Réplication de la base de données](storage/multi-master-replication.md)
      + [Revenir à une base de données unique](storage/revert-split-database.md)
+ [Retour aux guides opérationnels](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html?lang=fr)