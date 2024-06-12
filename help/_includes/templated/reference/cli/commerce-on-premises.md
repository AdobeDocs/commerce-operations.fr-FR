---
source-git-commit: 1f8fda87e0d39fdcf2372f72373a0b2ea486d25a
workflow-type: tm+mt
source-wordcount: '21185'
ht-degree: 0%

---
# bin/magento (Adobe Commerce sur site)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->

**Version**: 2.4.7-p1

Cette référence contient 141 commandes disponibles via le `bin/magento` outil de ligne de commande.
La liste initiale est générée automatiquement à l’aide de la fonction `bin/magento list` dans Adobe Commerce.
Utilisez la variable [&quot;Ajout de commandes d’interface de ligne de commande&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) pour ajouter une commande d’interface de ligne de commande personnalisée.

>[!NOTE]
>
>Vous pouvez appeler `bin/magento` Commandes d’interface de ligne de commande à l’aide de raccourcis au lieu du nom de commande complet. Par exemple, vous pouvez appeler `bin/magento setup:upgrade` using `bin/magento s:up`, `bin/magento s:upg`. Voir [syntaxe de raccourci](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) pour comprendre comment utiliser des raccourcis avec n’importe quelle commande d’interface de ligne de commande.

>[!NOTE]
>
>Cette référence est générée à partir du code base de l’application. Pour modifier le contenu, vous pouvez mettre à jour le code source de l’implémentation de la commande correspondante dans le [codebase](https://github.com/magento) et envoyer vos modifications pour révision. Une autre méthode consiste à _Donnez-nous vos commentaires_ (trouvez le lien en haut à droite). Pour obtenir des instructions sur les contributions, voir [Contributions au code](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

Commande interne permettant de fournir des suggestions d’achèvement du shell


### `--shell`, `-s`

Le type de conteneur (&quot;bash&quot;, &quot;fish&quot;, &quot;zsh&quot;)

- Requiert une valeur

### `--input`, `-i`

Un tableau de jetons d’entrée (par exemple, &quot;C.C._WORDS&quot; ou &quot;argv&quot;)

- Valeur par défaut : `[]`
- Requiert une valeur

### `--current`, `-c`

Index de la table &quot;input&quot; dans laquelle se trouve le curseur (par exemple, Throne_CWORD)

- Requiert une valeur

### `--api-version`, `-a`

Version API du script d’achèvement

- Requiert une valeur

### `--symfony`, `-S`

obsolète

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
bin/magento completion [--debug] [--] [<shell>]
```

Saut du script d’achèvement du shell


```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    bin/magento completion  | sudo tee /etc/bash_completion.d/magento

Or dump the script to a local file and source it:

    bin/magento completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/www/html/magento2/bin/magento completion )"
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
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```

Afficher l’aide d’une commande


```
The help command displays help for a given command:

  bin/magento help list

You can also output the help in other formats by using the --format option:

  bin/magento help --format=xml list

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
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Commandes de liste


```
The list command lists all commands:

  bin/magento list

You can also display the commands for a specific namespace:

  bin/magento list test

You can also output the information in other formats by using the --format option:

  bin/magento list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  bin/magento list --raw
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


## `admin:adobe-ims:disable`

```bash
bin/magento admin:adobe-ims:disable
```

Désactivation du module Adobe IMS


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


## `admin:adobe-ims:enable`

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

Activez le module Adobe IMS.


### `--organization-id`, `-o`

Définissez l’ID d’organisation pour la configuration Adobe IMS. Obligatoire lors de l’activation du module

- Accepte une valeur

### `--client-id`, `-c`

Définissez l’ID client pour la configuration Adobe IMS. Obligatoire lors de l’activation du module

- Accepte une valeur

### `--client-secret`, `-s`

Définissez le secret client pour la configuration Adobe IMS. Obligatoire lors de l’activation du module

- Accepte une valeur

### `--2fa`, `-t`

Vérifiez si 2FA est activé pour l’organisation dans Adobe Admin Console. Obligatoire lors de l’activation du module

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


## `admin:adobe-ims:info`

```bash
bin/magento admin:adobe-ims:info
```

Informations sur la configuration du module Adobe IMS


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


## `admin:adobe-ims:status`

```bash
bin/magento admin:adobe-ims:status
```

État du module Adobe IMS


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


## `admin:user:create`

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Création d’un administrateur


### `--admin-user`

(Obligatoire) Utilisateur administrateur

- Requiert une valeur

### `--admin-password`

(Obligatoire) Mot de passe administrateur

- Requiert une valeur

### `--admin-email`

(Obligatoire) Adresse électronique de l’administrateur

- Requiert une valeur

### `--admin-firstname`

(Obligatoire) Prénom de l’administrateur

- Requiert une valeur

### `--admin-lastname`

(Obligatoire) Nom de l’administrateur

- Requiert une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `admin:user:unlock`

```bash
bin/magento admin:user:unlock <username>
```

Déverrouiller le compte d’administrateur


```
This command unlocks an admin account by its username.
To unlock:
      bin/magento admin:user:unlock username
```


### `username`

Nom d’utilisateur administrateur à déverrouiller

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


## `app:config:dump`

```bash
bin/magento app:config:dump [<config-types>...]
```

Créer un vidage de l’application



### `config-types`

Liste de types de configuration séparés par des espaces, ou omettez de vider tous les [portées, système, thèmes, i18n]

- Valeur par défaut : `[]`

- Tableau

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


## `app:config:import`

```bash
bin/magento app:config:import
```

Importer des données à partir de fichiers de configuration partagés vers le stockage de données approprié


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


## `app:config:status`

```bash
bin/magento app:config:status
```

Vérifie si la propagation de la configuration nécessite une mise à jour


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


## `braintree:migrate`

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

Migration des cartes stockées d’une base de données Magento 1


### `--host`

Nom d’hôte/adresse IP. Le port est facultatif

- Requiert une valeur

### `--dbname`

Nom de la base

- Requiert une valeur

### `--username`

Nom d’utilisateur de la base de données. Doit avoir un accès en lecture

- Requiert une valeur

### `--password`

Mot de passe

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


## `cache:clean`

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Nettoie le ou les types de cache.



### `types`

Liste de types de cache séparés par des espaces, ou omettez de les appliquer à tous les types de cache.

- Valeur par défaut : `[]`

- Tableau

### `--bootstrap`

ajouter ou remplacer les paramètres de l’amorçage

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


## `cache:disable`

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Désactive le ou les types de cache



### `types`

Liste de types de cache séparés par des espaces, ou omettez de les appliquer à tous les types de cache.

- Valeur par défaut : `[]`

- Tableau

### `--bootstrap`

ajouter ou remplacer les paramètres de l’amorçage

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


## `cache:enable`

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Active le ou les types de cache



### `types`

Liste de types de cache séparés par des espaces, ou omettez de les appliquer à tous les types de cache.

- Valeur par défaut : `[]`

- Tableau

### `--bootstrap`

ajouter ou remplacer les paramètres de l’amorçage

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


## `cache:flush`

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Efface le stockage du cache utilisé par les types de cache.



### `types`

Liste de types de cache séparés par des espaces, ou omettez de les appliquer à tous les types de cache.

- Valeur par défaut : `[]`

- Tableau

### `--bootstrap`

ajouter ou remplacer les paramètres de l’amorçage

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


## `cache:status`

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

Vérifie l’état du cache


### `--bootstrap`

ajouter ou remplacer les paramètres de l’amorçage

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


## `catalog:images:resize`

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

Crée des images de produit redimensionnées.


### `--async`, `-a`

Redimensionner l’image en mode asynchrone

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--skip_hidden_images`

Ne pas traiter les images marquées comme masquées dans la page du produit

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


## `catalog:product:attributes:cleanup`

```bash
bin/magento catalog:product:attributes:cleanup
```

Supprime les attributs de produit inutilisés.


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


## `cms:wysiwyg:restrict`

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

Définissez si vous souhaitez imposer la validation du contenu du HTML utilisateur ou afficher un avertissement à la place.



### `restrict`

y\n

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


## `config:sensitive:set`

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

Définition de valeurs de configuration sensibles



### `path`

Chemin de configuration, par exemple groupe/section/nom_champ


### `value`

Valeur de configuration


### `--interactive`, `-i`

Activation du mode interactif pour définir toutes les variables sensibles

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--scope`

Portée de la configuration, si elle n’est pas définie, utilisez &quot;default&quot;

- Valeur par défaut : `default`
- Accepte une valeur

### `--scope-code`

Code d’étendue pour la configuration, chaîne vide par défaut

- Par défaut : &quot;
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


## `config:set`

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

Modification de la configuration du système



### `path`

Chemin de configuration au format section/groupe/nom_champ

- Obligatoire

### `value`

Valeur de configuration

- Obligatoire

### `--scope`

Étendue de configuration (par défaut, site web ou magasin)

- Valeur par défaut : `default`
- Requiert une valeur

### `--scope-code`

Code d’étendue (requis uniquement si la portée n’est pas &quot;par défaut&quot;)

- Requiert une valeur

### `--lock-env`, `-e`

Verrouiller la valeur qui empêche la modification dans l’administrateur (sera enregistrée dans app/etc/env.php)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--lock-config`, `-c`

Verrouiller et partager la valeur avec d’autres installations empêche la modification dans l’Admin (sera enregistrée dans app/etc/config.php).

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--lock`, `-l`

Obsolète, utilisez plutôt l’option —lock-env .

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


## `config:show`

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

Affiche la valeur de configuration d’un chemin donné. Si le chemin n’est pas spécifié, toutes les valeurs enregistrées s’affichent.



### `path`

Chemin de configuration, par exemple section_id/group_id/field_id


### `--scope`

Portée de la configuration, si elle n’est pas spécifiée, la portée &quot;par défaut&quot; est utilisée.

- Valeur par défaut : `default`
- Accepte une valeur

### `--scope-code`

Code d’étendue (requis uniquement si la portée n’est pas `default`)

- Par défaut : &quot;
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


## `cron:install`

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

Génère et installe crontab pour l’utilisateur actuel


### `--force`, `-f`

Forcer l’installation des tâches

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--non-optional`, `-d`

