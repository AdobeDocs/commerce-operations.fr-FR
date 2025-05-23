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

Le code qui étend ou personnalise le comportement d’Adobe Commerce est appelé extension. Vous pouvez éventuellement grouper et distribuer des extensions sur le [Commerce Marketplace](https://commercemarketplace.adobe.com/) ou un autre système de distribution d’extension.

Les extensions incluent :

- Modules (extension des fonctionnalités Adobe Commerce)
- Thèmes (modifiez l’aspect de votre storefront et de votre administrateur)
- Packages de langue (localisez le storefront et l’administrateur)

Cette rubrique explique comment utiliser l’interface de ligne de commande pour gérer les extensions tierces que vous achetez sur le Commerce Marketplace pour des projets _sur site_. Pour les projets d’infrastructure cloud, voir [Gestion des extensions](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure-store/extensions).

Vous pouvez utiliser la même procédure pour installer l’extension _any_ ; vous avez simplement besoin du nom et de la version du compositeur de l’extension. Pour le trouver, ouvrez le fichier `composer.json` de l’extension et notez les valeurs de `"name"` et `"version"`.

## Installer

Avant l’installation, vous pouvez :

1. Sauvegardez votre base.
1. Activer le mode de maintenance :

   ```bash
   bin/magento maintenance:enable
   ```

Pour installer une extension, vous devez :

1. Obtenez une extension du Commerce Marketplace ou d’un autre développeur d’extensions.
1. Si vous installez une extension à partir du Commerce Marketplace, assurez-vous que le référentiel `repo.magento.com` existe dans votre fichier `composer.json` :

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. Obtenez le nom et la version du compositeur de l’extension.
1. Mettez à jour le fichier `composer.json` de votre projet avec le nom et la version de l’extension.
1. Vérifiez que l’extension est installée correctement.
1. Activez et configurez l’extension.

### Obtenir des informations sur l’extension

Si vous connaissez déjà le nom et la version du compositeur de l’extension, ignorez cette étape et passez à l’étape [Mettre à jour votre fichier `composer.json`](#update-composer-dependencies).

Pour obtenir le nom et la version du compositeur de l’extension à partir du Commerce Marketplace :

1. Connectez-vous à [Commerce Marketplace](https://commercemarketplace.adobe.com/) avec le nom d’utilisateur et le mot de passe que vous avez utilisés pour acheter l’extension.

1. Dans le coin supérieur droit, cliquez sur **Votre nom** > **Mon profil**.

   ![Accéder à votre compte Marketplace](../../assets/installation/marketplace-my-profile.png)

1. Cliquez sur **Mes achats**.

   ![Historique des achats Marketplace](../../assets/installation//marketplace-my-purchases.png)

1. Recherchez l’extension que vous souhaitez installer et notez le nom et la version du composant.

   ![Les détails techniques affichent le nom du compositeur de l’extension ](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>Vous pouvez également trouver le nom du compositeur et la version de l’extension _any_ (que vous l’ayez achetée sur Commerce Marketplace ou ailleurs) dans le fichier `composer.json` de l’extension.

### Mise à jour des dépendances du compositeur

Ajoutez le nom et la version de l’extension à votre fichier `composer.json` :

1. Accédez au répertoire de votre projet et mettez à jour votre fichier `composer.json`.

   ```bash
   composer require <component-name>:<version>
   ```

   Par exemple,

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. Saisissez vos [clés d&#39;authentification](../prerequisites/authentication-keys.md). Votre clé publique est votre nom d’utilisateur ; votre clé privée est votre mot de passe.

1. Attendez que le compositeur termine la mise à jour des dépendances de votre projet et assurez-vous qu’il n’y a aucune erreur :

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

Recherchez l’extension sous &quot;Liste des modules désactivés&quot;.

### Activer

Certaines extensions ne fonctionnent pas correctement, sauf si vous effacez d’abord les fichiers d’affichage statique générés. Utilisez l’option `--clear-static-content` pour effacer les fichiers d’affichage statique lorsque vous activez une extension.

1. Activez l’extension et effacez les fichiers de vue statique :

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   Vous devriez voir la sortie suivante :

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

1. Recompiler votre projet : en mode de production, vous pouvez recevoir un message indiquant &quot;Veuillez réexécuter la commande de compilation du Magento&quot;. L’application ne vous invite pas à exécuter la commande compile en mode Développeur.

   ```bash
   bin/magento setup:di:compile
   ```

1. Vérifiez que l’extension est activée :

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   La sortie doit normalement s’afficher pour vérifier que l’extension n’est plus désactivée :

   ```
   Module is enabled
   ```

1. Nettoyez le cache :

   ```bash
   bin/magento cache:clean
   ```

1. Configurez l’extension dans Admin selon les besoins.

>[!TIP]
>
>Si vous rencontrez des erreurs lors du chargement du storefront dans un navigateur, utilisez la commande suivante pour effacer le cache : `bin/magento cache:flush`.

## Mettre à niveau

Pour mettre à jour ou mettre à niveau un module ou une extension :

1. Téléchargez le fichier mis à jour depuis Marketplace ou un autre développeur d’extensions. Prenez note du nom et de la version du module.

1. Exportez le contenu dans le répertoire racine de votre application.

1. S’il existe un module de compositeur pour le module, exécutez l’une des opérations suivantes.

   Mise à jour par nom de module :

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

- Comment rétablir les modifications des tables de la base de données
- Comment rétablir les modifications apportées aux données de la base
- Quels fichiers doivent être supprimés ou restaurés ?

>[!CAUTION]
>
>Exécutez les étapes de désinstallation sur un environnement hors production _first_ et effectuez un test complet avant de procéder au déploiement dans votre environnement de production.

Les instructions suivantes fournissent des informations générales pour la désinstallation d’extensions tierces :

1. Supprimez l’extension de votre référentiel de projet Adobe Commerce.

   - Pour les extensions basées sur le compositeur, supprimez l’extension de votre fichier Adobe Commerce `composer.json`.

     ```bash
     composer remove <component-name>
     ```

   - Pour les extensions non basées sur un compositeur, supprimez les fichiers physiques du référentiel de projet Adobe Commerce.

     ```bash
     rm -rf app/code/<vendor-name>/<component-name>
     ```

1. Si le fichier `config.php` est contrôlé par la source dans votre référentiel de projet Adobe Commerce, supprimez l’extension du fichier `config.php`.

1. Testez votre base de données locale pour vous assurer que les instructions fournies par le fournisseur fonctionnent comme prévu.

1. Vérifiez que l’extension est correctement désactivée et que votre site web fonctionne comme prévu dans votre environnement d’évaluation.

1. Déployez les modifications dans votre environnement de production.
