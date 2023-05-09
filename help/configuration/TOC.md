---
user-guide-title: Guide de configuration
user-guide-description: Configurez les fonctionnalités et services de votre application Adobe Commerce ou Magento Open Source.
feature: Configuration
source-git-commit: 68c4cfc29735d2ea296f579ed0a0ff52db3fdd9f
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Guide de configuration {#configuration-guide}

+ [Présentation](overview.md)
+ Configuration générale {#setup}
   + [Initialisation de l’application et amorçage](bootstrap/initialization.md)
   + [Modes d’application](bootstrap/application-modes.md)
   + [Paramètres du Bootstrap](bootstrap/set-parameters.md)
   + [Profilage](bootstrap/mage-profiler.md)
   + [Chemins de répertoire de base](bootstrap/mage-directory.md)
+ Déploiement {#deployment}
   + [Présentation du déploiement](deployment/overview.md)
   + [Déploiement mono-machine](deployment/single-machine.md)
   + [Déploiement du pipeline](deployment/technical-details.md)
   + [Conditions préalables](deployment/prerequisites.md)
   + [Configuration du système de développement](deployment/development-system.md)
   + [Configuration du système de création](deployment/build-system.md)
   + [Configuration du système de production](deployment/production-system.md)
   + [Autorisations d’accès aux systèmes de fichiers](deployment/file-system-permissions.md)
   + Exemples {#examples}
      + [Utiliser une configuration partagée](deployment/example-shared-configuration.md)
      + [Utilisation des commandes de l’interface de ligne de commande](deployment/example-using-cli.md)
      + [Utilisation de variables d’environnement](deployment/example-environment-variables.md)
+ Cache {#cache}
   + [Présentation de la mise en cache](cache/caching-overview.md)
   + [Types de cache](cache/cache-types.md)
   + [Options de cache](cache/cache-options.md)
   + [Cache L2](cache/level-two-cache.md)
   + Redis {#redis}
      + [Configuration de Redis](cache/config-redis.md)
      + [Utiliser des redis pour le cache par défaut](cache/redis-pg-cache.md)
      + [Utilisation de Redis pour le stockage de session](cache/redis-session.md)
   + Varnish {#varnish}
      + [Présentation du vernis](cache/config-varnish.md)
      + [Installer le vernis](cache/config-varnish-install.md)
   + [Serveur web](cache/config-varnish-server.md)
   + [Configuration de l’application Commerce](cache/configure-varnish-commerce.md)
   + [Configuration du vernis avancé](cache/config-varnish-advanced.md)
   + [Nettoyage du cache](cache/use-varnish-cache.md)
   + [Nettoyage du cache de plusieurs instances Varnish](cache/use-multiple-varnish-cache.md)
   + [Vérification de la configuration du vernis](cache/config-varnish-final.md)
   + [Bloc ESI de marque](cache/use-varnish-esi.md)
   + [Cache de contenu statique](cache/static-content-signing.md)
+ Ligne de commande {#cli}
   + [Outil de ligne de commande](cli/config-cli.md)
   + [Commandes courantes](cli/common-cli-commands.md)
   + [Activation de la journalisation](cli/enable-logging.md)
   + [Gestion du cache](cli/manage-cache.md)
   + [Gestion des indexeurs](cli/manage-indexers.md)
   + [Configuration des tâches cron](cli/configure-cron-jobs.md)
   + [Compiler le code](cli/code-compiler.md)
   + [Mode de fonctionnement](cli/set-mode.md)
   + [Démarrage des consommateurs de la file de messages](cli/start-message-queues.md)
   + [Surligneur URN](cli/urn-highlighter.md)
   + [Rapports de dépendance](cli/dependency-reports.md)
   + [Localisation](cli/localization.md)
   + Gestion des configurations {#configuration-management}
      + [Définir des valeurs](cli/set-configuration-values.md)
      + [Paramètres d’exportation](cli/export-configuration.md)
      + [Importer des données](cli/import-configuration.md)
   + Vue statique {#static-view}
      + [Stratégies de déploiement](cli/static-view-file-strategy.md)
      + [Déploiement de fichiers d’affichage statique](cli/static-view-file-deployment.md)
   + [Créer des liens symboliques](cli/create-symlinks.md)
   + [Exécution de tests unitaires](cli/unit-tests.md)
   + [Conversion de fichiers de mise en page](cli/convert-layout-files.md)
   + [Génération de données pour les tests de performance](cli/generate-data.md)
   + [Exécution des utilitaires de prise en charge (Commerce uniquement)](cli/run-support-utilities.md)
+ Fichiers de configuration {#files}
   + [Fichiers de configuration pour le déploiement](reference/deployment-files.md)
   + [Types de configuration](reference/config-create-types.md)
   + [Fichiers de module](reference/module-files.md)
   + [Sortie de module](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [gitignore](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ Chemins de configuration {#paths}
   + [Général](reference/config-reference-general.md)
   + [Extension B2B](reference/config-reference-b2b.md)
   + [Catalogue](reference/config-reference-catalog.md)
   + [Clients](reference/config-reference-customers.md)
   + [Modes de paiement](reference/config-reference-payment.md)
   + [Ventes](reference/config-reference-sales.md)
   + [Services](reference/config-reference-services.md)
   + [Paramètres sensibles et spécifiques au système](reference/config-reference-sens.md)
   + [Remplacement des paramètres de configuration](reference/override-config-settings.md)
+ Tâches Cron {#crons}
   + [Tâches et groupes Cron](cron/custom-cron.md)
   + [Personnalisation de la référence des crons](cron/custom-cron-reference.md)
   + [Configuration d’une tâche cron personnalisée](cron/custom-cron-tutorial.md)
+ Journaux {#logs}
   + [Journaux personnalisés](logs/custom-logging.md)
   + [Interface de journalisation](logs/logger-interface.md)
   + [Activité Log database](logs/database-activity.md)
   + [Écriture dans un fichier journal personnalisé](logs/custom-log-files.md)
+ Queues des messages {#message-queues}
   + [Structure de la file d&#39;attente des messages](queues/message-queue-framework.md)
   + [Gestion des files d’attente de messages](queues/manage-message-queues.md)
   + [Configuration d’Amazon MQ](queues/aws-mq.md)
   + [Consommateurs](queues/consumers.md)
+ Plusieurs sites {#multi-sites}
   + [Plusieurs sites et vues](multi-sites/ms-overview.md)
   + [Identifiant d’incrémentation de l’entité de base de données](multi-sites/change-increment-id.md)
   + [Configuration dans l’administrateur](multi-sites/ms-admin.md)
   + [Configuration avec Nginx](multi-sites/ms-nginx.md)
   + [Configuration avec Apache](multi-sites/ms-apache.md)
+ Moteur de recherche {#search}
   + [Présentation des moteurs de recherche](search/overview-search.md)
   + [Configuration du moteur de recherche](search/configure-search-engine.md)
   + [Filtrage avec mots de passe](search/search-stopwords.md)
+ Sécurité {#security}
   + [Présentation de la sécurité](security/overview.md)
   + [Hachage de mot de passe](security/password-hashing.md)
   + [Empoisonnement du cache](security/cache-poisoning.md)
   + [Secure cron PHP](security/secure-cron-php.md)
   + [TXT de sécurité](security/security-txt.md)
   + [En-tête X-Frame-Options](security/xframe-options.md)
+ Stockage {#storage}
   + [profileur de base de données](storage/db-profiler.md)
   + Stockage distant {#remote-storage}
      + [Module de stockage distant](remote-storage/remote-storage.md)
      + [Compartiment AWS S3](remote-storage/remote-storage-aws-s3.md)
      + [Redimensionnement des images](remote-storage/remote-storage-image-resize.md)
      + [Stockage distant pour le cloud](remote-storage/cloud-support.md)
   + Stockage de session {#session-storage}
      + [Emplacement de stockage de session](storage/sessions.md)
      + [mis en cache pour le stockage de session](storage/memcached.md)
      + [memcached sur CentOS](storage/memcache-centos.md)
      + [memcached sur Ubuntu](storage/memcache-ubuntu.md)
   + Diviser la base de données {#split-db}
      + [Présentation de la base de données partagée](storage/multi-master.md)
      + [Configuration automatique](storage/multi-master-masterdb.md)
      + [Configuration manuelle](storage/multi-master-manual.md)
      + [Vérifier la base de données partagée](storage/multi-master-verify.md)
      + [Réplication des bases de données](storage/multi-master-replication.md)
      + [Rétablissement d’une seule base de données](storage/revert-split-database.md)
+ [Revenir aux guides opérationnels](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)