Installer uniquement les tâches non facultatives (par défaut)

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


## `cron:remove`

```bash
bin/magento cron:remove
```

Supprime les tâches de crontab


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


## `cron:run`

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

Exécute les tâches par programmation.


### `--group`

Exécuter des tâches uniquement à partir d’un groupe spécifié

- Requiert une valeur

### `--exclude-group`

Exclure les tâches du groupe spécifié

- Valeur par défaut : `[]`
- Accepte plusieurs valeurs

### `--bootstrap`

Ajout ou remplacement des paramètres de l’amorçage

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


## `customer:hash:upgrade`

```bash
bin/magento customer:hash:upgrade
```

Mise à niveau du hachage du client en fonction du dernier algorithme


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


## `deploy:mode:set`

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

Définissez le mode d’application.



### `mode`

Le mode d’application à définir. Les options disponibles sont &quot;développeur&quot; ou &quot;production&quot;

- Obligatoire

### `--skip-compilation`, `-s`

Ignore l’effacement et la régénération du contenu statique (code généré, CSS prétraité et ressources dans pub/static/)

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


## `deploy:mode:show`

```bash
bin/magento deploy:mode:show
```

Affiche le mode d’application actuel.


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


## `dev:di:info`

```bash
bin/magento dev:di:info <class>
```

Fournit des informations sur la configuration de l’injection de dépendance pour la commande.



### `class`

Nom de la classe

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


## `dev:email:newsletter-compatibility-check`

```bash
bin/magento dev:email:newsletter-compatibility-check
```

Analyse les modèles de newsletter à la recherche de problèmes potentiels de compatibilité de l’utilisation des variables


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


## `dev:email:override-compatibility-check`

```bash
bin/magento dev:email:override-compatibility-check
```

Analyse les remplacements de modèles de courrier électronique pour détecter des problèmes éventuels de compatibilité de l’utilisation des variables


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


## `dev:profiler:disable`

```bash
bin/magento dev:profiler:disable
```

Désactivez le profileur.


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


## `dev:profiler:enable`

```bash
bin/magento dev:profiler:enable [<type>]
```

Activez le profileur.



### `type`

Type de profil


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


## `dev:query-log:disable`

```bash
bin/magento dev:query-log:disable
```

Désactivation de la journalisation des requêtes DB


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


## `dev:query-log:enable`

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

Activation de la journalisation des requêtes DB


### `--include-all-queries`

Consignez toutes les requêtes. [true\|false]

- Valeur par défaut : `true`
- Accepte une valeur

### `--query-time-threshold`

Seuils de temps de requête.

- Valeur par défaut : `0.001`
- Accepte une valeur

### `--include-call-stack`

Inclure la pile d’appels. [true\|false]

- Valeur par défaut : `true`
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


## `dev:source-theme:deploy`

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

Collecte et publie les fichiers source pour le thème.



### `file`

Fichiers à prétraiter (le fichier doit être spécifié sans extension)

- Valeur par défaut : `css/styles-mcss/styles-l`

- Tableau

### `--type`

Type de fichier source : [less]

- Valeur par défaut : `less`
- Requiert une valeur

### `--locale`

Paramètres régionaux : [en_US]

- Valeur par défaut : `en_US`
- Requiert une valeur

### `--area`

Zone : [frontend\|adminhtml]

- Valeur par défaut : `frontend`
- Requiert une valeur

### `--theme`

Thème : [Fournisseur/thème]

- Valeur par défaut : `Magento/luma`
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


## `dev:template-hints:disable`

```bash
bin/magento dev:template-hints:disable
```

Désactivez les conseils de modèle front-end. Une purge du cache peut être nécessaire.


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


## `dev:template-hints:enable`

```bash
bin/magento dev:template-hints:enable
```

Activez les conseils sur les modèles front-end. Une purge du cache peut être nécessaire.


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


## `dev:template-hints:status`

```bash
bin/magento dev:template-hints:status
```

Afficher l’état des conseils de modèle front-end.


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


## `dev:tests:run`

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

Exécution de tests



### `type`

Type de test à exécuter. Types disponibles : all, unit, integration, integration-all, static, static-all, integrity, legacy, default

- Valeur par défaut : `default`


### `--arguments`, `-c`

Arguments supplémentaires pour PHPUnit. Exemple : &quot;-c&#39;—filter=MyTest&#39;&quot; (aucun espace)

- Par défaut : &quot;
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


## `dev:urn-catalog:generate`

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

Génère le catalogue des URL vers les mappages *.xsd pour l’IDE à mettre en surbrillance le xml.



### `path`

Chemin d’accès au fichier pour générer le catalogue. Pour PhpStorm, utilisez .idea/misc.xml

- Obligatoire

### `--ide`

Format dans lequel le catalogue sera généré. Pris en charge : [phpstorm, vscode]

- Valeur par défaut : `phpstorm`
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


## `dev:xml:convert`

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

Convertit un fichier XML à l’aide de feuilles de style XSL



### `xml-file`

Chemin d’accès au fichier XML qui va être transformé

- Obligatoire

### `processor`

Chemin vers la feuille de style XSL qui sera appliquée au fichier XML

- Obligatoire

### `--overwrite`, `-o`

Remplacer le fichier XML

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


## `downloadable:domains:add`

```bash
bin/magento downloadable:domains:add [<domains>...]
```

Ajout de domaines à la liste blanche des domaines téléchargeables



### `domains`

Nom des domaines

- Valeur par défaut : `[]`

- Tableau

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


## `downloadable:domains:remove`

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

Suppression de domaines de la liste blanche des domaines téléchargeables



### `domains`

Noms de domaine

- Valeur par défaut : `[]`

- Tableau

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


## `downloadable:domains:show`

```bash
bin/magento downloadable:domains:show
```

Afficher la liste blanche des domaines téléchargeables


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


## `encryption:payment-data:update`

```bash
bin/magento encryption:payment-data:update
```

Recrypte les données de carte de crédit chiffrées à l’aide du dernier chiffrement.


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


## `events:create-event-provider`

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]events:provider:create 
```

Créez un fournisseur d’événements personnalisés dans les événements d’Adobe I/O pour cette instance. Si vous ne spécifiez pas les options de libellé et de description, elles doivent être définies dans le fichier système app/etc/event-types.json .


### `--label`

Un libellé pour définir votre fournisseur personnalisé.

- Accepte une valeur

### `--description`

Une description de votre fournisseur.

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


## `events:generate:module`

```bash
bin/magento events:generate:module
```

Générer un module basé sur une liste de modules externes


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


## `events:info`

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```

Renvoie la charge utile de l’événement spécifié.



### `event-code`

Code d’événement

- Obligatoire

### `--depth`

Le nombre de niveaux dans la payload de l’événement à renvoyer.

- Valeur par défaut : `2`
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


## `events:list`

```bash
bin/magento events:list
```

Affiche la liste des événements abonnés.


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


## `events:list:all`

```bash
bin/magento events:list:all <module_name>
```

Renvoie une liste d’événements abonnées définis dans le module spécifié



### `module_name`

Nom du module

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


## `events:metadata:populate`

```bash
bin/magento events:metadata:populate
```

Crée des métadonnées dans Adobe I/O à partir de la liste de configuration (configurations XML et application).


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


## `events:provider:info`

```bash
bin/magento events:provider:info
```

Renvoie des détails sur le fournisseur d’événements configuré


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


## `events:registrations:list`

```bash
bin/magento events:registrations:list
```

Répertorie les enregistrements d’événement dans votre projet App Builder


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


## `events:subscribe`

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [-d|--destination DESTINATION] [--hipaaAuditRequired] [--] <event-code>
```

Abonne à l&#39;événement



### `event-code`

Code d’événement

- Obligatoire

### `--force`, `-f`

Force l’abonnement à l’événement spécifié, même s’il n’a pas été défini localement.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--fields`

Liste des champs de la payload des données d’événement.

- Valeur par défaut : `[]`
- Requiert une valeur

### `--parent`

Code d’événement parent pour un abonnement à un événement avec des règles.

- Requiert une valeur

### `--rules`

La liste des règles de l’abonnement à l’événement, où chaque règle est formatée sous la forme &quot;champ\|opérateur\|valeur&quot;.

- Valeur par défaut : `[]`
- Requiert une valeur

### `--priority`, `-p`

