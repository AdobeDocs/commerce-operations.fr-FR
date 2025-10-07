---
title: Commandes communes
description: Découvrez les commandes d’interface de ligne de commande Adobe Commerce courantes et leurs exemples d’utilisation. Découvrez les outils de ligne de commande essentiels au développement et à l’administration.
exl-id: d35a1dd9-10b3-4364-b6f4-b1e259a04e3d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Commandes communes

Voici un résumé de certaines des commandes disponibles.

**Pour afficher la liste complète des commandes** :

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

Les commandes sont présentées sous forme de résumé uniquement ; pour plus d&#39;informations sur une commande, cliquez sur le lien dans la colonne Commande.

| Commande | Description |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | Gère le cache |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | Gère les indexeurs |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Exécute les traitements cron Commerce |
| [`magento setup:di:compile`](../cli/code-compiler.md) | Compile tous les proxys et usines inexistants ; et précompile les définitions de classe, les informations d’héritage et les définitions de plug-in pour un magasin et un site web. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | Dépendances de module, dépendances circulaires et dépendances de framework Commerce. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | Crée un dictionnaire de traduction ou un package de traduction |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | Déploie des fichiers de vue statiques |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | CSS créé à partir de LESS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | Exécute des tests automatisés |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | Mettez à jour vos fichiers XML de disposition pour qu’ils correspondent à la nouvelle feuille de style XSLT (Extensible Stylesheet Language Transformations) |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | Générez des données à utiliser pour les tests de performance. |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | Installe des données d’exemple facultatives après l’installation de l’application Commerce.<br><br>Pour plus d’informations sur les données d’exemple, voir [Données d’exemple facultatives](../../installation/sample-data/overview.md). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | Gère les configurations du serveur principal |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | Crée/modifie/déverrouille les utilisateurs administrateurs. |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | Active/désactive les indications du modèle de développement. |

## Arguments courants

Les arguments suivants sont communs à [toutes les commandes](/help/tools/reference/commerce-on-premises.md). Ces commandes peuvent être exécutées avant ou après l’installation du logiciel Commerce :

| Version longue | Version courte | Signification |
|--- |--- |--- |
| `--help` | `-h` | Obtenez de l’aide pour n’importe quelle commande. Par exemple, `./magento help setup:install` ou `./magento help setup:config:set`. |
| `--quiet` | `-q` | Mode silencieux ; aucune sortie. |
| `--no-interaction` | `-n` | Aucune question interactive. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Niveau de détail. Par exemple, `--verbose=3` ou `-vvv` affiche le niveau de détail du débogage, qui est la sortie la plus détaillée. La valeur par défaut est `--verbose=1` ou `-v`. |
| `--version` | `-V` | Afficher cette version de l&#39;application |
| `--ansi` | s.o. | Forcer la sortie ANSI |
| `--no-ansi` | s.o. | Désactiver la sortie ANSI |
