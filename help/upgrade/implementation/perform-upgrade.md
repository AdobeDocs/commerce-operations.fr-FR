---
title: Effectuer une mise à niveau
description: Pour mettre à niveau un projet Adobe Commerce ou Magento Open Source, procédez comme suit.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# Effectuer une mise à niveau

Vous pouvez mettre à niveau votre application Adobe Commerce ou Magento Open Source à partir de la ligne de commande si vous avez installé le logiciel en procédant comme suit :

- Téléchargement du module externe à l’aide du `composer create-project` .
- Installation de l’archive compressée.

>[!NOTE]
>
>N’utilisez pas cette méthode pour effectuer la mise à niveau si vous avez cloné le référentiel GitHub. Voir [Mettre à niveau une installation basée sur Git](../developer/git-installs.md) pour obtenir des instructions de mise à niveau.

Les instructions suivantes vous montrent comment mettre à niveau à l’aide du compositeur. Adobe Commerce 2.4.2 a introduit la prise en charge du compositeur 2. Si vous tentez de mettre à niveau à partir de &lt;2.4.1, vous devez d’abord effectuer une mise à niveau vers une version compatible avec le compositeur 2 (par exemple, 2.4.2) à l’aide du compositeur 1. _before_ mise à niveau vers Composer 2 pour les mises à niveau ultérieures à la version 2.4.2. En outre, vous devez exécuter une [version prise en charge](../../installation/system-requirements.md) de PHP.

>[!WARNING]
>
>La procédure de mise à niveau d’Adobe Commerce et de Magento Open Source a été modifiée. Vous devez installer une nouvelle version de la fonction `magento/composer-root-update-plugin` (voir [conditions préalables](../prepare/prerequisites.md)). En outre, les commandes de mise à niveau ont été modifiées à partir de `composer require magento/<package_name>` to `composer require-commerce magento/<package_name>`.

## Avant de commencer

Vous devez renseigner la variable [conditions préalables à la mise à niveau](../prepare/prerequisites.md) pour préparer votre environnement avant de lancer le processus de mise à niveau.

## Gestion des modules

>[!NOTE]
>
>Consultez les exemples à la fin de cette section pour obtenir de l’aide sur la spécification de différents niveaux de version. Par exemple, version mineure, correctif de qualité et correctif de sécurité. Les clients Adobe Commerce peuvent accéder aux correctifs deux semaines avant la date de disponibilité générale (GA). Les packages de version préliminaire sont disponibles uniquement via le compositeur . Vous ne pouvez pas les trouver sur le portail de téléchargements ou GitHub avant GA. Si vous ne trouvez pas ces modules dans le compositeur, contactez l’assistance Adobe Commerce.

1. Passez en mode de maintenance pour empêcher l’accès à votre boutique lors de la mise à niveau.

   ```bash
   bin/magento maintenance:enable
   ```

   Voir [Activation ou désactivation du mode de maintenance](../../installation/tutorials/maintenance-mode.md) pour d’autres options. Vous pouvez éventuellement créer une [page du mode de maintenance personnalisé](../troubleshooting/maintenance-mode-options.md).

1. Le démarrage du processus de mise à niveau pendant l’exécution de processus asynchrones, tels que les consommateurs de file d’attente de messages, peut entraîner une corruption des données. Pour empêcher la corruption des données, désactivez toutes les tâches cron.

   _Adobe Commerce sur l’infrastructure cloud :_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source :_

   ```bash
   bin/magento cron:remove
   ```

1. Démarrez manuellement tous les consommateurs de la file d’attente de messages pour vous assurer que tous les messages sont consommés.

   ```bash
   bin/magento cron:run --group=consumers
   ```

   Attendez que la tâche cron soit terminée. Vous pouvez surveiller l’état de la tâche à l’aide d’une visionneuse de processus ou en exécutant la fonction `ps aux | grep 'bin/magento queue'` plusieurs fois jusqu’à ce que tous les processus soient terminés.

1. Créez une sauvegarde de la variable `composer.json` fichier .

   ```bash
   cp composer.json composer.json.bak
   ```

1. Ajoutez ou supprimez des packages spécifiques en fonction de vos besoins.

   Par exemple, si vous effectuez une mise à niveau de Magento Open Source vers Adobe Commerce, supprimez le package de Magento Open Source.

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   Vous pouvez également mettre à niveau des données d’exemple.

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _Adobe Commerce :_

      ```bash
      composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
      ```

   - _Magento Open Source :_

      ```bash
      composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
      ```