Permet d’accélérer la transmission de cet événement. Définissez cette option pour les événements qui doivent être diffusés immédiatement. Par défaut, les événements sont envoyés par cron une fois par minute.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--destination`, `-d`

Destination de cet événement. Spécifiez cette option pour les événements qui doivent être diffusés vers la destination personnalisée.

- Valeur par défaut : `default`
- Requiert une valeur

### `--hipaaAuditRequired`

Indique que l’événement contient des données soumises au contrôle HIPAA.

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


## `events:sync-events-metadata`

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

Synchroniser les métadonnées d’événement pour cette instance


### `--delete`, `-d`

Suppression des métadonnées d’événements devenues inutiles

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


## `events:unsubscribe`

```bash
bin/magento events:unsubscribe <event-code>
```

Supprime l’abonnement à l’événement fourni.



### `event-code`

Code d’événement à désabonner de

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


## `i18n:collect-phrases`

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

Détecte les expressions dans le code base



### `directory`

Chemin du répertoire à analyser. Non nécessaire si l’indicateur —magento est défini


### `--output`, `-o`

Chemin (y compris le nom du fichier) vers un fichier de sortie. Si aucun fichier n’est spécifié, la valeur par défaut est stdout.

- Requiert une valeur

### `--magento`, `-m`

Utilisez le paramètre —magento pour analyser le code base du Magento actuel. Omettez le paramètre si un répertoire est spécifié.

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


## `i18n:pack`

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

Enregistre le package de langue



### `source`

Chemin d’accès au fichier du dictionnaire source avec traduction

- Obligatoire

### `locale`

Paramètre régional cible du dictionnaire, par exemple &quot;de_DE&quot;

- Obligatoire

### `--mode`, `-m`

Mode d’enregistrement pour le dictionnaire - &quot;replace&quot; - replace language pack par new - &quot;merge&quot; - merge des modules de langue, par défaut &quot;replace&quot;

- Valeur par défaut : `replace`
- Requiert une valeur

### `--allow-duplicates`, `-d`

Utilisez le paramètre —allow-duplicates pour enregistrer les doublons de traduction. Sinon, omettez le paramètre .

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


## `i18n:uninstall`

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

Désinstallation des packages de langue



### `package`

Nom du package de langue

- Valeur par défaut : `[]`

- Obligatoire
- Tableau

### `--backup-code`, `-b`

Sauvegarder le code et les fichiers de configuration (à l’exclusion des fichiers temporaires)

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


## `indexer:info`

```bash
bin/magento indexer:info
```

Affiche les indexeurs autorisés


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


## `indexer:reindex`

```bash
bin/magento indexer:reindex [<index>...]
```

Réindexation des données



### `index`

Liste de types d’index séparés par des espaces ou omettre de s’appliquer à tous les index.

- Valeur par défaut : `[]`

- Tableau

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


## `indexer:reset`

```bash
bin/magento indexer:reset [<index>...]
```

Réinitialise l’état de l’indexeur sur non valide



### `index`

Liste de types d’index séparés par des espaces ou omettre de s’appliquer à tous les index.

- Valeur par défaut : `[]`

- Tableau

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


## `indexer:set-dimensions-mode`

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

Définition du mode Dimensions de l’indexeur



### `indexer`

Indexer name [catalog_product_price|catalogpermissions_category]


### `mode`

Modes de dimension de l’indexeur catalog_product_price none,website,customer_group,website_and_customer_group catalogpermissions_category none,customer_group


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


## `indexer:set-mode`

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

Définit le type de mode d’index



### `mode`

Type de mode Indexer [temps réel|planning]


### `index`

Liste de types d’index séparés par des espaces ou omettre de s’appliquer à tous les index.

- Valeur par défaut : `[]`

- Tableau

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


## `indexer:set-status`

```bash
bin/magento indexer:set-status <status> [<index>...]
```

Définit l’état de l’indexeur spécifié



### `status`

Type d’état de l’indexeur [non valide|suspendu|valide]

- Obligatoire

### `index`

Liste de types d’index séparés par des espaces ou omettre de s’appliquer à tous les index.

- Valeur par défaut : `[]`

- Tableau

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


## `indexer:show-dimensions-mode`

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

Affiche le mode de Dimension de l’indexeur.



### `indexer`

Liste de types d’index séparés par des espaces ou omit à appliquer à tous les index (catalog_product_price,catalogpermissions_category)

- Valeur par défaut : `[]`

- Tableau

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


## `indexer:show-mode`

```bash
bin/magento indexer:show-mode [<index>...]
```

Affiche le mode Index.



### `index`

Liste de types d’index séparés par des espaces ou omettre de s’appliquer à tous les index.

- Valeur par défaut : `[]`

- Tableau

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


## `indexer:status`

```bash
bin/magento indexer:status [<index>...]
```

Affiche l’état de l’indexeur.



### `index`

Liste de types d’index séparés par des espaces ou omettre de s’appliquer à tous les index.

- Valeur par défaut : `[]`

- Tableau

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


## `info:adminuri`

```bash
bin/magento info:adminuri
```

Affiche l’URI d’administration du Magento


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


## `info:backups:list`

```bash
bin/magento info:backups:list
```

Imprime la liste des fichiers de sauvegarde disponibles.


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


## `info:currency:list`

```bash
bin/magento info:currency:list
```

Affiche la liste des devises disponibles.


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


## `info:dependencies:show-framework`

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

Affiche le nombre de dépendances sur la structure du Magento


### `--output`, `-o`

Nom de fichier du rapport

- Valeur par défaut : `framework-dependencies.csv`
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


## `info:dependencies:show-modules`

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

Affiche le nombre de dépendances entre les modules


### `--output`, `-o`

Nom de fichier du rapport

- Valeur par défaut : `modules-dependencies.csv`
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


## `info:dependencies:show-modules-circular`

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

Affiche le nombre de dépendances circulaires entre les modules.


### `--output`, `-o`

Nom de fichier du rapport

- Valeur par défaut : `modules-circular-dependencies.csv`
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


## `info:language:list`

```bash
bin/magento info:language:list
```

Affiche la liste des paramètres régionaux de langue disponibles.


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


## `info:timezone:list`

```bash
bin/magento info:timezone:list
```

Affiche la liste des fuseaux horaires disponibles.


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


## `inventory:reservation:create-compensations`

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

Créer des réserves par des arguments de compensation fournis



### `compensations`

Liste des arguments de compensation au format &quot;:::&quot;

- Valeur par défaut : `[]`

- Tableau

### `--raw`, `-r`

Sortie brute

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


## `inventory:reservation:list-inconsistencies`

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

Afficher toutes les commandes et produits présentant des incohérences de quantité vendable


### `--complete-orders`, `-c`

Afficher uniquement les incohérences pour les commandes terminées

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--incomplete-orders`, `-i`

Afficher uniquement les incohérences pour les commandes incomplètes

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--bunch-size`, `-b`

Définit le nombre de commandes qui seront chargées simultanément.

- Valeur par défaut : `50`
- Accepte une valeur

### `--raw`, `-r`

Sortie brute

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


## `inventory-geonames:import`

```bash
bin/magento inventory-geonames:import <countries>...
```

Télécharger et importer des noms géographiques pour l’algorithme de sélection de source



### `countries`

Liste des codes pays à importer

- Valeur par défaut : `[]`

- Obligatoire
- Tableau

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


## `maintenance:allow-ips`

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

Définit les adresses IP exemptées du mode de maintenance



### `ip`

Adresses IP autorisées

- Valeur par défaut : `[]`

- Tableau

### `--none`

Effacer les adresses IP autorisées

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--add`

Ajouter l’adresse IP à la liste existante

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `maintenance:disable`

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Désactive le mode de maintenance


### `--ip`

Adresses IP autorisées (utilisez &quot;none&quot; pour effacer la liste IP autorisée)

- Valeur par défaut : `[]`
- Requiert une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `maintenance:enable`

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Active le mode de maintenance


### `--ip`

Adresses IP autorisées (utilisez &quot;none&quot; pour effacer la liste IP autorisée)

- Valeur par défaut : `[]`
- Requiert une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `maintenance:status`

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Affiche l’état du mode de maintenance


### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `media-content:sync`

```bash
bin/magento media-content:sync
```

Synchronisation du contenu avec les ressources


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


## `media-gallery:sync`

```bash
bin/magento media-gallery:sync
```

Synchronisation du stockage des médias et des ressources multimédias dans la base de données


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


## `module:config:status`

```bash
bin/magento module:config:status
```

Vérifie la configuration des modules dans le fichier &#39;app/etc/config.php&#39; et indique s&#39;ils sont à jour ou non


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


## `module:disable`

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Désactive les modules spécifiés



### `module`

Nom du module

- Valeur par défaut : `[]`

- Tableau

### `--force`, `-f`

Vérification des dépendances de contournement

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--all`

Désactiver tous les modules

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--clear-static-content`, `-c`

Effacez les fichiers d’affichage statique générés. Nécessaire, si le ou les modules disposent de fichiers d’affichage statiques

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `module:enable`

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Active les modules spécifiés



### `module`

Nom du module

- Valeur par défaut : `[]`

- Tableau

### `--force`, `-f`

Vérification des dépendances de contournement

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--all`

Activer tous les modules

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--clear-static-content`, `-c`

Effacez les fichiers d’affichage statique générés. Nécessaire, si le ou les modules disposent de fichiers d’affichage statiques

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `module:status`

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

Affiche l’état des modules.



### `module-names`

Nom facultatif du module

- Valeur par défaut : `[]`

- Tableau

### `--enabled`

Imprimer uniquement les modules activés

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--disabled`

Imprimer uniquement les modules désactivés

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `module:uninstall`

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

Désinstallation des modules installés par le compositeur



### `module`

Nom du module

- Valeur par défaut : `[]`

- Obligatoire
- Tableau

### `--remove-data`, `-r`

Suppression des données installées par le ou les modules

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--backup-code`

Sauvegarder le code et les fichiers de configuration (à l’exclusion des fichiers temporaires)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--backup-media`

Effectuer une sauvegarde multimédia

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--backup-db`

Sauvegarder la base de données complète

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--non-composer`

Tous les modules qui seront passés ici seront basés sur des non-compositeurs.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--clear-static-content`, `-c`

Effacez les fichiers d’affichage statique générés. Nécessaire, si le ou les modules disposent de fichiers d’affichage statiques

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `newrelic:create:deploy-marker`

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

Vérifiez les entrées de la file d’attente de déploiement et créez un marqueur de déploiement approprié.



### `message`

Déployer un message ?

- Obligatoire

### `change_log`

Journal des modifications ?

- Obligatoire

### `user`

Utilisateur de déploiement


### `revision`

Révision


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


## `queue:consumers:list`

