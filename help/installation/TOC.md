---
user-guide-title: Guide d’installation
user-guide-description: Découvrez comment installer Adobe Commerce et Magento Open Source pour les déploiements sur site.
source-git-commit: 949ef8d2036ceeef3cc892a5063ddecc2586a6a9
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# Guide d’installation {#installation-guide}

- [Présentation](overview.md)
- [Configuration requise](system-requirements.md)
- Conditions préalables {#prerequisites}
   - [Présentation](prerequisites/overview.md)
   - Système de fichiers {#file-system}
      - [Présentation](prerequisites/file-system/overview.md)
      - [Configuration des autorisations](prerequisites/file-system/configure-permissions.md)
   - Serveur web {#web-server}
      - [Nginx](prerequisites/web-server/nginx.md)
      - [Apache](prerequisites/web-server/apache.md)
   - Serveur de base de données {#database-server}
      - [MySQL](prerequisites/database/mysql.md)
      - [Connexions distantes](prerequisites/database/mysql-remote.md)
   - Moteur de recherche {#search-engine}
      - [Présentation](prerequisites/search-engine/overview.md)
      - [AWS OpenSearch](prerequisites/search-engine/aws-opensearch.md)
      - [Configuration de Nginx](prerequisites/search-engine/configure-nginx.md)
      - [Configuration d’Apache](prerequisites/search-engine/configure-apache.md)
   - [PHP](prerequisites/php-settings.md)
   - [courtier de messages](prerequisites/rabbitmq.md)
   - [Sécurité](prerequisites/security.md)
   - [Clés d’authentification](prerequisites/authentication-keys.md)
   - [Adobe Commerce](prerequisites/commerce.md)
   - [Logiciels facultatifs](prerequisites/optional-software.md)
- [Installation de démarrage rapide](composer.md)
- [Installation avancée](advanced.md)
- Etapes de post-installation {#next-steps}
   - [Vérification de l’installation](next-steps/verify.md)
   - [Configuration de l’application](next-steps/configuration.md)
   - [Définir un masque (facultatif)](next-steps/set-umask.md)
   - Installer des exemples de données (facultatif) {#sample-data}
      - [Présentation](sample-data/overview.md)
      - [Télécharger les modules du compositeur](sample-data/composer-packages.md)
      - [Clonage des référentiels Git](sample-data/git-repositories.md)
      - [Suppression ou mise à jour de modules](sample-data/remove-or-update.md)
- Tutoriels {#tutorials}
   - [Sauvegarde et restauration du système de fichiers, du média et de la base de données](tutorials/backup.md)
   - [Vérification du statut de la base de données](tutorials/database-status.md)
   - [Configuration du comportement des consommateurs de messages](tutorials/message-consumers.md)
   - [Configuration du fournisseur de verrouillage](tutorials/lock-provider.md)
   - [Configuration du magasin](tutorials/store.md)
   - [Créer, modifier ou déverrouiller des comptes d’administration](tutorials/admin.md)
   - [Création ou mise à jour de la configuration du déploiement](tutorials/deployment.md)
   - [Création du schéma de la base de données](tutorials/database.md)
   - [Affichage ou modification de l’URI d’administration](tutorials/admin-uri.md)
   - [Activation ou désactivation du mode de maintenance](tutorials/maintenance-mode.md)
   - [Activation ou désactivation des modules](tutorials/manage-modules.md)
   - [Installer une extension](tutorials/extensions.md)
   - [Installer Commerce](tutorials/install.md)
   - [Modification de docroot pour améliorer la sécurité](tutorials/docroot.md)
   - [Désinstallation des packages de langue](tutorials/language-packages.md)
   - [Désinstallation des modules](tutorials/uninstall-modules.md)
   - [Désinstallation ou réinstallation de Commerce](tutorials/uninstall.md)
   - [Désinstaller les thèmes](tutorials/themes.md)
   - [Mise à niveau du schéma de base de données](tutorials/database-upgrade.md)
