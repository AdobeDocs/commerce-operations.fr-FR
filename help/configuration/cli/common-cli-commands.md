---
title: Commandes courantes
description: Affichez un échantillon des commandes et de l’utilisation courantes de l’interface de ligne de commande de Commerce.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# Commandes courantes

Vous trouverez ci-dessous un résumé de certaines des commandes disponibles.

**Pour afficher une liste complète des commandes**:

```bash
bin/magento list
```

Exemple de commande d’aide :

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

Les commandes sont présentées sous forme de résumé uniquement ; pour plus d’informations sur une commande, cliquez sur le lien dans la colonne Commande .

| Commande | Description |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | Gère le cache |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | Gère les indexeurs |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Exécution de tâches Commerce cron |
| [`magento setup:di:compile`](../cli/code-compiler.md) | Compile tous les proxys et usines inexistants ; et pré-compile les définitions de classe, les informations d’héritage et les définitions de plug-in pour un magasin et un site web. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | Dépendances des modules, dépendances circulaires et dépendances des structures Commerce. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | Crée un dictionnaire de traduction ou un package de traduction |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | Déploiement de fichiers d’affichage statiques |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | Crée une page CSS à partir de LESS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | Exécution de tests automatisés |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | Mettez à jour vos fichiers XML de mise en page pour qu’ils correspondent à la nouvelle feuille de style XSLT (Extensible Stylesheet Language Transformations). |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | Générer des données à utiliser pour les tests de performances. |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | Installe des exemples de données facultatifs après l’installation de l’application Commerce.<br><br>Pour plus d’informations sur les exemples de données, voir [Exemple de données facultatif](../../installation/sample-data/overview.md). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | Gère les configurations du serveur principal |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | Crée/modifie/déverrouille les utilisateurs administrateurs. |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | Active/désactive les conseils de modèle de développeur. |

## Arguments courants

Les arguments suivants sont communs à toutes les commandes. Ces commandes peuvent être exécutées avant ou après l’installation du logiciel Commerce :

| Version longue | Version courte | Signification |
|--- |--- |--- |
| `--help` | `-h` | Obtenez de l’aide pour n’importe quelle commande. Par exemple : `./magento help setup:install` ou `./magento help setup:config:set`. |
| `--quiet` | `-q` | Mode silencieux ; pas de sortie. |
| `--no-interaction` | `-n` | Aucune question interactive. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Niveau de verbosité. Par exemple : `--verbose=3` ou `-vvv` affiche la verbosité de débogage, qui est la sortie la plus détaillée. La valeur par défaut est `--verbose=1` ou `-v`. |
| `--version` | `-V` | Afficher cette version de l’application |
| `--ansi` | n/a | Forcer la sortie ANSI |
| `--no-ansi` | n/a | Désactiver la sortie ANSI |