```bash
bin/magento queue:consumers:list
```

Liste des consommateurs MessageQueue


```
This command shows list of MessageQueue consumers.
```

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


## `queue:consumers:restart`

```bash
bin/magento queue:consumers:restart
```

Redémarrer les consommateurs MessageQueue


```
Command put poison pill for MessageQueue consumers and force to restart them after next status check.
```

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


## `queue:consumers:start`

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

Démarrez le client MessageQueue


```
This command starts MessageQueue consumer by its name.

To start consumer which will process all queued messages and terminate execution:

    bin/magento queue:consumers:start someConsumer

To specify the number of messages which should be processed by consumer before its termination:

    bin/magento queue:consumers:start someConsumer --max-messages=50

To specify the number of messages per batch for the batch consumer:

    bin/magento queue:consumers:start someConsumer --batch-size=500

To specify the preferred area:

    bin/magento queue:consumers:start someConsumer --area-code='adminhtml'

To do not run multiple copies of one consumer simultaneously:

    bin/magento queue:consumers:start someConsumer --single-thread

To save PID enter path (This option is deprecated, use --single-thread instead):

    bin/magento queue:consumers:start someConsumer --pid-file-path='/var/someConsumer.pid'

To define the number of processes per consumer:

    bin/magento queue:consumers:start someConsumer --multi-process=4
```


### `consumer`

Nom du consommateur à démarrer.

- Obligatoire

### `--max-messages`

Nombre de messages à traiter par le consommateur avant la fin du traitement. Si non spécifié, arrêtez-le après avoir traité tous les messages en file d&#39;attente.

- Requiert une valeur

### `--batch-size`

Nombre de messages par lot. Applicable au consommateur par lot uniquement.

- Requiert une valeur

### `--area-code`

La valeur par défaut de la zone préférée (global, adminhtml, etc..) est globale.

- Requiert une valeur

### `--single-thread`

Cette option empêche l’exécution simultanée de plusieurs copies d’un même consommateur.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--multi-process`

Nombre de processus par consommateur.

- Accepte une valeur

### `--pid-file-path`

Le chemin d’accès au fichier pour l’enregistrement du PID (cette option est obsolète, utilisez plutôt —single-thread).

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


## `remote-storage:sync`

```bash
bin/magento remote-storage:sync
```

Synchronisez les fichiers multimédias avec l’enregistrement à distance.


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


## `saas:resync`

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync]
```

resynchronisez les données de flux vers le service SaaS.


### `--feed`

Nom du flux pour effectuer une synchronisation complète avec le service SaaS. Flux disponibles : paiement des services Commande Production, paiement des services Sandbox Commande, paiement des services État de commande Production, paiement des services État de commande Sandbox, paiement des services État de commande Sandbox, paiement des services Entrepôt Production, paiement des services Banque Sandbox

- Requiert une valeur

### `--no-reindex`

Exécutez le renvoi des données de flux vers le service SaaS uniquement. Ne réindexe pas. (Cette option ne s’applique pas aux produits, aux produits, aux courses de produits, aux flux de prix)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--cleanup-feed`

Forcer le nettoyage de la table de l’indexeur de flux avant synchronisation.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--dry-run`

Séchez-vous ! Les données ne seront pas exportées. Pour enregistrer la charge utile dans le fichier journal var/log/saas-export.log, exécutez avec la variable env EXPORTER_EXTENDED_LOG=1.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--thread-count`

Définissez le nombre de threads de synchronisation.

- Requiert une valeur

### `--batch-size`

Définition de la taille de lot de synchronisation

- Requiert une valeur

### `--continue-resync`

Continuer la resynchronisation à partir de la dernière position stockée (cette option s’applique aux produits, aux produits de remplacement, aux flux de prix)

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


## `sampledata:deploy`

```bash
bin/magento sampledata:deploy [--no-update]
```

Déploiement d’exemples de modules de données pour les installations de Magento compositeur


### `--no-update`

Mettre à jour le compositeur.json sans exécuter la mise à jour du compositeur

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


## `sampledata:remove`

```bash
bin/magento sampledata:remove [--no-update]
```

Supprimez tous les exemples de packages de données de compositeur.json.


### `--no-update`

Mettre à jour le compositeur.json sans exécuter la mise à jour du compositeur

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


## `sampledata:reset`

```bash
bin/magento sampledata:reset
```

Réinitialiser tous les exemples de modules de données pour la réinstallation


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


## `security:recaptcha:disable-for-user-forgot-password`

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

Désactiver reCAPTCHA pour le formulaire de mot de passe oublié par l’utilisateur administrateur


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


## `security:recaptcha:disable-for-user-login`

```bash
bin/magento security:recaptcha:disable-for-user-login
```

Désactiver reCAPTCHA pour le formulaire de connexion de l’utilisateur administrateur


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


## `security:tfa:google:set-secret`

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

Définissez le secret utilisé pour la génération du HTTP Google.



### `user`

Nom d’utilisateur

- Obligatoire

### `secret`

Secret

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


## `security:tfa:providers`

```bash
bin/magento security:tfa:providers
```

Liste de tous les fournisseurs disponibles


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


## `security:tfa:reset`

```bash
bin/magento security:tfa:reset <user> <provider>
```

Réinitialiser la configuration d’un utilisateur



### `user`

Nom d’utilisateur

- Obligatoire

### `provider`

Code du fournisseur

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


## `server:run`

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-wn|--workerNum [WORKERNUM]] [-dm|--dispatchMode [DISPATCHMODE]] [-mr|--maxRequests [MAXREQUESTS]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]] [-mwt|--maxWaitTime [MAXWAITTIME]] [--state-monitor]
```

Exécution du serveur d’applications


### `--port`, `-p`

port pour servir sur

- Valeur par défaut : `9501`
- Accepte une valeur

### `--background`, `-b`

indicateur du mode d’arrière-plan

- Valeur par défaut : `0`
- Accepte une valeur

### `--workerNum`, `-wn`

nombre de processus de travail à démarrer

- Valeur par défaut : `4`
- Accepte une valeur

### `--dispatchMode`, `-dm`

mode de distribution des connexions aux processus de travail

- Valeur par défaut : `3`
- Accepte une valeur

### `--maxRequests`, `-mr`

requêtes max avant le redémarrage du processus de travail

- Valeur par défaut : `10000`
- Accepte une valeur

### `--area`, `-a`

zone du serveur d’applications

- Valeur par défaut : `graphql`
- Accepte une valeur

### `--magento-init-params`, `-mip`

magento bootstrap init params

- Par défaut : &quot;
- Accepte une valeur

### `--maxWaitTime`, `-mwt`