1. Mettez à niveau votre instance à l’aide de ce qui suit : `composer require-commerce` syntaxe de commande :

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   Les options de commande incluent :

   - `<product>` —(Obligatoire) Package à mettre à niveau. Pour les installations sur site, cette valeur doit être : `product-community-edition` ou `product-enterprise-edition`.

   - `<version>` —(Obligatoire) Version d’Adobe Commerce ou de Magento Open Source vers laquelle vous effectuez une mise à niveau. Par exemple : `2.4.3`.

   - `--no-update` —(Obligatoire) Désactive la mise à jour automatique des dépendances.

   - `--interactive-root-conflicts` —(Facultatif) Permet d’afficher et de mettre à jour de manière interactive les valeurs obsolètes des versions précédentes ou les valeurs personnalisées qui ne correspondent pas à la version vers laquelle vous effectuez la mise à niveau.

   - `--force-root-updates` —(Facultatif) Remplace toutes les valeurs personnalisées en conflit par les valeurs de Magento attendues.

   - `--help` —(Facultatif) Fournit des détails d’utilisation du module externe.
   Si aucun `--interactive-root-conflicts` nor `--force-root-updates` sont spécifiées, la commande conserve les valeurs existantes en conflit et affiche un message d’avertissement. Pour en savoir plus sur le module externe, reportez-vous à la section [Plug-Usage README](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. Mettez à jour les dépendances.

   ```bash
   composer update
   ```

### Exemple - Liste des versions disponibles

Pour afficher la liste complète des versions 2.4.x disponibles :

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### Exemple - Version mineure

Les versions mineures contiennent de nouvelles fonctionnalités, des correctifs de qualité et des correctifs de sécurité. Utilisez le compositeur pour spécifier une version mineure. Par exemple, pour spécifier le métappackage Magento Open Source 2.4.3 :

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.0 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.0 --no-update
```

### Exemple - Correctif de qualité

Les correctifs de qualité contiennent principalement des fonctions fonctionnelles. _et_ correctifs de sécurité. Cependant, elles peuvent parfois contenir de nouvelles fonctionnalités rétrocompatibles. Utilisez le compositeur pour télécharger un correctif de qualité. Par exemple, pour spécifier le métappackage Magento Open Source 2.4.1 :

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3 --no-update
```

### Exemple - Correctif de sécurité

Les correctifs de sécurité contiennent uniquement des correctifs de sécurité. Ils sont conçus pour faciliter et accélérer le processus de mise à niveau.

Les correctifs de sécurité utilisent la convention de dénomination du compositeur `2.4.x-px`. Utilisez le compositeur pour spécifier un correctif.

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3-p1 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3-p1 --no-update
```

## Mise à jour des métadonnées

1. Mettez à jour le `"name"`, `"version"`, et `"description"` dans le champ `composer.json` le cas échéant.

   >[!NOTE]
   >
   >Mise à jour des métadonnées dans le `composer.json` est entièrement superficiel et non fonctionnel.

1. Appliquez les mises à jour.

   ```bash
   composer update
   ```

1. Effacez la variable `var/` et `generated/` sous-répertoires :

   ```bash
   rm -rf var/cache/*
   ```

   ```bash
   rm -rf var/page_cache/*
   ```

   ```bash
   rm -rf generated/code/*
   ```

   >[!NOTE]
   >
   >Si vous utilisez un stockage de cache autre que le système de fichiers, tel que Redis ou Memcached, vous devez également effacer manuellement le cache là-bas.

1. Mettez à jour le schéma et les données de la base de données.

   ```bash
   bin/magento setup:upgrade
   ```

1. Désactivez le mode de maintenance.

   ```bash
   bin/magento maintenance:disable
   ```

1. _(Facultatif)_ Redémarrez le vernis.

   Si vous utilisez le vernis pour la mise en cache de la page, redémarrez-le :

   ```bash
   service varnish restart
   ```

## Vérifier votre travail

Ouvrez l’URL de storefront dans un navigateur web pour vérifier si la mise à niveau a réussi. Si votre mise à niveau a échoué, votre storefront ne se chargera pas correctement.

Si l’application échoue avec une  `We're sorry, an error has occurred while generating this email.` error:

1. Réinitialiser [propriétaire et autorisations du système de fichiers](../../installation/prerequisites/file-system/configure-permissions.md) en tant qu’utilisateur avec `root` des privilèges.
1. Effacez les répertoires suivants :
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Vérifiez à nouveau votre vitrine dans votre navigateur web.
