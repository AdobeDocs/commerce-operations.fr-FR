---
source-git-commit: e044459f849f35a4a1e161a191bc7497fcef9281
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 1%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->
**Version** : 3.0.25

Cette référence contient 9 commandes disponibles via l’outil de ligne de commande `bin/uct`.
La liste initiale est générée automatiquement à l’aide de la commande `bin/uct list` dans Adobe Commerce.

## Général

En savoir plus sur l’outil dans [Présentation](/help/upgrade/upgrade-compatibility-tool/overview.md).

Cette documentation de référence est générée à partir du code source de l’application. Pour modifier la documentation, vous devez ouvrir une requête de tirage pour la commande correspondante dans le référentiel [codebase](https://github.com/magento) approprié. Pour plus d’informations, voir [Contributions du code](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

### Options globales

#### `--help`, `-h`

Afficher l’aide pour la commande donnée. Lorsqu’aucune commande n’est fournie, afficher l’aide pour la commande de liste

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus verbose et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

#### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--no-interaction`, `-n`

Ne posez aucune question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `_complete`

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

Commande interne pour fournir des suggestions d&#39;achèvement du shell

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--shell`, `-s`

Le type de coque (« bash », « fish », « zsh »)

- Requiert une valeur

#### `--input`, `-i`

Tableau de jetons d’entrée (par exemple COMP_WORDS ou argv)

- Valeur par défaut : `[]`
- Requiert une valeur

#### `--current`, `-c`

Index du tableau « input » dans lequel se trouve le curseur (par exemple COMP_CWORD)

- Requiert une valeur

#### `--api-version`, `-a`

Version API du script d&#39;achèvement

- Requiert une valeur

#### `--symfony`, `-S`

obsolète

- Requiert une valeur


## `completion`

```bash
bin/uct completion [--debug] [--] [<shell>]
```

Vider le script de fin du shell

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    uct/bin/uct completion  | sudo tee /etc/bash_completion.d/uct

Or dump the script to a local file and source it:

    uct/bin/uct completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/jenkins/workspace/gendocs-uct-cli/uct/bin/uct completion )"
```

### Arguments

#### `shell`

Le type de shell (par exemple « bash »), la valeur de la variable d&#39;environnement « $SHELL » sera utilisée si elle n&#39;est pas indiquée

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--debug`

Faire apparaître dans le journal de débogage l’achèvement

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `help`

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```

Affichage de l’aide d’une commande

```
The help command displays help for a given command:

  uct/bin/uct help list

You can also output the help in other formats by using the --format option:

  uct/bin/uct help --format=xml list

To display the list of available commands, please use the list command.
```

### Arguments

#### `command_name`

Nom de la commande

- Valeur par défaut : `help`

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--format`

Le format de sortie (txt, xml, json ou md)

- Valeur par défaut : `txt`
- Requiert une valeur

#### `--raw`

Pour générer l’aide de la commande brute

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `list`

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Commandes de liste

```
The list command lists all commands:

  uct/bin/uct list

You can also display the commands for a specific namespace:

  uct/bin/uct list test

You can also output the information in other formats by using the --format option:

  uct/bin/uct list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  uct/bin/uct list --raw
```

### Arguments

#### `namespace`

Nom de l’espace de noms

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--raw`

Pour générer la liste de commandes brute

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--format`

Le format de sortie (txt, xml, json ou md)

- Valeur par défaut : `txt`
- Requiert une valeur

#### `--short`

Pour ignorer la description des arguments des commandes

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `refactor`

```bash
bin/uct refactor <path>
```

Résout les problèmes qui peuvent être résolus automatiquement. Le code du chemin d’accès fourni sera mis à jour.

### Arguments

#### `path`

Chemin d’accès à la résolution des problèmes dans .

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).


## `core:code:changes`

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```

L’outil de compatibilité de mise à niveau est un outil de ligne de commande qui vérifie une instance Adobe Commerce par rapport à une version spécifique en analysant tous les modules non-Adobe Commerce installés dans celle-ci. Renvoie une liste d’erreurs et d’avertissements que vous devez corriger avant d’effectuer la mise à niveau vers une nouvelle version du code Adobe Commerce.

### Arguments

#### `dir`

Répertoire d’installation d’Adobe Commerce.

- Obligatoire


#### `vanilla-dir`

Répertoire d’installation d’Adobe Commerce vanilla.

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--output`, `-o`

Chemin d’accès au fichier dans lequel la sortie sera exportée (format JSON)

- Accepte une valeur


## `dbschema:diff`

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Permet de répertorier les différences de schéma de base de données Adobe Commerce entre deux versions sélectionnées. Versions disponibles : 2.3.0 | 2,3,1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2,3,4 | 2.3.4-p1 | 2.3.4-p2 | 2,3,5 | 2.3.5-p1 | 2.3.5-p2 | 2,3,6 | 2.3.6-p1 | 2,3,7 | 2.3.7-p1 | 2.3.7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2.4.0 | 2.4.0-p1 | 2,4,1 | 2.4.1-p1 | 2,4,2 | 2.4.2-p1 | 2.4.2-p2 | 2,4,3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2,4,4 | 2.4.4-p1 | 2,4,5 | 2.4.4-p2 | 2.4.5-p1 | 2.4.4-p3 | 2.4.4-p4 | 2.4.4-p5 | 2.4.5-p2 | 2.4.5-p3 | 2.4.5-p4 | 2,4,6 | 2.4.6-p1 | 2.4.6-p2 | 2.4.7-beta1 | 2.4.4-p6 | 2.4.5-p5 | 2.4.6-p3 | 2.4.7-beta2 | 2.4.4-p7 | 2.4.5-p6 | 2.4.6-p4 | 2.4.7-bêta3 | 2,4,7 | 2.4.6-p5 | 2.4.5-p7 | 2.4.4-p8 | 2.4.4-p9 | 2.4.5-p8 | 2.4.6-p6 | 2.4.7-p1 | 2.4.4-p10 | 2.4.5-p9 | 2.4.6-p7 | 2.4.7-p2 | 2.4.4-p11 | 2.4.5-p10 | 2.4.6-p8 | 2.4.7-p3 | 2.4.8-beta1 | 2.4.4-p12 | 2.4.5-p11 | 2.4.6-p9 | 2.4.7-p4 | 2.4.8-beta2 | 2.4.4-p13 | 2.4.5-p12 | 2.4.6-p10 | 2.4.7-p5 | 2,4,8 | 2.4.9-alpha2 | 2.4.8-p2 | 2.4.7-p7 | 2.4.6-p12 | 2.4.5-p14 | 2.4.4-p15 | 2.4.9-alpha1 | 2.4.8-p1 | 2.4.7-p6 | 2.4.6-p11 | 2.4.5-p13 | 2.4.4-p14 | 2.4.9-alpha3 | 2.4.8-p3 | 2.4.7-p8 | 2.4.6-p13 | 2.4.5-p15 | 2.4.4-p16

### Arguments

#### `current-version`

version actuelle (par exemple, 2.3.2).

- Obligatoire


#### `target-version`

version cible (par exemple, 2.4.5).

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).


## `graphql:compare`

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```

Vérification de la compatibilité des schémas GraphQL

### Arguments

#### `schema1`

URL du point d’entrée pointant vers le premier schéma GraphQL.

- Obligatoire


#### `schema2`

URL du point d’entrée pointant vers le deuxième schéma GraphQL.

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--output`, `-o`

Chemin d’accès au fichier dans lequel la sortie sera exportée (format JSON)

- Accepte une valeur


## `upgrade:check`

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```

L’outil de compatibilité de mise à niveau est un outil de ligne de commande qui vérifie une instance personnalisée Adobe Commerce par rapport à une version spécifique en analysant tous les modules installés dans celle-ci. Renvoie une liste d’erreurs et d’avertissements à corriger avant la mise à niveau vers la dernière version d’Adobe Commerce.

### Arguments

#### `dir`

Répertoire d’installation d’Adobe Commerce.

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--current-version`, `-a`

La version actuelle d’Adobe Commerce et la version de l’installation d’Adobe Commerce seront utilisées si elles sont omises.

- Accepte une valeur

#### `--coming-version`, `-c`

Version Adobe Commerce cible. La dernière version stable d’Adobe Commerce publiée sera utilisée si elle est omise. Versions d’Adobe Commerce disponibles : 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.4-p2 \| 2.4.4-p3 \| 2.4.4-p4 \| 2.4.4-p5 \| 2.4.4-p6 \| 2.4.4-p7 \| 2.4.4-p8 \| 2.4.4-p9 \| 2.4.4-p10 \| 2.4.4-p11 \| 2.4.4-p12 \| 2.4.4-p13 \| 2.4.4-p14 \| 2.4.4-p15 \| 2.4.4-p16 \| 2.4.5 \| 2.4.5-p1 \| 2.4.5-p2 \| 2.4.5-p3 \| 2.4.5-p4 \| 2.4.5-p5 \| 2.4.5-p6 \| 2.4.5-p7 \| 2.4.5-p8 \| 2.4.5-p9 \| 2.4.5-p10 \| 2.4.5-p11 \| 2.4.5-p12 \| 2.4.5-p13 \| 2.4.5-p14 \| 2.4.5-p15 \| 2.4.6 \| 2.4.6-p1 \| 2.4.6-p2 \| 2.4.6-p3 \| 2.4.6-p4 \| 2.4.6-p5 \| 2.4.6-p6 \| 2.4.6-p7 \| 2.4.6-p8 \| 2.4.6-p9 \| 2.4.6-p10 \| 2.4.6-p11 \| 2.4.6-p12 \| 2.4.6-p13 \| 2.4.7-beta1 \| 2.4.7-beta2 \| 2.4.7-beta3 \| 2.4.7 \| 2.4.7-p1 \| 2.4.7-p2 \| 2.4.7-p3 \| 2.4.7-p4 \| 2.4.7-p5 \| 2.4.7-p6 \| 2.4.7-p7 \| 2.4.7-p8 \| 2.4.8-beta1 \| 2.4.8-beta2 \| 2.4.8 \| 2.4.8-p1 \| 2.4.8-p2 \| 2.4.8-p3 \| 2.4.9-alpha1 \| 2.4.9-alpha2 \| 2.4.9-alpha3

- Accepte une valeur

#### `--json-output-path`

Chemin d’accès au fichier dans lequel la sortie sera exportée au format JSON

- Accepte une valeur

#### `--html-output-path`

Chemin du fichier où sera exportée la sortie au format HTML

- Accepte une valeur

#### `--min-issue-level`

Niveau de problème minimal à afficher dans le rapport (avertissement, erreur ou critique).

- Valeur par défaut : `warning`
- Accepte une valeur

#### `--ignore-current-version-compatibility-issues`, `-i`

Ignorer les problèmes courants de la version actuelle et des versions à venir

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--context`

Contexte d’exécution. Cette option est proposée à des fins d’intégration et n’affecte pas le résultat de l’exécution.

- Requiert une valeur