durée d’attente des programmes de travail après rechargement (par exemple, (changement de configuration) avant de les supprimer

- Valeur par défaut : `3600`
- Accepte une valeur

### `--state-monitor`

Activez la surveillance de l’état. Utilisez cette option uniquement pour les problèmes d’état de débogage.

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


## `server:state-monitor:aggregate-output`

```bash
bin/magento server:state-monitor:aggregate-output
```

Sortie agrégée du moniteur d’état d’ApplicationServer


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


## `setup:backup`

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Sauvegarde de la base de code d’application, du média et de la base de données du Magento


### `--code`

Sauvegarder le code et les fichiers de configuration (à l’exclusion des fichiers temporaires)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--media`

Effectuer une sauvegarde multimédia

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--db`

Sauvegarder la base de données complète

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:config:set`

```bash
bin/magento setup:config:set [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Crée ou modifie la configuration du déploiement


### `--enable-debug-logging`

Activation de la journalisation du débogage

- Requiert une valeur

### `--enable-syslog-logging`

Activation de la journalisation du journal de syslog

- Requiert une valeur

### `--backend-frontname`

Nom frontal du serveur principal (il sera généré automatiquement s’il manque)

- Requiert une valeur

### `--remote-storage-driver`

Pilote de stockage distant

- Requiert une valeur

### `--remote-storage-prefix`

Préfixe de stockage distant

- Par défaut : &quot;
- Requiert une valeur

### `--remote-storage-endpoint`

Point d’entrée de stockage distant

- Requiert une valeur

### `--remote-storage-bucket`

Boucle de stockage à distance

- Requiert une valeur

### `--remote-storage-region`

Région de stockage distant

- Requiert une valeur

### `--remote-storage-key`

Clé d&#39;accès au stockage distant

- Par défaut : &quot;
- Requiert une valeur

### `--remote-storage-secret`

Clé secrète de stockage à distance

- Par défaut : &quot;
- Requiert une valeur

### `--remote-storage-path-style`

Style de chemin de stockage distant

- Valeur par défaut : `0`
- Requiert une valeur

### `--id_salt`

GraphQl Salt

- Requiert une valeur

### `--config-async`

Activer l’enregistrement de configuration d’administrateur asynchrone ? 1 - Oui, 0 - Non

- Requiert une valeur

### `--checkout-async`

Activer le traitement asynchrone des commandes ? 1 - Oui, 0 - Non

- Requiert une valeur

### `--amqp-host`

Hôte du serveur Amqp

- Par défaut : &quot;
- Requiert une valeur

### `--amqp-port`

Port du serveur Amqp

- Valeur par défaut : `5672`
- Requiert une valeur

### `--amqp-user`

Nom d’utilisateur du serveur Amqp

- Par défaut : &quot;
- Requiert une valeur

### `--amqp-password`

Mot de passe du serveur Amqp

- Par défaut : &quot;
- Requiert une valeur

### `--amqp-virtualhost`

virtualhost Amqp

- Valeur par défaut : `/`
- Requiert une valeur

### `--amqp-ssl`

Amqp SSL

- Par défaut : &quot;
- Requiert une valeur

### `--amqp-ssl-options`

Options SSL Amqp (JSON)

- Par défaut : &quot;
- Requiert une valeur

### `--consumers-wait-for-messages`

Les consommateurs doivent-ils attendre un message de la file d’attente ? 1 - Oui, 0 - Non

- Requiert une valeur

### `--queue-default-connection`

La connexion par défaut des files de messages est mise en file d’attente. Peut être &#39;db&#39;, &#39;amqp&#39; ou un système de file d&#39;attente personnalisé. Le système de file d&#39;attente doit être installé et configuré, sinon les messages ne seront pas traités correctement.

- Requiert une valeur

### `--deferred-total-calculating`

Activer le calcul du total différé ? 1 - Oui, 0 - Non

- Requiert une valeur

### `--key`

Clé de chiffrement

- Requiert une valeur

### `--db-host`

Hôte du serveur de base de données

- Requiert une valeur

### `--db-name`

Nom de la base

- Requiert une valeur

### `--db-user`

Database server username

- Requiert une valeur

### `--db-engine`

Moteur de serveur de base de données

- Requiert une valeur

### `--db-password`

Mot de passe du serveur de base de données

- Requiert une valeur

### `--db-prefix`

Préfixe de table de base de données

- Requiert une valeur

### `--db-model`

Type de base de données

- Requiert une valeur

### `--db-init-statements`

Jeu initial de commandes de la base de données

- Requiert une valeur

### `--skip-db-validation`, `-s`

Si spécifié, la validation de la connexion à la base de données est ignorée.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--http-cache-hosts`

http Cache hosts

- Requiert une valeur

### `--db-ssl-key`

Chemin complet du fichier de clé client pour établir la connexion de la base de données via SSL

- Par défaut : &quot;
- Requiert une valeur

### `--db-ssl-cert`

Chemin complet du fichier de certificat client pour établir la connexion de la base de données via SSL

- Par défaut : &quot;
- Requiert une valeur

### `--db-ssl-ca`

Chemin complet du fichier de certificat du serveur pour établir la connexion de la base de données via SSL

- Par défaut : &quot;
- Requiert une valeur

### `--db-ssl-verify`

Vérification de la certification du serveur

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--session-save`

Gestionnaire d’enregistrement de session

- Requiert une valeur

### `--session-save-redis-host`

Nom d’hôte complet, adresse IP ou chemin absolu en cas d’utilisation de sockets UNIX

- Requiert une valeur

### `--session-save-redis-port`

Port d’écoute du serveur Redis

- Requiert une valeur

### `--session-save-redis-password`

Mot de passe du serveur Redis

- Requiert une valeur

### `--session-save-redis-timeout`

Timeout de connexion, en secondes

- Requiert une valeur

### `--session-save-redis-persistent-id`

Chaîne unique pour activer les connexions persistantes

- Requiert une valeur

### `--session-save-redis-db`

Redis database number

- Requiert une valeur

### `--session-save-redis-compression-threshold`

Seuil de compression des redis

- Requiert une valeur

### `--session-save-redis-compression-lib`

Redis la bibliothèque de compression. Valeurs : gzip (par défaut), lzf, lz4, snappy

- Requiert une valeur

### `--session-save-redis-log-level`

Redis le niveau de journalisation. Valeurs : 0 (minimum verbose) à 7 (plus verbose)

- Requiert une valeur

### `--session-save-redis-max-concurrency`

Nombre maximal de processus pouvant attendre un verrouillage sur une session

- Requiert une valeur

### `--session-save-redis-break-after-frontend`

Nombre de secondes à patienter avant de tenter de rompre un verrouillage pour la session frontale

- Requiert une valeur

### `--session-save-redis-break-after-adminhtml`

Nombre de secondes à attendre avant de tenter de rompre un verrouillage pour la session d’administration

- Requiert une valeur

### `--session-save-redis-first-lifetime`

Durée de vie, en secondes, de la session pour les non-robots lors de la première écriture (utilisez 0 pour désactiver).

- Requiert une valeur

### `--session-save-redis-bot-first-lifetime`

Durée de vie, en secondes, de la session pour les robots lors de la première écriture (utiliser 0 pour désactiver)

- Requiert une valeur

### `--session-save-redis-bot-lifetime`

Durée de vie de la session pour les robots lors des écritures suivantes (utilisez 0 pour désactiver)

- Requiert une valeur

### `--session-save-redis-disable-locking`

Redis désactiver le verrouillage. Valeurs : false (par défaut), true

- Requiert une valeur

### `--session-save-redis-min-lifetime`

Durée de vie de la session min., en secondes

- Requiert une valeur

### `--session-save-redis-max-lifetime`

Durée de vie maximale de la session, exprimée en secondes

- Requiert une valeur

### `--session-save-redis-sentinel-master`

Redis Sentinel maître

- Requiert une valeur

### `--session-save-redis-sentinel-servers`

Serveurs Redis Sentinel, séparés par des virgules

- Requiert une valeur

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel vérifie maître. Valeurs : false (par défaut), true

- Requiert une valeur

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel connecte les nouvelles tentatives.

- Requiert une valeur

### `--cache-backend`

Gestionnaire de cache par défaut

- Requiert une valeur

### `--cache-backend-redis-server`

Serveur Redis

- Requiert une valeur

### `--cache-backend-redis-db`

Numéro de base de données du cache

- Requiert une valeur

### `--cache-backend-redis-port`

Port d’écoute du serveur Redis

- Requiert une valeur

### `--cache-backend-redis-password`

Mot de passe du serveur Redis

- Requiert une valeur

### `--cache-backend-redis-compress-data`

Défini sur 0 pour désactiver la compression (la valeur par défaut est 1, activée).

- Requiert une valeur

### `--cache-backend-redis-compression-lib`

Bibliothèque de compression à utiliser [snappy,lzf,l4z,zstd,gzip] (laissez vide pour déterminer automatiquement)

- Requiert une valeur

### `--cache-backend-redis-use-lua`

Définissez cette variable sur 1 pour activer lua (la valeur par défaut est 0, désactivée).

- Requiert une valeur

### `--cache-id-prefix`

Préfixe d’ID pour les clés de cache

- Requiert une valeur

### `--allow-parallel-generation`

Autoriser la génération du cache de manière non bloquante

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--page-cache`

Gestionnaire de cache par défaut

- Requiert une valeur

### `--page-cache-redis-server`

Serveur Redis

- Requiert une valeur

### `--page-cache-redis-db`

Numéro de base de données du cache

- Requiert une valeur

### `--page-cache-redis-port`

Port d’écoute du serveur Redis

- Requiert une valeur

### `--page-cache-redis-password`

Mot de passe du serveur Redis

- Requiert une valeur

### `--page-cache-redis-compress-data`

Définissez cette variable sur 1 pour compresser le cache de la page entière (utilisez 0 pour désactiver).

- Requiert une valeur

### `--page-cache-redis-compression-lib`

Bibliothèque de compression à utiliser [snappy,lzf,l4z,zstd,gzip] (laissez vide pour déterminer automatiquement)

- Requiert une valeur

### `--page-cache-id-prefix`

Préfixe d’ID pour les clés de cache

- Requiert une valeur

### `--lock-provider`

Verrouillage du nom du fournisseur

- Requiert une valeur

### `--lock-db-prefix`

Préfixe de verrouillage spécifique à l&#39;installation pour éviter les conflits de verrouillage

- Requiert une valeur

### `--lock-zookeeper-host`

Hôte et port pour se connecter à la grappe Zookeeper. Par exemple : 127.0.0.1:2181

- Requiert une valeur

### `--lock-zookeeper-path`

Chemin d’accès où le gardien de page enregistre les verrous. Le chemin par défaut est : /magento/locks

- Requiert une valeur

### `--lock-file-path`

Chemin d’accès où les verrous de fichier seront enregistrés.

- Requiert une valeur

### `--document-root-is-pub`

Indicateur indiquant que Pub est à la racine, peut être vrai ou faux uniquement

- Requiert une valeur

### `--backpressure-logger`

Gestionnaire des enregistreurs de rétropression

- Requiert une valeur

### `--backpressure-logger-redis-server`

Serveur Redis

- Requiert une valeur

### `--backpressure-logger-redis-port`

Port d’écoute du serveur Redis

- Requiert une valeur

### `--backpressure-logger-redis-timeout`

Délai d’expiration du serveur Redis

- Requiert une valeur

### `--backpressure-logger-redis-persistent`

Redis persistante

- Requiert une valeur

### `--backpressure-logger-redis-db`

Redis db number

- Requiert une valeur

### `--backpressure-logger-redis-password`

Mot de passe du serveur Redis

- Requiert une valeur

### `--backpressure-logger-redis-user`

Utilisateur du serveur Redis

- Requiert une valeur

### `--backpressure-logger-id-prefix`

Préfixe d’ID pour les clés

- Requiert une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-data:upgrade`

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installation et mise à niveau des données dans DB


### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-declaration:generate-patch`

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

Générez un correctif et placez-le dans un dossier spécifique.



### `module`

Nom du module

- Obligatoire

### `patch`

Nom du correctif

- Obligatoire

### `--revertable`

Vérifiez si le correctif est réversible ou non.

- Valeur par défaut : `false`
- Accepte une valeur

### `--type`

Découvrez le type de correctif à générer. Valeurs disponibles : `data`, `schema`.

- Valeur par défaut : `data`
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


## `setup:db-declaration:generate-whitelist`

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

Générer la liste blanche des tables et colonnes qui peuvent être éditées par le programme d&#39;installation de la déclaration


### `--module-name`

Nom du module dans lequel la liste blanche sera générée

- Valeur par défaut : `all`
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


## `setup:db-schema:add-slave`

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Déplacer les tableaux associés aux guillemets de passage en caisse vers un serveur DB distinct


### `--host`

Hôte du serveur de base de données esclave

- Valeur par défaut : `localhost`
- Requiert une valeur

### `--dbname`

Nom de la base de données esclave

- Requiert une valeur

### `--username`

Nom d’utilisateur de la base de données esclave

- Valeur par défaut : `root`
- Requiert une valeur

### `--password`

Mot de passe utilisateur de la base de données esclave

- Accepte une valeur

### `--connection`

Nom de la connexion esclave

- Valeur par défaut : `default`
- Accepte une valeur

### `--resource`

Nom de la ressource esclave

- Valeur par défaut : `default`
- Accepte une valeur

### `--maxAllowedLag`

Connexion maximale autorisée à l’esclave de la traîne (en secondes)

- Par défaut : &quot;
- Accepte une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-schema:split-quote`

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Déplacez les tables liées aux guillemets de passage en caisse vers un serveur DB distinct. Obsolète depuis la version 2.4.2 et sera supprimée


### `--host`

Extraction de l’hôte du serveur DB

- Requiert une valeur

### `--dbname`

Checout Database Name

- Requiert une valeur

### `--username`

Extraction du nom d’utilisateur DB

- Requiert une valeur

### `--password`

Extraction du mot de passe de l’utilisateur DB

- Accepte une valeur

### `--connection`

Nom de la connexion de passage en caisse

- Valeur par défaut : `checkout`
- Accepte une valeur

### `--resource`

Nom de la ressource d’extraction

- Valeur par défaut : `checkout`
- Accepte une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-schema:split-sales`

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Déplacez les tables liées aux ventes vers un serveur de base de données distinct. Obsolète depuis la version 2.4.2 et sera supprimée


### `--host`

Hôte de serveur de base de données des ventes

- Requiert une valeur

### `--dbname`

Nom de la base de données de ventes

- Requiert une valeur

### `--username`

Nom d’utilisateur de la base de données des ventes

- Requiert une valeur

### `--password`

Mot de passe utilisateur de la base de données des ventes

- Accepte une valeur

### `--connection`

Nom de la connexion commerciale

- Valeur par défaut : `sales`
- Accepte une valeur

### `--resource`

Nom de la ressource commerciale

- Valeur par défaut : `sales`
- Accepte une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-schema:upgrade`

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installation et mise à niveau du schéma DB


### `--convert-old-scripts`

Permet de convertir les anciens scripts (InstallSchema, UpgradeSchema) au format db_schema.xml .

- Valeur par défaut : `false`
- Accepte une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:db:status`

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Vérifie si le schéma ou les données de la base de données doivent être mis à niveau


### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:di:compile`

```bash
bin/magento setup:di:compile
```

Génère la configuration de l’ID et toutes les classes manquantes qui peuvent être générées automatiquement


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


## `setup:install`

```bash
bin/magento setup:install [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installation de l’application de Magento


### `--enable-debug-logging`

Activation de la journalisation du débogage

- Requiert une valeur

### `--enable-syslog-logging`

Activation de la journalisation du journal de syslog

- Requiert une valeur

### `--backend-frontname`

Nom frontal du serveur principal (il sera généré automatiquement s’il manque)

- Requiert une valeur

### `--remote-storage-driver`

Pilote de stockage distant

- Requiert une valeur

### `--remote-storage-prefix`

Préfixe de stockage distant

- Par défaut : &quot;
- Requiert une valeur

### `--remote-storage-endpoint`

Point d’entrée de stockage distant

- Requiert une valeur

### `--remote-storage-bucket`

Boucle de stockage à distance

- Requiert une valeur

### `--remote-storage-region`

Région de stockage distant

- Requiert une valeur

### `--remote-storage-key`

Clé d&#39;accès au stockage distant

- Par défaut : &quot;
- Requiert une valeur

### `--remote-storage-secret`

Clé secrète de stockage à distance

- Par défaut : &quot;
- Requiert une valeur

### `--remote-storage-path-style`

Style de chemin de stockage distant

- Valeur par défaut : `0`
- Requiert une valeur

### `--id_salt`

GraphQl Salt

- Requiert une valeur

### `--config-async`

Activer l’enregistrement de configuration d’administrateur asynchrone ? 1 - Oui, 0 - Non

- Requiert une valeur

### `--checkout-async`

Activer le traitement asynchrone des commandes ? 1 - Oui, 0 - Non

- Requiert une valeur

### `--amqp-host`

Hôte du serveur Amqp

- Par défaut : &quot;
- Requiert une valeur

### `--amqp-port`

Port du serveur Amqp

- Valeur par défaut : `5672`
- Requiert une valeur

### `--amqp-user`

Nom d’utilisateur du serveur Amqp

- Par défaut : &quot;
- Requiert une valeur

### `--amqp-password`

Mot de passe du serveur Amqp

- Par défaut : &quot;
- Requiert une valeur

### `--amqp-virtualhost`

virtualhost Amqp

- Valeur par défaut : `/`
- Requiert une valeur

### `--amqp-ssl`

Amqp SSL

- Par défaut : &quot;
- Requiert une valeur

### `--amqp-ssl-options`

Options SSL Amqp (JSON)

- Par défaut : &quot;
- Requiert une valeur

### `--consumers-wait-for-messages`

Les consommateurs doivent-ils attendre un message de la file d’attente ? 1 - Oui, 0 - Non

- Requiert une valeur

### `--queue-default-connection`

La connexion par défaut des files de messages est mise en file d’attente. Peut être &#39;db&#39;, &#39;amqp&#39; ou un système de file d&#39;attente personnalisé. Le système de file d&#39;attente doit être installé et configuré, sinon les messages ne seront pas traités correctement.

- Requiert une valeur

### `--deferred-total-calculating`

Activer le calcul du total différé ? 1 - Oui, 0 - Non

- Requiert une valeur

### `--key`

Clé de chiffrement

- Requiert une valeur

### `--db-host`

Hôte du serveur de base de données

- Requiert une valeur

### `--db-name`

Nom de la base

- Requiert une valeur

### `--db-user`

Database server username

- Requiert une valeur

### `--db-engine`

Moteur de serveur de base de données

- Requiert une valeur

### `--db-password`

Mot de passe du serveur de base de données

- Requiert une valeur

### `--db-prefix`

Préfixe de table de base de données

- Requiert une valeur

### `--db-model`

Type de base de données

- Requiert une valeur

### `--db-init-statements`

Jeu initial de commandes de la base de données

- Requiert une valeur

### `--skip-db-validation`, `-s`

Si spécifié, la validation de la connexion à la base de données est ignorée.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--http-cache-hosts`

http Cache hosts

- Requiert une valeur

### `--db-ssl-key`

Chemin complet du fichier de clé client pour établir la connexion de la base de données via SSL

- Par défaut : &quot;
- Requiert une valeur

### `--db-ssl-cert`

Chemin complet du fichier de certificat client pour établir la connexion de la base de données via SSL

- Par défaut : &quot;
- Requiert une valeur

### `--db-ssl-ca`

Chemin complet du fichier de certificat du serveur pour établir la connexion de la base de données via SSL

- Par défaut : &quot;
- Requiert une valeur

### `--db-ssl-verify`

Vérification de la certification du serveur

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--session-save`

Gestionnaire d’enregistrement de session

- Requiert une valeur

### `--session-save-redis-host`

Nom d’hôte complet, adresse IP ou chemin absolu en cas d’utilisation de sockets UNIX

- Requiert une valeur

### `--session-save-redis-port`

Port d’écoute du serveur Redis

- Requiert une valeur

### `--session-save-redis-password`

Mot de passe du serveur Redis

- Requiert une valeur

### `--session-save-redis-timeout`

Timeout de connexion, en secondes

- Requiert une valeur

### `--session-save-redis-persistent-id`

Chaîne unique pour activer les connexions persistantes

- Requiert une valeur

### `--session-save-redis-db`

Redis database number

- Requiert une valeur

### `--session-save-redis-compression-threshold`

Seuil de compression des redis

- Requiert une valeur

### `--session-save-redis-compression-lib`

Redis la bibliothèque de compression. Valeurs : gzip (par défaut), lzf, lz4, snappy

- Requiert une valeur

### `--session-save-redis-log-level`

Redis le niveau de journalisation. Valeurs : 0 (minimum verbose) à 7 (plus verbose)

- Requiert une valeur

### `--session-save-redis-max-concurrency`

Nombre maximal de processus pouvant attendre un verrouillage sur une session

- Requiert une valeur

### `--session-save-redis-break-after-frontend`

Nombre de secondes à patienter avant de tenter de rompre un verrouillage pour la session frontale

- Requiert une valeur

### `--session-save-redis-break-after-adminhtml`

Nombre de secondes à attendre avant de tenter de rompre un verrouillage pour la session d’administration

- Requiert une valeur

### `--session-save-redis-first-lifetime`

Durée de vie, en secondes, de la session pour les non-robots lors de la première écriture (utilisez 0 pour désactiver).

- Requiert une valeur

### `--session-save-redis-bot-first-lifetime`

Durée de vie, en secondes, de la session pour les robots lors de la première écriture (utiliser 0 pour désactiver)

- Requiert une valeur

### `--session-save-redis-bot-lifetime`

Durée de vie de la session pour les robots lors des écritures suivantes (utilisez 0 pour désactiver)

- Requiert une valeur

### `--session-save-redis-disable-locking`

Redis désactiver le verrouillage. Valeurs : false (par défaut), true

- Requiert une valeur

### `--session-save-redis-min-lifetime`

Durée de vie de la session min., en secondes

- Requiert une valeur

### `--session-save-redis-max-lifetime`

Durée de vie maximale de la session, exprimée en secondes

- Requiert une valeur

### `--session-save-redis-sentinel-master`

Redis Sentinel maître

- Requiert une valeur

### `--session-save-redis-sentinel-servers`

Serveurs Redis Sentinel, séparés par des virgules

- Requiert une valeur

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel vérifie maître. Valeurs : false (par défaut), true

- Requiert une valeur

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel connecte les nouvelles tentatives.

- Requiert une valeur

### `--cache-backend`

Gestionnaire de cache par défaut

- Requiert une valeur

### `--cache-backend-redis-server`

Serveur Redis

- Requiert une valeur

### `--cache-backend-redis-db`

Numéro de base de données du cache

- Requiert une valeur

### `--cache-backend-redis-port`

Port d’écoute du serveur Redis

- Requiert une valeur

### `--cache-backend-redis-password`

Mot de passe du serveur Redis

- Requiert une valeur

### `--cache-backend-redis-compress-data`

Défini sur 0 pour désactiver la compression (la valeur par défaut est 1, activée).

- Requiert une valeur

### `--cache-backend-redis-compression-lib`

Bibliothèque de compression à utiliser [snappy,lzf,l4z,zstd,gzip] (laissez vide pour déterminer automatiquement)

- Requiert une valeur

### `--cache-backend-redis-use-lua`

Définissez cette variable sur 1 pour activer lua (la valeur par défaut est 0, désactivée).

- Requiert une valeur

### `--cache-id-prefix`

Préfixe d’ID pour les clés de cache

- Requiert une valeur

### `--allow-parallel-generation`

Autoriser la génération du cache de manière non bloquante

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--page-cache`

Gestionnaire de cache par défaut

- Requiert une valeur

### `--page-cache-redis-server`

Serveur Redis

- Requiert une valeur

### `--page-cache-redis-db`

Numéro de base de données du cache

- Requiert une valeur

### `--page-cache-redis-port`

Port d’écoute du serveur Redis

- Requiert une valeur

### `--page-cache-redis-password`

Mot de passe du serveur Redis

- Requiert une valeur

### `--page-cache-redis-compress-data`

Définissez cette variable sur 1 pour compresser le cache de la page entière (utilisez 0 pour désactiver).

- Requiert une valeur

### `--page-cache-redis-compression-lib`

Bibliothèque de compression à utiliser [snappy,lzf,l4z,zstd,gzip] (laissez vide pour déterminer automatiquement)

- Requiert une valeur

### `--page-cache-id-prefix`

Préfixe d’ID pour les clés de cache

- Requiert une valeur

### `--lock-provider`

Verrouillage du nom du fournisseur

- Requiert une valeur

### `--lock-db-prefix`

Préfixe de verrouillage spécifique à l&#39;installation pour éviter les conflits de verrouillage

- Requiert une valeur

### `--lock-zookeeper-host`

Hôte et port pour se connecter à la grappe Zookeeper. Par exemple : 127.0.0.1:2181

- Requiert une valeur

### `--lock-zookeeper-path`

Chemin d’accès où le gardien de page enregistre les verrous. Le chemin par défaut est : /magento/locks

- Requiert une valeur

### `--lock-file-path`

Chemin d’accès où les verrous de fichier seront enregistrés.

- Requiert une valeur

### `--document-root-is-pub`

Indicateur indiquant que Pub est à la racine, peut être vrai ou faux uniquement

- Requiert une valeur

### `--backpressure-logger`

Gestionnaire des enregistreurs de rétropression

- Requiert une valeur

### `--backpressure-logger-redis-server`

Serveur Redis

- Requiert une valeur

### `--backpressure-logger-redis-port`

Port d’écoute du serveur Redis

- Requiert une valeur

### `--backpressure-logger-redis-timeout`

Délai d’expiration du serveur Redis

- Requiert une valeur

### `--backpressure-logger-redis-persistent`

Redis persistante

- Requiert une valeur

### `--backpressure-logger-redis-db`

Redis db number

- Requiert une valeur

### `--backpressure-logger-redis-password`

Mot de passe du serveur Redis

- Requiert une valeur

### `--backpressure-logger-redis-user`

Utilisateur du serveur Redis

- Requiert une valeur

### `--backpressure-logger-id-prefix`

Préfixe d’ID pour les clés

- Requiert une valeur

### `--base-url`

URL à laquelle le magasin est censé être disponible. Obsolète, utilisez config:set avec le chemin web/unsecure/base_url

- Requiert une valeur

### `--language`

Code de langue par défaut. Obsolète, utilisez config:set avec le chemin d’accès général/locale/code

- Requiert une valeur

### `--timezone`

Code de fuseau horaire par défaut. Obsolète, utilisez config:set avec le chemin général/locale/timezone

- Requiert une valeur

### `--currency`

Code de devise par défaut. Obsolète, utilisez config:set avec le chemin currency/options/base, currency/options/default et currency/options/allow

- Requiert une valeur

### `--use-rewrites`

Utilisez les réécritures. Obsolète, utilisez config:set avec le chemin web/seo/use_rewrites

- Requiert une valeur

### `--use-secure`

Utilisez des URL sécurisées. Activez cette option uniquement si SSL est disponible. Obsolète, utilisez config:set avec le chemin web/secure/use_in_frontend

- Requiert une valeur

### `--base-url-secure`

URL de base de la connexion SSL. Obsolète, utilisez config:set avec le chemin web/secure/base_url

- Requiert une valeur

### `--use-secure-admin`

Exécutez l’interface d’administration avec SSL. Obsolète, utilisez config:set avec le chemin web/secure/use_in_adminhtml

- Requiert une valeur

### `--admin-use-security-key`

Utilisation ou non d’une fonctionnalité &quot;clé de sécurité&quot; dans les URL et les formulaires d’administration du Magento. Obsolète, utilisez config:set avec le chemin admin/security/use_form_key

- Requiert une valeur

### `--admin-user`

Utilisateur administrateur

- Accepte une valeur

### `--admin-password`

Mot de passe administrateur

- Accepte une valeur

### `--admin-email`

Admin Email

- Accepte une valeur

### `--admin-firstname`

Prénom de l’administrateur

- Accepte une valeur

### `--admin-lastname`

Nom de l’administrateur

- Accepte une valeur

### `--search-engine`

Moteur de recherche. Valeurs : élasticsearch7, élasticsearch8, opensearch

- Requiert une valeur

### `--elasticsearch-host`

Hôte du serveur Elasticsearch.

- Requiert une valeur

### `--elasticsearch-port`

Port du serveur Elasticsearch.

- Requiert une valeur

### `--elasticsearch-enable-auth`

Définissez cette variable sur 1 pour activer l’authentification. (la valeur par défaut est 0, désactivé)

- Requiert une valeur

### `--elasticsearch-username`

Nom d’utilisateur Elasticsearch. Applicable uniquement si l’authentification HTTP est activée

- Requiert une valeur

### `--elasticsearch-password`

Mot de passe de l’Elasticsearch. Applicable uniquement si l’authentification HTTP est activée

- Requiert une valeur

### `--elasticsearch-index-prefix`

Préfixe d’index Elasticsearch.

- Requiert une valeur

### `--elasticsearch-timeout`

Délai d’expiration du serveur Elasticsearch.

- Requiert une valeur

### `--opensearch-host`

Hôte du serveur OpenSearch.

- Requiert une valeur

### `--opensearch-port`

Port du serveur OpenSearch.

- Requiert une valeur

### `--opensearch-enable-auth`

Définissez cette variable sur 1 pour activer l’authentification. (la valeur par défaut est 0, désactivé)

- Requiert une valeur

### `--opensearch-username`

Nom d’utilisateur OpenSearch. Applicable uniquement si l’authentification HTTP est activée

- Requiert une valeur

### `--opensearch-password`

Mot de passe OpenSearch. Applicable uniquement si l’authentification HTTP est activée

- Requiert une valeur

### `--opensearch-index-prefix`

Préfixe d’index OpenSearch.

- Requiert une valeur

### `--opensearch-timeout`

Délai d’expiration du serveur OpenSearch.

- Requiert une valeur

### `--cleanup-database`

Nettoyage de la base de données avant installation

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--sales-order-increment-prefix`

Préfixe du numéro de commande commerciale

- Requiert une valeur

### `--use-sample-data`

Utiliser des exemples de données

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--enable-modules`

Liste des noms de module séparés par des virgules. Cela doit être inclus pendant l’installation. Param magique disponible &quot;all&quot;.

- Accepte une valeur

### `--disable-modules`

Liste des noms de module séparés par des virgules. Cela doit être évité lors de l’installation. Param magique disponible &quot;all&quot;.

- Accepte une valeur

### `--convert-old-scripts`

Permet de convertir les anciens scripts (InstallSchema, UpgradeSchema) au format db_schema.xml .

- Valeur par défaut : `false`
- Accepte une valeur

### `--interactive`, `-i`

Installation du Magento interactif

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--safe-mode`

Installation sécurisée d’un Magento avec des vidages lors d’opérations destructrices, comme la suppression de colonnes

- Accepte une valeur

### `--data-restore`

Restauration des données supprimées des vidages

- Accepte une valeur

### `--dry-run`

L&#39;installation du Magento sera exécutée en mode Exécution sec

- Valeur par défaut : `false`
- Accepte une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:performance:generate-fixtures`

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

Génère des fixations



### `profile`

Chemin d’accès au fichier de configuration du profil

- Obligatoire

### `--skip-reindex`, `-s`

Ignorer la réindexation

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


## `setup:rollback`

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Restauration du code d’application Magento, des médias et de la base de données


### `--code-file`, `-c`

Nom de base du fichier de sauvegarde de code dans var/backup

- Requiert une valeur

### `--media-file`, `-m`

Nom de base du fichier de sauvegarde multimédia dans var/backup

- Requiert une valeur

### `--db-file`, `-d`

Nom de base du fichier de sauvegarde db dans var/backup

- Requiert une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:static-content:deploy`

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

Déploiement de fichiers d’affichage statiques



### `languages`

Liste de codes de langue ISO-639 séparés par des espaces pour lesquels générer des fichiers d’affichage statique.

- Valeur par défaut : `[]`

- Tableau

### `--force`, `-f`

Déployez des fichiers dans n’importe quel mode.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--strategy`, `-s`

Déployez des fichiers à l’aide de la stratégie spécifiée.

- Valeur par défaut : `quick`
- Accepte une valeur

### `--area`, `-a`

Générez des fichiers uniquement pour les zones spécifiées.

- Valeur par défaut : `all`
- Accepte plusieurs valeurs

### `--exclude-area`

Ne générez pas de fichiers pour les zones spécifiées.

- Valeur par défaut : `none`
- Accepte plusieurs valeurs

### `--theme`, `-t`

Générez des fichiers d’affichage statique uniquement pour les thèmes spécifiés.

- Valeur par défaut : `all`
- Accepte plusieurs valeurs

### `--exclude-theme`

Ne générez pas de fichiers pour les thèmes spécifiés.

- Valeur par défaut : `none`
- Accepte plusieurs valeurs

### `--language`, `-l`

Générez des fichiers uniquement pour les langues spécifiées.

- Valeur par défaut : `all`
- Accepte plusieurs valeurs

### `--exclude-language`

Ne générez pas de fichiers pour les langues spécifiées.

- Valeur par défaut : `none`
- Accepte plusieurs valeurs

### `--jobs`, `-j`

Activez le traitement parallèle à l’aide du nombre spécifié de tâches.

- Valeur par défaut : `0`
- Accepte une valeur

### `--max-execution-time`

Délai d’exécution maximal attendu du processus statique de déploiement (en secondes).

- Valeur par défaut : `900`
- Accepte une valeur

### `--symlink-locale`

Créez des liens symboliques pour les fichiers de ces paramètres régionaux, qui sont transmis pour le déploiement, mais sans personnalisation.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--content-version`

La version personnalisée du contenu statique peut être utilisée si vous exécutez le déploiement sur plusieurs noeuds afin de vous assurer que la version du contenu statique est identique et que la mise en cache fonctionne correctement.

- Requiert une valeur

### `--refresh-content-version-only`

L’actualisation de la version du contenu statique peut uniquement être utilisée pour actualiser le contenu statique dans le cache du navigateur et le cache CDN.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-javascript`

Ne déployez pas de fichiers JavaScript.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-js-bundle`

Ne déployez pas de fichiers de bundle JavaScript.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-css`

Ne déployez pas de fichiers CSS.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-less`

Ne déployez pas de fichiers LESS.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-images`

Ne déployez pas d’images.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-fonts`

Ne déployez pas de fichiers de polices.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-html`

Ne déployez pas de fichiers de HTML.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-misc`

Ne déployez pas de fichiers d’autres types (.md, .jbf, .csv, etc.).

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-html-minify`

Ne minimisez pas les fichiers de HTML.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-parent`

Ne compilez pas de thèmes parents. Pris en charge uniquement dans les stratégies rapides et standard.

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


## `setup:store-config:set`

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installe la configuration du magasin. Obsolète depuis la version 2.2.0. Utilisez config:set à la place.


### `--base-url`

URL à laquelle le magasin est censé être disponible. Obsolète, utilisez config:set avec le chemin web/unsecure/base_url

- Requiert une valeur

### `--language`

Code de langue par défaut. Obsolète, utilisez config:set avec le chemin d’accès général/locale/code

- Requiert une valeur

### `--timezone`

Code de fuseau horaire par défaut. Obsolète, utilisez config:set avec le chemin général/locale/timezone

- Requiert une valeur

### `--currency`

Code de devise par défaut. Obsolète, utilisez config:set avec le chemin currency/options/base, currency/options/default et currency/options/allow

- Requiert une valeur

### `--use-rewrites`

Utilisez les réécritures. Obsolète, utilisez config:set avec le chemin web/seo/use_rewrites

- Requiert une valeur

### `--use-secure`

Utilisez des URL sécurisées. Activez cette option uniquement si SSL est disponible. Obsolète, utilisez config:set avec le chemin web/secure/use_in_frontend

- Requiert une valeur

### `--base-url-secure`

URL de base de la connexion SSL. Obsolète, utilisez config:set avec le chemin web/secure/base_url

- Requiert une valeur

### `--use-secure-admin`

Exécutez l’interface d’administration avec SSL. Obsolète, utilisez config:set avec le chemin web/secure/use_in_adminhtml

- Requiert une valeur

### `--admin-use-security-key`

Utilisation ou non d’une fonctionnalité &quot;clé de sécurité&quot; dans les URL et les formulaires d’administration du Magento. Obsolète, utilisez config:set avec le chemin admin/security/use_form_key

- Requiert une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:uninstall`

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

Désinstallation de l’application de Magento


### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `setup:upgrade`

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Mises à niveau de l’application Magento, des données de base de données et des schémas


### `--keep-generated`

Empêche la suppression des fichiers générés. Nous vous déconseillons d’utiliser cette option, sauf lors d’un déploiement en production. Pour plus d’informations, consultez votre intégrateur ou votre administrateur système.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--convert-old-scripts`

Permet de convertir les anciens scripts (InstallSchema, UpgradeSchema) au format db_schema.xml .

- Valeur par défaut : `false`
- Accepte une valeur

### `--safe-mode`

Installation sécurisée d’un Magento avec des vidages lors d’opérations destructrices, comme la suppression de colonnes

- Accepte une valeur

### `--data-restore`

Restauration des données supprimées des vidages

- Accepte une valeur

### `--dry-run`

L&#39;installation du Magento sera exécutée en mode Exécution sec

- Valeur par défaut : `false`
- Accepte une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : &quot;MAGE_MODE=developer&amp;MAGE_DIRS&quot;[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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


## `store:list`

```bash
bin/magento store:list
```

Affiche la liste des magasins


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


## `store:website:list`

```bash
bin/magento store:website:list
```

Affiche la liste des sites web


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


## `support:backup:code`

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

Création d’une sauvegarde de code


### `--name`

Nom de l’image

- Accepte une valeur

### `--output`, `-o`

Chemin de sortie

- Accepte une valeur

### `--logs`, `-l`

Inclure les journaux

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


## `support:backup:db`

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

Création d’une sauvegarde DB


### `--name`

Nom de l’image

- Accepte une valeur

### `--output`, `-o`

Chemin de sortie

- Accepte une valeur

### `--logs`, `-l`

Inclure les journaux

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--ignore-sanitize`, `-i`

Ignorer l’assainissement

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


## `support:utility:check`

```bash
bin/magento support:utility:check [--hide-paths]
```

Vérifier les utilitaires de sauvegarde requis


### `--hide-paths`

Vérifiez uniquement les utilitaires de console requis

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


## `support:utility:paths`

```bash
bin/magento support:utility:paths [-f|--force]
```

Créer une liste de chemins d’accès aux utilitaires


### `--force`, `-f`

Force

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


## `theme:uninstall`

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

Désinstallation du thème



### `theme`

Chemin du thème. Le chemin d’accès au thème doit être spécifié sous la forme d’un chemin d’accès complet, qui est zone/fournisseur/nom. Par exemple, frontal/Magento/vide

- Valeur par défaut : `[]`

- Obligatoire
- Tableau

### `--backup-code`

Sauvegarde du code (à l’exclusion des fichiers temporaires)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--clear-static-content`, `-c`

Effacez les fichiers d’affichage statique générés.

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


## `varnish:vcl:generate`

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

Génère un VCL vernis et l’ajoute à la ligne de commande


### `--access-list`

Liste d’accès aux adresses IP pouvant purger le vernis

- Valeur par défaut : `localhost`
- Requiert une valeur

### `--backend-host`

Hôte du serveur principal web

- Valeur par défaut : `localhost`
- Requiert une valeur

### `--backend-port`

Port du serveur principal web

- Valeur par défaut : `8080`
- Requiert une valeur

### `--export-version`

Version du fichier vernis

- Valeur par défaut : `6`
- Requiert une valeur

### `--grace-period`

Période de grâce en secondes

- Valeur par défaut : `300`
- Requiert une valeur

### `--input-file`

Fichier d’entrée pour générer vcl à partir de

- Requiert une valeur

### `--output-file`

Chemin d’accès au fichier pour l’écriture de vcl

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


## `webhooks:dev:run`

```bash
bin/magento webhooks:dev:run <name> <payload>
```

Exécute un webhook enregistré à des fins de développement.



### `name`

Nom du webhook

- Obligatoire

### `payload`

Charge utile du webhook au format JSON

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


## `webhooks:generate:module`

```bash
bin/magento webhooks:generate:module
```

Génération de modules externes en fonction des enregistrements de webhook


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


## `webhooks:info`

```bash
bin/magento webhooks:info [--depth [DEPTH]] [--] <webhook-name> [<webhook-type>]
```

Renvoie la charge utile du webhook spécifié.



### `webhook-name`

Nom de la méthode webhook

- Obligatoire

### `webhook-type`

Type de webhook (avant, après)

- Valeur par défaut : `before`


### `--depth`

Le nombre de niveaux dans la payload du webhook à renvoyer.

- Valeur par défaut : `3`
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


## `webhooks:list`

```bash
bin/magento webhooks:list
```

Affiche la liste des webhooks abonnés


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


## `webhooks:list:all`

```bash
bin/magento webhooks:list:all <module_name>
```

Renvoie une liste de noms de méthode webhook pris en charge pour le module spécifié



### `module_name`

Nom du module

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
