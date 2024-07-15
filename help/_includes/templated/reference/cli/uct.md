---
source-git-commit: cdd98c866623255d3aa2ebf3cdb3b704006d3053
workflow-type: tm+mt
source-wordcount: '1646'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Version** : 3.0.17

Cette référence contient 9 commandes disponibles via l’outil de ligne de commande `bin/uct`.
La liste initiale est générée automatiquement à l’aide de la commande `bin/uct list` sur Adobe Commerce.

Pour en savoir plus sur l’outil, voir [Aperçu](/help/upgrade/upgrade-compatibility-tool/overview.md).

>[!NOTE]
>
>Cette référence est générée à partir du code base de l’application. Pour modifier le contenu, vous pouvez mettre à jour le code source pour l’implémentation de commande correspondante dans le référentiel [codebase](https://github.com/magento) et envoyer vos modifications pour révision. Une autre méthode consiste à _Laisser un commentaire_ (trouvez le lien en haut à droite). Pour obtenir des instructions sur les contributions, voir [Contributions au code](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
```

Commande interne permettant de fournir des suggestions d’achèvement du shell


### `--shell`, `-s`

Le type de shell (&quot;bash&quot;)

- Requiert une valeur

### `--input`, `-i`

Tableau de jetons d’entrée (COMP_WORDS ou argv, par exemple)

- Valeur par défaut : `[]`
- Requiert une valeur

### `--current`, `-c`

Index du tableau &quot;input&quot; dans lequel se trouve le curseur (par exemple, COMP_CWORD)

- Requiert une valeur

### `--symfony`, `-S`

Version du script d’achèvement

- Requiert une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Lorsqu’aucune commande n’est fournie à l’aide de l’affichage de la commande de liste

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte pas de valeur

### `--no-ansi`

Négociez l’option &quot;—ansi&quot;

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-interaction`, `-n`

Ne posez aucune question interactive

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `completion`

```bash
bin/uct completion [--debug] [--] [<shell>]
```

Saut du script d’achèvement du shell


```
The completion command dumps the shell completion script required
to use shell autocompletion (currently only bash completion is supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    uct/bin/uct completion bash | sudo tee /etc/bash_completion.d/uct

Or dump the script to a local file and source it:

    uct/bin/uct completion bash > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/jenkins/workspace/gendocs-uct-cli/uct/bin/uct completion bash)"
```


### `shell`

Le type de shell (par exemple &quot;bash&quot;), la valeur de la variable d’environnement &quot;$SHELL&quot; sera utilisée si ce n’est pas le cas.


### `--debug`

Suivi du journal de débogage de fin

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Lorsqu’aucune commande n’est fournie à l’aide de l’affichage de la commande de liste

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte pas de valeur

### `--no-ansi`

Négociez l’option &quot;—ansi&quot;

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-interaction`, `-n`

Ne posez aucune question interactive

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `help`

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```

Afficher l’aide d’une commande


```
The help command displays help for a given command:

  uct/bin/uct help list

You can also output the help in other formats by using the --format option:

  uct/bin/uct help --format=xml list

To display the list of available commands, please use the list command.
```


### `command_name`

Nom de la commande

- Valeur par défaut : `help`


### `--format`

Format de sortie (txt, xml, json ou md)

- Valeur par défaut : `txt`
- Requiert une valeur

### `--raw`

Pour générer l’aide de la commande brute

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Lorsqu’aucune commande n’est fournie à l’aide de l’affichage de la commande de liste

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte pas de valeur

### `--no-ansi`

Négociez l’option &quot;—ansi&quot;

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-interaction`, `-n`

Ne posez aucune question interactive

- Valeur par défaut : `false`
- N’accepte pas de valeur


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


### `namespace`

Nom de l’espace de noms


### `--raw`

Pour générer la liste de commandes brute

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--format`

Format de sortie (txt, xml, json ou md)

- Valeur par défaut : `txt`
- Requiert une valeur

### `--short`

Pour ignorer les arguments de description des commandes

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Lorsqu’aucune commande n’est fournie à l’aide de l’affichage de la commande de liste

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte pas de valeur

### `--no-ansi`

Négociez l’option &quot;—ansi&quot;

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-interaction`, `-n`

Ne posez aucune question interactive

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `refactor`

```bash
bin/uct refactor <path>
```

Résout les problèmes qui peuvent être résolus automatiquement. Le code du chemin d’accès indiqué sera mis à jour.



### `path`

Chemin de résolution des problèmes dans .

- Obligatoire

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Lorsqu’aucune commande n’est fournie à l’aide de l’affichage de la commande de liste

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte pas de valeur

### `--no-ansi`

Négociez l’option &quot;—ansi&quot;

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-interaction`, `-n`

Ne posez aucune question interactive

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `core:code:changes`

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```

L’outil de compatibilité de mise à niveau est un outil de ligne de commande qui vérifie la compatibilité d’une instance Adobe Commerce avec une version spécifique en analysant tous les modules non Adobe Commerce installés dans celle-ci. Renvoie la liste des erreurs et avertissements que vous devez corriger avant d’effectuer une mise à niveau vers une nouvelle version du code Adobe Commerce.



### `dir`

Répertoire d’installation Adobe Commerce.

- Obligatoire

### `vanilla-dir`

Répertoire d’installation d’Adobe Commerce vanilla.


### `--output`, `-o`

Chemin du fichier vers lequel la sortie sera exportée (format Json)

- Accepte une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Lorsqu’aucune commande n’est fournie à l’aide de l’affichage de la commande de liste

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte pas de valeur

### `--no-ansi`

Négociez l’option &quot;—ansi&quot;

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-interaction`, `-n`

Ne posez aucune question interactive

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `dbschema:diff`

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Permet de répertorier les différences de schéma Adobe Commerce DB entre deux versions sélectionnées. Versions disponibles : 2.3.0 | 2.3.1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4-p1 | 2.3.4-p2 | 2.3.5 | 2.3.5-p1 | 2.3.5-p2 | 2.3.6 | 2.3.6-p1 | 2.3.7 | 2.3.7-p1 | 2.3.7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2.4.0 | 2.4.0-p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2-p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4-p1 | 2.4.5 | 2.4.4-p2 | 2.4.5-p1 | 2.4.4-p3 | 2.4.4-p4 | 2.4.4-p5 | 2.4.5-p2 | 2.4.5-p3 | 2.4.5-p4 | 2.4.6 | 2.4.6-p1 | 2.4.6-p2 | 2.4.7-beta1 | 2.4.4-p6 | 2.4.5-p5 | 2.4.6-p3 | 2.4.7-beta2 | 2.4.4-p7 | 2.4.5-p6 | 2.4.6-p4 | 2.4.7-beta3 | 2.4.7 | 2.4.6-p5 | 2.4.5-p7 | 2.4.4-p8 | 2.4.4-p9 | 2.4.5-p8 | 2.4.6-p6 | 2.4.7-p1



### `current-version`

version actuelle (par exemple, 2.3.2).

- Obligatoire

### `target-version`

version cible (par exemple, 2.4.5).

- Obligatoire

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Lorsqu’aucune commande n’est fournie à l’aide de l’affichage de la commande de liste

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte pas de valeur

### `--no-ansi`

Négociez l’option &quot;—ansi&quot;

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-interaction`, `-n`

Ne posez aucune question interactive

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `graphql:compare`

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```

Vérification de la compatibilité des schémas GraphQL



### `schema1`

URL du point d’entrée pointant vers le premier schéma GraphQL.

- Obligatoire

### `schema2`

URL du point d’entrée pointant vers le deuxième schéma GraphQL.

- Obligatoire

### `--output`, `-o`

Chemin du fichier vers lequel la sortie sera exportée (format JSON)

- Accepte une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Lorsqu’aucune commande n’est fournie à l’aide de l’affichage de la commande de liste

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte pas de valeur

### `--no-ansi`

Négociez l’option &quot;—ansi&quot;

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-interaction`, `-n`

Ne posez aucune question interactive

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `upgrade:check`

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```

L’outil de compatibilité de mise à niveau est un outil de ligne de commande qui vérifie la personnalisation d’une instance Adobe Commerce par rapport à une version spécifique en analysant tous les modules qui y sont installés. Renvoie la liste des erreurs et avertissements à corriger avant la mise à niveau vers la dernière version d’Adobe Commerce.



### `dir`

Répertoire d’installation Adobe Commerce.

- Obligatoire

### `--current-version`, `-a`

La version actuelle d’Adobe Commerce, la version de l’installation d’Adobe Commerce, sera utilisée si elle est omise.

- Accepte une valeur

### `--coming-version`, `-c`

Version d’Adobe Commerce cible. La dernière version stable publiée d’Adobe Commerce sera utilisée si elle est omise. Versions d’Adobe Commerce disponibles : 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.4-p2 \| 2.4.4-p3 \| 2.4.4-p4 \| 2.4.4-p5 \| 2.4.4-p6 \| 2.4.4-p7 \| 2.4.4-p8 \| 2.4.4-p9 \| 2.4.5 \| 2.4.5-p1 \| 2.4.5-p2 \| 2.4.5-p3 \| 2.4.5-p4 \| 2.4.5-p5 \| 2.4.5-p6 \| 2.4.5-p7 \| 2.4.5-p8 \| 2.4.6 \| 2.4.6-p1 \| 2.4.6-p2 \| 2.4.6-p3 \| 2.4.6-p4 \| 2.4.6-p5 \| 2.4.6-p6 \| 2.4.7-beta1 \| 2.4.7-beta2 \| 2.4.7-beta3 \| 2.4.7 \| 2.4.7-p1

- Accepte une valeur

### `--json-output-path`

Chemin du fichier dans lequel la sortie sera exportée au format json

- Accepte une valeur

### `--html-output-path`

Chemin du fichier dans lequel la sortie sera exportée au format HTML.

- Accepte une valeur

### `--min-issue-level`

Niveau de problème minimal à afficher dans le rapport (avertissement, erreur ou critique).

- Valeur par défaut : `warning`
- Accepte une valeur

### `--ignore-current-version-compatibility-issues`, `-i`

Ignorer les problèmes courants pour la version actuelle et à venir

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--context`

Contexte d&#39;exécution. Cette option est destinée à des fins d’intégration et n’affecte pas le résultat de l’exécution.

- Requiert une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Lorsqu’aucune commande n’est fournie à l’aide de l’affichage de la commande de liste

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte pas de valeur

### `--no-ansi`

Négociez l’option &quot;—ansi&quot;

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-interaction`, `-n`

Ne posez aucune question interactive

- Valeur par défaut : `false`
- N’accepte pas de valeur

