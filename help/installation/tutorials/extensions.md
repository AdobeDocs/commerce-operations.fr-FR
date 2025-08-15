---
title: Gestion des extensions tierces
description: Pour installer, activer, mettre à niveau et désinstaller des extensions Adobe Commerce, procédez comme suit.
exl-id: b564662a-2e5f-4fa9-bae1-ca7498478fa9
source-git-commit: f057cf082eeab1e34957e284817c6b93517de21b
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 0%

---


# Gestion des extensions tierces

Le code qui étend ou personnalise le comportement d’Adobe Commerce est appelé extension. Vous pouvez éventuellement regrouper et distribuer des extensions sur [Commerce Marketplace](https://commercemarketplace.adobe.com/) ou sur un autre système de distribution d’extensions.

Les extensions incluent :

- Modules (extension des fonctionnalités d’Adobe Commerce)
- Thèmes (modifier l’aspect de votre storefront et de votre administrateur)
- Packages de langue (localiser le storefront et l’administrateur)

Cette rubrique explique comment utiliser l’interface de ligne de commande pour gérer les extensions tierces que vous achetez auprès de Commerce Marketplace pour les projets _On-premise_. Pour les projets d’infrastructure cloud, voir [Gestion des extensions](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions).

Vous pouvez utiliser la même procédure pour installer l’extension _any_ ; tout ce dont vous avez besoin est le nom et la version du compositeur de l’extension. Pour le trouver, ouvrez le fichier `composer.json` de l’extension et notez les valeurs de `"name"` et `"version"`.

## Installer

Avant l’installation, vous pouvez :

1. Sauvegardez votre base de données.
1. Activez le mode de maintenance :

   ```bash
   bin/magento maintenance:enable
   ```

Pour installer une extension, vous devez :

1. Obtenez une extension du Commerce Marketplace ou d’un autre développeur d’extensions.
1. Si vous installez une extension à partir de Commerce Marketplace, assurez-vous que le référentiel `repo.magento.com` existe dans votre fichier `composer.json` :

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. Obtenez le nom et la version du compositeur de l’extension.
1. Mettez à jour le fichier `composer.json` dans votre projet avec le nom et la version de l’extension.
1. Vérifiez que l’extension est installée correctement.
1. Activez et configurez l’extension.

### Obtenir des informations sur l’extension

Si vous connaissez déjà le nom et la version du compositeur de l’extension, ignorez cette étape et continuez avec [Mettre à jour votre fichier `composer.json`](#update-composer-dependencies).

Pour obtenir le nom et la version du compositeur de l’extension à partir du Commerce Marketplace :

1. Connectez-vous à [Commerce Marketplace](https://commercemarketplace.adobe.com/) avec le nom d&#39;utilisateur et le mot de passe que vous avez utilisés pour acheter l&#39;extension.

1. Dans le coin supérieur droit, cliquez sur **Votre nom** > **Mon profil**.

   ![Accéder à votre compte Marketplace](../../assets/installation/marketplace-my-profile.png)

1. Cliquez sur **Mes achats**.

   ![Historique des achats du marché](../../assets/installation//marketplace-my-purchases.png)

1. Recherchez l’extension à installer et notez le nom et la version du composant.

   ![Les détails techniques affichent le nom du compositeur de l’extension](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>Vous pouvez également trouver le nom du compositeur et la version de l’extension _any_ (que vous l’ayez achetée sur Commerce Marketplace ou ailleurs) dans le fichier `composer.json` de l’extension.

### Mettre à jour les dépendances du compositeur

Ajoutez le nom et la version de l’extension à votre fichier `composer.json` :

1. Accédez au répertoire du projet et mettez à jour le fichier `composer.json`.

   ```bash
   composer require <component-name>:<version>
   ```

   Par exemple,

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. Saisissez vos [ clés d’authentification ](../prerequisites/authentication-keys.md). Votre clé publique est votre nom d&#39;utilisateur ; votre clé privée est votre mot de passe.

1. Attendez que le compositeur ait terminé la mise à jour des dépendances de votre projet et vérifiez qu’il n’y a aucune erreur :

   ```
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

### Vérification de l’installation

Pour vérifier que l’extension est installée correctement, exécutez la commande suivante :

```bash
bin/magento module:status J2t_Payplug
```

Par défaut, l’extension est probablement désactivée :

```
Module is disabled
```

Le nom de l’extension est au format `<VendorName>_<ComponentName>` ; il s’agit d’un format différent du nom du compositeur. Utilisez ce format pour activer l’extension. Si vous n’êtes pas sûr du nom de l’extension, exécutez :

```bash
bin/magento module:status
```

Et recherchez l’extension sous « Liste des modules désactivés ».

### Activer

Certaines extensions ne fonctionnent pas correctement, sauf si vous effacez d’abord les fichiers d’affichage statique générés. Utilisez l’option `--clear-static-content` pour effacer les fichiers d’affichage statiques lorsque vous activez une extension.

1. Activez l’extension et effacez les fichiers d’affichage statique :

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   La sortie suivante devrait s’afficher :

   ```
   The following modules have been enabled:
   - J2t_Payplug
   
   To make sure that the enabled modules are properly registered, run 'setup:upgrade'.
   Cache cleared successfully.
   Generated classes cleared successfully. Please run the 'setup:di:compile' command to generate classes.
   Generated static view files cleared successfully.
   ```

1. Enregistrez l’extension :

   ```bash
   bin/magento setup:upgrade
   ```

1. Recompiler votre projet : en mode Production, vous pouvez recevoir un message indiquant « Veuillez réexécuter la commande de compilation Magento ». L’application ne vous invite pas à exécuter la commande compiler en mode Développeur.

   ```bash
   bin/magento setup:di:compile
   ```

1. Vérifiez que l’extension est activée :

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   Vous devriez voir la sortie vérifiant que l’extension n’est plus désactivée :

   ```
   Module is enabled
   ```

1. Nettoyez le cache :

   ```bash
   bin/magento cache:clean
   ```

1. Configurez l’extension dans Admin selon vos besoins.

>[!TIP]
>
>Si vous rencontrez des erreurs lors du chargement du storefront dans un navigateur, utilisez la commande suivante pour effacer le cache : `bin/magento cache:flush`.

## Mise à niveau

Pour mettre à jour ou mettre à niveau un module ou une extension :

1. Téléchargez le fichier mis à jour à partir de Marketplace ou d’un autre développeur d’extensions. Notez le nom et la version du module.

1. Exportez le contenu vers le répertoire racine de votre application.

1. S’il existe un package de compositeur pour le module , exécutez l’une des opérations suivantes.

   Mettre à jour par nom de module :

   ```bash
   composer update vendor/module-name
   ```

   Mise à jour par version :

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. Exécutez les commandes suivantes pour mettre à niveau, déployer et nettoyer le cache.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```

## Désinstaller

Vous devez contacter le fournisseur de l’extension pour obtenir des instructions sur la suppression d’une extension tierce. Les instructions doivent fournir les informations suivantes :

- Comment annuler les modifications de table de base de données
- Comment annuler les modifications apportées aux données de la base de données
- Les fichiers à supprimer ou à rétablir

>[!CAUTION]
>
>Effectuez les étapes de désinstallation sur un environnement hors production _d’abord_ et testez-le minutieusement avant de le déployer sur votre environnement de production.

Les instructions suivantes fournissent des informations générales sur la désinstallation des extensions tierces :

1. Supprimez l’extension de votre référentiel de projet Adobe Commerce.

   - Pour les extensions basées sur un compositeur, supprimez l’extension de votre fichier Adobe Commerce `composer.json`.

     ```bash
     composer remove <component-name>
     ```

   - Pour les extensions non basées sur un compositeur, supprimez les fichiers physiques du référentiel de votre projet Adobe Commerce.

     ```bash
     rm -rf app/code/<vendor-name>/<component-name>
     ```

1. Si le fichier `config.php` est sous contrôle de code source dans votre référentiel de projet Adobe Commerce, supprimez l’extension du fichier `config.php`.

1. Testez votre base de données locale pour vous assurer que les instructions fournies par le fournisseur fonctionnent comme prévu.

1. Vérifiez que l’extension est correctement désactivée et que votre site web fonctionne comme prévu sur votre environnement d’évaluation.

1. Déployez les modifications dans votre environnement de production.
