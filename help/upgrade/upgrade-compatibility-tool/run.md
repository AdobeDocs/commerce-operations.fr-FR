---
title: '"Exécutez la variable [!DNL Upgrade Compatibility Tool]"'
description: Procédez comme suit pour exécuter la fonction [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande pour votre projet Adobe Commerce.
source-git-commit: 1dde98ab903f54aee0a094efd86dbf296065e92c
workflow-type: tm+mt
source-wordcount: '1081'
ht-degree: 0%

---


# Téléchargez la [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Pour commencer à utiliser la méthode [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande, téléchargez-la en exécutant la commande suivante :

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Le [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande

Le [!DNL Upgrade Compatibility Tool] est un outil qui vérifie une instance personnalisée Adobe Commerce par rapport à une version spécifique en analysant tous les modules qui y sont installés. Elle renvoie une liste des problèmes, erreurs et avertissements critiques qui doivent être résolus avant la mise à niveau vers la dernière version d’Adobe Commerce.

Voir [tutoriel vidéo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) pour en savoir plus sur le [!DNL Upgrade Compatibility Tool].

Commandes disponibles pour la fonction [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande :

| **Commande** | **Description** |
|----------------|-----------------|
| `upgrade:check` | Cette commande exécute la fonction [!DNL Upgrade Compatibility Tool] en analysant tous les modules qui y sont installés. |
| `core:code:changes` | Cette commande compare votre installation actuelle d’Adobe Commerce à une installation Vanilla propre. |
| `refactor` | Cette commande corrige automatiquement un ensemble réduit de problèmes. |
| `graphql:compare` | Cette commande permet d’analyser deux points d’entrée GraphQL et de comparer leurs schémas. |
| `list` | Cette commande renvoie une liste de tous les [!DNL Upgrade Compatibility Tool] commandes disponibles. |
| `help` | Cette commande renvoie tous les éléments disponibles `help`options de la variable [!DNL Upgrade Compatibility Tool]. Cette commande peut être exécutée ainsi qu&#39;une option avec les commandes précédentes. |

## Utilisez la variable `upgrade:check` command

Le `upgrade:check` recherche les modifications de code principal pour cette instance Adobe Commerce spécifique et toutes les modifications de code personnalisé qui y sont installées.

Le `upgrade:check` est la commande principale pour exécuter l’outil :

```bash
bin/uct upgrade:check <dir>
```

Où `<dir>` est le répertoire dans lequel se trouve votre instance Adobe Commerce.

Options disponibles pour la variable `upgrade:check` command :

| **Commande** | **Options disponibles** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: Renvoie toutes les options disponibles.</li><li>—min-issue-level : Vous pouvez filtrer les problèmes en fonction du niveau de problème minimum (la valeur par défaut est WARNING).</li><li>—ignore-current-version-compatibility-issues (ou -i) : Si vous ne souhaitez pas inclure dans votre rapport les problèmes critiques, les erreurs et les avertissements de la version actuelle.</li><li>—coming-version (ou -c) : Ciblez une version spécifique d’Adobe Commerce.</li></ul> |

Le [!DNL Upgrade Compatibility Tool] vous permet d’exécuter la variable `upgrade:check` avec une commande `--ignore-current-version-compatibility-issues` . Utilisez cette option lorsque vous souhaitez uniquement obtenir de nouveaux problèmes introduits avec la mise à jour de votre version actuelle vers la version ciblée de votre [!DNL Upgrade Compatibility Tool] rapport :

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Cela s’applique uniquement aux validations d’API PHP.

### Ajouter le `--coming-version` option

Vous pouvez comparer votre installation Adobe Commerce actuelle à n’importe quelle version d’Adobe Commerce. `>=2.3` en utilisant la variable `--coming-version` .

Vous devez fournir la version comme paramètre lors de l’exécution de la variable `upgrade:check` command :

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Où `-c, --coming-version[=COMING-VERSION]` fait référence à la version ciblée Adobe Commerce.

Certaines limites s’appliquent lors de l’exécution de la variable `--coming-version`:

- Ce paramètre fait référence à toute balise qui identifie une version spécifique d’Adobe Commerce.
- Il s&#39;agit d&#39;une obligation explicite; fournir uniquement la valeur de ne fonctionne pas.
- Fournissez la version de la balise sans guillemets (ni simples ni doubles) : ~~&#39;2.4.1-develop&#39;~~.
- Vous ne devez PAS fournir d’anciennes versions que celle que vous avez installée actuellement, ni plus de 2.3, qui est la plus ancienne version prise en charge actuellement.

## Utilisez la variable `core:code:changes` command

Vous pouvez comparer votre installation Adobe Commerce actuelle pour vérifier si le code principal d’Adobe Commerce a été modifié pour mettre en oeuvre une personnalisation. Cette commande affiche uniquement une liste des modifications principales :

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Où les arguments sont les suivants :

- `<dir>`: Répertoire d’installation d’Adobe Commerce.
- `<vanilla dir>`: Répertoire d’installation d’Adobe Commerce vanilla.

Options disponibles pour la variable `core:code:changes` command :

| **Commande** | **Options disponibles** |
|----------------|-----------------|
| `core:code:changes` | `--help`: Renvoie tous les éléments disponibles `--help` options. |

>[!NOTE]
>
> Il est recommandé d’exclure le code personnalisé du code principal. Voir Adobe Commerce 2.4 [guide de mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) pour plus de bonnes pratiques de mise à niveau.

### Installation de vanille

A _vanille_ l’installation est une installation propre d’une balise ou d’une branche de version spécifiée pour une version spécifique.

Le `bin/uct core:code:changes` vérifie si votre système contient une instance Vanilla. Si c’est la première fois que vous utilisez une installation Vanilla, une question de ligne de commande interactive vous invite à télécharger le projet Vanilla à partir du référentiel Adobe Commerce (`https://repo.magento.com/`).

Vous pouvez exécuter une [!DNL Upgrade Compatibility Tool] avec la commande `--vanilla-dir` pour spécifier le répertoire d’installation d’Adobe Commerce vanilla.

Voir [Déploiement de l’instance Vanilla](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) pour plus d’informations.

## Utilisez la variable `refactor` command

Le [!DNL Upgrade Compatibility Tool] permet de résoudre automatiquement un ensemble réduit de problèmes :

- Fonctions qui étaient autorisées à être utilisées sans passer d’argument, mais avec une telle utilisation désormais obsolète.
- Utilisation de `$this` dans les modèles de Magento.
- Utilisation du mot-clé PHP `final` dans des méthodes privées.

Pour ce faire, exécutez le `refactor` command :

```bash
bin/uct refactor <dir>
```

Où `<dir>` est le répertoire dans lequel se trouve votre instance Adobe Commerce.

Options disponibles pour la variable `refactor` command :

| **Commande** | **Options disponibles** |
|----------------|-----------------|
| `refactor` | `--help`: Renvoie tous les éléments disponibles `--help` options. |

## Utilisez la variable `graphql:compare` command

Cette commande permet d’accéder au [!DNL Upgrade Compatibility Tool] pour analyser deux points d’entrée GraphQL et comparer leurs schémas en recherchant des modifications de rupture et dangereuses entre eux :

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Où les arguments sont les suivants :

- `<schema1>`: URL du point d’entrée pour l’installation existante.
- `<schema2>`: URL du point d’entrée pour l’installation Vanilla.

Options disponibles pour la variable `graphql:compare` command :

| **Commande** | **Options disponibles** |
|----------------|-----------------|
| `graphql:compare` | `--help`: Renvoie tous les éléments disponibles `--help` options. |

## Utilisez la variable `list` command

Pour renvoyer une liste de la variable [!DNL Upgrade Compatibility Tool] commandes disponibles, exécutez :

```bash
bin/uct list
```

## Utilisez la variable `--help` command

Pour afficher la variable [!DNL Upgrade Compatibility Tool] options générales de la commande et aide, exécutez :

```bash
bin/uct --help
```

qui renvoie une liste avec tous les éléments disponibles ; `help` options de la variable [!DNL Upgrade Compatibility Tool] dans une interface de ligne de commande :

```terminal
- -m, --module-path[=MODULE-PATH]: Path of the modules to be analysed
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

Cependant, il est possible d’exécuter `--help` comme option lors de l’exécution d’une commande spécifique. Cela renverra des `--help` pour cette commande spécifique.

Exemple de `upgrade:check` avec `--help` option :

```bash
bin/uct upgrade:check --help
```

Cela renvoie des options spécifiques qui peuvent être exécutées pour la variable `upgrade:check` command :

```terminal
--min-issue-level.
-i, --ignore-current-version-compatibility-issues.
```

## Suivre les bonnes pratiques d’Adobe Commerce

- Évitez d’avoir deux modules portant le même nom.
- Suivez Adobe Commerce [normes de codage](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).
- Adobe Commerce 2.4 [Guide de mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) bonnes pratiques.

## Optimiser vos résultats

Le [!DNL Upgrade Compatibility Tool] fournit un rapport contenant les résultats avec tous les problèmes identifiés par défaut sur votre projet. Vous pouvez optimiser les résultats pour vous concentrer sur les problèmes que vous devez corriger pour terminer la mise à niveau :

- Utiliser l’option `--ignore-current-version-compatibility-issues` lorsque vous souhaitez uniquement obtenir de nouveaux problèmes qui sont introduits avec la mise à jour de votre version actuelle vers la version ciblée dans votre [!DNL Upgrade Compatibility Tool] rapport.
- Ajouter le `--min-issue-level` , ce paramètre permet de définir le niveau de problème minimum afin de n’établir la priorité que sur les problèmes les plus importants de votre mise à niveau.
- Le [!DNL Upgrade Compatibility Tool] nécessite au moins 2 Go de mémoire vive pour fonctionner. Ce paramètre est recommandé pour éviter les problèmes en raison d’une faible limitation de mémoire. Le [!DNL Upgrade Compatibility Tool] affiche une question si vous exécutez le `upgrade:check` avec une valeur faible `memory_limit` .
- Si vous souhaitez analyser uniquement un certain fournisseur, module ou même répertoire, vous pouvez également spécifier le chemin d’accès comme option. Exécutez la variable `bin` avec l’option ajoutée `-m`. Cela permet à la variable [!DNL Upgrade Compatibility Tool] pour analyser indépendamment un module spécifique et aide à résoudre les problèmes de mémoire qui peuvent se produire lors de l’exécution de la variable [!DNL Upgrade Compatibility Tool]. Spécifiez la variable `-m` pour exécuter l’outil sur un module spécifique :

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

Où les arguments sont les suivants :

- `<dir>`: Répertoire d’installation d’Adobe Commerce.
- `[=MODULE-PATH]`: Répertoire de chemin d’accès au module spécifique.
