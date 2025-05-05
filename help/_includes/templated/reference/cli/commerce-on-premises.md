---
source-git-commit: ba444c5f74cdeec86c842014d02775faf16b2f50
workflow-type: tm+mt
source-wordcount: '8253'
ht-degree: 1%

---
# bin/magento (Adobe Commerce on-premise)

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->

**Version** : 2.4.8

Cette référence contient 145 commandes disponibles via l’outil de ligne de commande `bin/magento`.
La liste initiale est générée automatiquement à l’aide de la commande `bin/magento list` dans Adobe Commerce.

## Général

Utilisez le guide [« Ajouter des commandes d’interface de ligne de commande »](https://developer.adobe.com/commerce/php/development/cli-commands/) pour ajouter une commande d’interface de ligne de commande personnalisée.

Vous pouvez appeler `bin/magento` commandes de l’interface de ligne de commande à l’aide de raccourcis au lieu du nom complet de la commande. Par exemple, vous pouvez appeler `bin/magento setup:upgrade` en utilisant `bin/magento s:up`, `bin/magento s:upg`. Voir [syntaxe des raccourcis](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) pour comprendre comment utiliser des raccourcis avec n’importe quelle commande d’interface de ligne de commande.

Cette documentation de référence est générée à partir du code source de l’application. Pour modifier la documentation, vous devez ouvrir une pull request pour la commande correspondante dans le référentiel codebase[&#128279;](https://github.com/magento) approprié. Voir [Code Contributions](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) pour plus d’informations.

### Options globales

#### `--help`, `-h`

Afficher l’aide pour la commande donnée. Lorsqu’aucune commande n’est fournie, afficher l’aide pour la commande de liste

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--quiet`, `-q`

Ne pas générer de message

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus verbose et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--version`, `-V`

Afficher cette version de l&#39;application

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--ansi`

Forcer (ou désactiver --no-ansi) la sortie ANSI

- N’accepte pas de valeur

#### `--no-ansi`

Annulez l’option « --asi »

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--no-interaction`, `-n`

Ne posez aucune question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `_complete`

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

Commande interne pour fournir des suggestions de fin de shell

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).

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
bin/magento completion [--debug] [--] [<shell>]
```

Vider le script de fin du shell

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
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```

Affichage de l’aide d’une commande

```
The help command displays help for a given command:

  bin/magento help list

You can also output the help in other formats by using the --format option:

  bin/magento help --format=xml list

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


## `admin:adobe-ims:disable`

```bash
bin/magento admin:adobe-ims:disable
```

Désactiver le module Adobe IMS

### Options

Pour les options globales, voir [Options globales](#global-options).


## `admin:adobe-ims:enable`

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

Activez le module Adobe IMS.

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--organization-id`, `-o`

Définissez l’ID d’organisation pour la configuration Adobe IMS. Obligatoire lors de l’activation du module

- Accepte une valeur

#### `--client-id`, `-c`

Définissez l’identifiant client pour la configuration Adobe IMS. Obligatoire lors de l’activation du module

- Accepte une valeur

#### `--client-secret`, `-s`

Définissez le secret client pour la configuration Adobe IMS. Obligatoire lors de l’activation du module

- Accepte une valeur

#### `--2fa`, `-t`

Vérifiez si 2FA est activé pour l’organisation dans Adobe Admin Console. Obligatoire lors de l’activation du module

- Accepte une valeur


## `admin:adobe-ims:info`

```bash
bin/magento admin:adobe-ims:info
```

Informations sur Adobe configuration du module IMS

### Options

Pour les options globales, voir [Options globales](#global-options).


## `admin:adobe-ims:status`

```bash
bin/magento admin:adobe-ims:status
```

Statut du module Adobe IMS

### Options

Pour les options globales, voir [Options globales](#global-options).


## `admin:user:create`

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Crée un administrateur

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--admin-user`

(Obligatoire) Utilisateur administrateur

- Requiert une valeur

#### `--admin-password`

(Obligatoire) Mot de passe administrateur

- Requiert une valeur

#### `--admin-email`

(Obligatoire) Adresse électronique de l’administrateur

- Requiert une valeur

#### `--admin-firstname`

(Obligatoire) Prénom de l’administrateur

- Requiert une valeur

#### `--admin-lastname`

(Obligatoire) Nom de l’administrateur

- Requiert une valeur

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `admin:user:unlock`

```bash
bin/magento admin:user:unlock <username>
```

Déverrouiller le compte administrateur

```
This command unlocks an admin account by its username.
To unlock:
      bin/magento admin:user:unlock username
```

### Arguments

#### `username`

Nom d’utilisateur administrateur à déverrouiller

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).


## `app:config:dump`

```bash
bin/magento app:config:dump [<config-types>...]
```

Créer un vidage de l’application

### Arguments

#### `config-types`

Liste séparée par des espaces de types de configuration ou omettre pour vider toutes les [portées, thèmes, système, i18n]

- Valeur par défaut : `[]`
- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).


## `app:config:import`

```bash
bin/magento app:config:import
```

Importer les données des fichiers de configuration partagés vers le stockage de données approprié

### Options

Pour les options globales, voir [Options globales](#global-options).


## `app:config:status`

```bash
bin/magento app:config:status
```

Vérifie si la propagation de la configuration nécessite une mise à jour

### Options

Pour les options globales, voir [Options globales](#global-options).


## `braintree:migrate`

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

Migration des cartes stockées à partir d’une base de données Magento 1

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--host`

Nom d’hôte/adresse IP. Port facultatif

- Requiert une valeur

#### `--dbname`

Nom de la base

- Nécessite une valeur

#### `--username`

Nom d’utilisateur de la base de données. Doit disposer d’un accès en lecture

- Nécessite une valeur

#### `--password`

Mot de passe

- Nécessite une valeur


## `cache:clean`

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Nettoie le(s) type(s) de cache

### Arguments

#### `types`

Liste des types de cache séparés par des espaces. ou omettez de l’appliquer à tous les types de cache.

- Faire défaut: `[]`
- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--bootstrap`

ajouter ou remplacer des paramètres du bootstrap

- Requiert une valeur


## `cache:clean:payment_services_merchant_scopes`

```bash
bin/magento cache:clean:payment_services_merchant_scopes
```

Nettoyer le cache des portées des commerçants des services de paiement

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `cache:disable`

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Désactive le(s) type(s) de cache.

### Arguments

#### `types`

Liste séparée par des espaces de types de cache à appliquer à tous les types de cache.

- Valeur par défaut : `[]`
- Tableau

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).

#### `--bootstrap`

Ajouter ou remplacer des paramètres de l’amorçage

- Nécessite une valeur


## `cache:enable`

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Active le(s) type(s) de cache

### Arguments

#### `types`

Liste des types de cache séparés par des espaces. ou omettez de l’appliquer à tous les types de cache.

- Faire défaut: `[]`
- Tableau

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).

#### `--bootstrap`

Ajouter ou remplacer des paramètres de l’amorçage

- Nécessite une valeur


## `cache:flush`

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Vide le stockage en cache utilisé par type(s) de cache

### Arguments

#### `types`

Liste des types de cache séparés par des espaces. ou omettez de l’appliquer à tous les types de cache.

- Faire défaut: `[]`
- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--bootstrap`

ajouter ou remplacer des paramètres du bootstrap

- Requiert une valeur


## `cache:status`

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

Vérifie l’état du cache

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--bootstrap`

ajouter ou remplacer des paramètres du bootstrap

- Requiert une valeur


## `catalog:images:resize`

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

Crée des images de produit redimensionnées.

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--async`, `-a`

Redimensionnement d’une image en mode asynchrone

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--skip_hidden_images`

Ne pas traiter les images marquées comme masquées dans la page produit

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `catalog:product:attributes:cleanup`

```bash
bin/magento catalog:product:attributes:cleanup
```

Supprime les attributs de produit inutilisés.

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `cms:wysiwyg:restrict`

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

Indiquez s’il faut appliquer la validation du contenu HTML utilisateur ou afficher un avertissement à la place

### Arguments

#### `restrict`

o\n

- Obligatoire

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `config:sensitive:set`

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

Définition de valeurs de configuration sensibles

### Arguments

#### `path`

Chemin de configuration par exemple group/section/field_name


#### `value`

Valeur de configuration

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--interactive`, `-i`

Activez le mode interactif pour définir toutes les variables sensibles

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--scope`

Étendue de la configuration, si non définie, utiliser &#39;default&#39;

- Faire défaut: `default`
- Accepte une valeur

#### `--scope-code`

Code d’étendue pour la configuration, chaîne vide par défaut

- Valeur par défaut : «
- Accepte une valeur


## `config:set`

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

Modifier la configuration du système

### Arguments

#### `path`

Chemin de configuration au format section/group/field_name

- Obligatoire


#### `value`

Valeur de configuration

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--scope`

Étendue de la configuration (par défaut, site web ou magasin)

- Valeur par défaut : `default`
- Requiert une valeur

#### `--scope-code`

Code de portée (obligatoire uniquement si la portée n’est pas « par défaut »)

- Requiert une valeur

#### `--lock-env`, `-e`

Valeur de verrouillage qui empêche toute modification dans l’Admin (sera enregistrée dans app/etc/env.php)

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--lock-config`, `-c`

Verrouiller et partager la valeur avec d&#39;autres installations, empêche toute modification dans l&#39;Admin (sera enregistrée dans app/etc/config.php)

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--lock`, `-l`

Obsolète, utilisez plutôt l’option —lock-env .

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `config:show`

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

Affiche la valeur de configuration pour le chemin donné. Si le chemin n’est pas spécifié, toutes les valeurs enregistrées s’affichent

### Arguments

#### `path`

Chemin d’accès à la configuration ; par exemple, section_id/group_id/field_id

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--scope`

Portée de la configuration : si elle n’est pas spécifiée, la portée « par défaut » est utilisée

- Valeur par défaut : `default`
- Accepte une valeur

#### `--scope-code`

Code de portée (obligatoire uniquement si la portée n’est pas `default`)

- Valeur par défaut : «
- Accepte une valeur


## `cron:install`

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

Génère et installe crontab pour l’utilisateur actuel

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--force`, `-f`

Forcer les tâches d&#39;installation

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--non-optional`, `-d`

Installez uniquement les tâches non facultatives (par défaut)

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `cron:remove`

```bash
bin/magento cron:remove
```

Supprime les tâches de crontab

### Options

Pour les options globales, voir [Options globales](#global-options).


## `cron:run`

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

Exécute les traitements par planning

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--group`

Exécuter les traitements uniquement à partir du groupe spécifié

- Requiert une valeur

#### `--exclude-group`

Exclure des tâches du groupe spécifié

- Faire défaut: `[]`
- Accepte plusieurs valeurs

#### `--bootstrap`

Ajouter ou remplacer des paramètres de l’amorçage

- Nécessite une valeur


## `customer:hash:upgrade`

```bash
bin/magento customer:hash:upgrade
```

Mettez à niveau le hachage du client selon le dernier algorithme

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `deploy:mode:set`

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

Définissez le mode d’application.

### Arguments

#### `mode`

Mode d’application à définir. Les options disponibles sont « développeur » ou « production »

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--skip-compilation`, `-s`

Ignore l’effacement et la régénération du contenu statique (code généré, CSS prétraité et ressources dans pub/static/)

- Faire défaut: `false`
- N’accepte aucune valeur


## `deploy:mode:show`

```bash
bin/magento deploy:mode:show
```

Affiche le mode d&#39;application actuel.

### Options

Pour les options globales, voir [Options globales](#global-options).


## `dev:di:info`

```bash
bin/magento dev:di:info <class> [<area>]
```

Fournit des informations sur la configuration de l’injection de dépendance pour la commande .

### Arguments

#### `class`

Nom de la classe

- Obligatoire


#### `area`

Indicatif

### Options

Pour les options globales, voir [Options globales](#global-options).


## `dev:email:newsletter-compatibility-check`

```bash
bin/magento dev:email:newsletter-compatibility-check
```

Analyse les modèles de newsletter pour détecter d’éventuels problèmes de compatibilité d’utilisation des variables

### Options

Pour les options globales, voir [Options globales](#global-options).


## `dev:email:override-compatibility-check`

```bash
bin/magento dev:email:override-compatibility-check
```

Analyse les remplacements du modèle d’e-mail à la recherche de problèmes potentiels de compatibilité d’utilisation des variables

### Options

Pour les options globales, voir [Options globales](#global-options).


## `dev:profiler:disable`

```bash
bin/magento dev:profiler:disable
```

Désactivez le profileur.

### Options

Pour les options globales, voir [Options globales](#global-options).


## `dev:profiler:enable`

```bash
bin/magento dev:profiler:enable [<type>]
```

Activez le profileur.

### Arguments

#### `type`

Type de profileur

### Options

Pour les options globales, voir [Options globales](#global-options).


## `dev:query-log:disable`

```bash
bin/magento dev:query-log:disable
```

Désactiver la journalisation des requêtes de base de données

### Options

Pour les options globales, voir [Options globales](#global-options).


## `dev:query-log:enable`

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

Activer la journalisation des requêtes de base de données

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--include-all-queries`

Enregistrer toutes les requêtes. [true\|false]

- Faire défaut: `true`
- Accepte une valeur

#### `--query-time-threshold`

Seuils de durée de requête.

- Faire défaut: `0.001`
- Accepte une valeur

#### `--include-call-stack`

Inclure la pile d’appels. [true\|false]

- Faire défaut: `true`
- Accepte une valeur


## `dev:source-theme:deploy`

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

Collecte et publie les fichiers source du thème.

### Arguments

#### `file`

Fichiers à prétraiter (le fichier doit être spécifié sans extension)

- Faire défaut: `css/styles-mcss/styles-l`

- Tableau

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).

#### `--type`

Type de fichiers source : [moins]

- Faire défaut: `less`
- Nécessite une valeur

#### `--locale`

Paramètres régionaux : [en_US]

- Faire défaut: `en_US`
- Nécessite une valeur

#### `--area`

Zone : [frontend\|adminhtml]

- Faire défaut: `frontend`
- Nécessite une valeur

#### `--theme`

Thème : [Fournisseur/thème]

- Faire défaut: `Magento/luma`
- Nécessite une valeur


## `dev:template-hints:disable`

```bash
bin/magento dev:template-hints:disable
```

Désactivez les conseils de modèle frontend. Un vidage du cache peut être nécessaire.

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `dev:template-hints:enable`

```bash
bin/magento dev:template-hints:enable
```

Activez les conseils de modèle frontaux. Un vidage du cache peut être nécessaire.

### Options

Pour les options globales, voir [Options globales](#global-options).


## `dev:template-hints:status`

```bash
bin/magento dev:template-hints:status
```

Afficher le statut des indications du modèle front-end.

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `dev:tests:run`

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

Exécute des tests

### Arguments

#### `type`

Type de test à exécuter. Types disponibles : all, unit, integration-all, static, static-all, integrity, hérité, défaut

- Valeur par défaut : `default`

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--arguments`, `-c`

Arguments supplémentaires pour PHPUnit. Exemple : « -c&#39;—filter=MyTest&#39;«  (sans espaces)

- Valeur par défaut : «
- Requiert une valeur


## `dev:urn-catalog:generate`

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

Génère le catalogue d’URN vers les mappages *.xsd pour que l’IDE mette en surbrillance le format xml.

### Arguments

#### `path`

Chemin d’accès au fichier pour la sortie du catalogue. Pour PhpStorm, utilisez .idea/misc.xml

- Obligatoire

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).

#### `--ide`

Format dans lequel le catalogue sera généré. Pris en charge : [phpstorm, vscode]

- Faire défaut: `phpstorm`
- Nécessite une valeur


## `dev:xml:convert`

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

Conversion du fichier XML à l’aide de feuilles de style XSL

### Arguments

#### `xml-file`

Chemin d’accès au fichier XML à transformer

- Obligatoire


#### `processor`

Chemin d’accès à la feuille de style XSL à appliquer au fichier XML

- Obligatoire

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).

#### `--overwrite`, `-o`

Ecraser le fichier XML

- Faire défaut: `false`
- N’accepte aucune valeur


## `downloadable:domains:add`

```bash
bin/magento downloadable:domains:add [<domains>...]
```

Ajouter des domaines à la liste autorisée des domaines téléchargeables

### Arguments

#### `domains`

Nom des domaines

- Valeur par défaut : `[]`
- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).


## `downloadable:domains:remove`

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

Supprimer des domaines de la liste autorisée des domaines téléchargeables

### Arguments

#### `domains`

Noms de domaine

- Faire défaut: `[]`
- Tableau

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `downloadable:domains:show`

```bash
bin/magento downloadable:domains:show
```

Afficher la liste autorisée des domaines téléchargeables

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `encryption:data:list-re-encryptors`

```bash
bin/magento encryption:data:list-re-encryptors
```

Affiche la liste des rechiffreurs de données disponibles.

### Options

Pour les options globales, voir [Options globales](#global-options).


## `encryption:data:re-encrypt`

```bash
bin/magento encryption:data:re-encrypt [<encryptors>...]
```

Rechiffre les données chiffrées à l’aide de la clé de chiffrement actuelle.

### Arguments

#### `encryptors`

Liste séparée par des espaces des rechiffreurs à utiliser.

- Valeur par défaut : `[]`
- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).


## `encryption:key:change`

```bash
bin/magento encryption:key:change [-k|--key [KEY]]
```

Modifiez la clé de chiffrement dans le fichier env.php.

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--key`, `-k`

La clé doit être une chaîne de 32 caractères. Si elle n’est pas fournie, une clé aléatoire est générée.

- Accepte une valeur


## `encryption:payment-data:update`

```bash
bin/magento encryption:payment-data:update
```

Rechiffre les données de carte de crédit chiffrées avec le dernier chiffrement.

### Options

Pour les options globales, voir [Options globales](#global-options).


## `events:create-event-provider`

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]events:provider:create 
```

Créez un fournisseur d’événements personnalisé dans Adobe I/O Events pour cette instance. Si vous ne spécifiez pas les options de libellé et de description, celles-ci doivent être définies dans le fichier système app/etc/event-types.json.

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--label`

Libellé permettant de définir votre fournisseur personnalisé.

- Accepte une valeur

#### `--description`

Description de votre fournisseur.

- Accepte une valeur


## `events:generate:module`

```bash
bin/magento events:generate:module
```

Génération du module en fonction de la liste des modules externes

### Options

Pour les options globales, voir [Options globales](#global-options).


## `events:info`

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```

Renvoie la payload de l’événement spécifié.

### Arguments

#### `event-code`

Code de l’événement

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--depth`

Nombre de niveaux dans la payload d&#39;événement à renvoyer

- Valeur par défaut : `2`
- Accepte une valeur


## `events:list`

```bash
bin/magento events:list
```

Affiche la liste des événements avec abonnement

### Options

Pour les options globales, voir [Options globales](#global-options).


## `events:list:all`

```bash
bin/magento events:list:all <module_name>
```

Renvoie une liste d’événements auxquels vous pouvez vous abonner définis dans le module spécifié

### Arguments

#### `module_name`

Nom du module

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).


## `events:metadata:populate`

```bash
bin/magento events:metadata:populate
```

Crée des métadonnées dans Adobe I/O à partir de la liste de configuration (configurations XML et d’application).

### Options

Pour les options globales, voir [Options globales](#global-options).


## `events:provider:info`

```bash
bin/magento events:provider:info
```

Renvoie des détails sur le fournisseur d’événements configuré

### Options

Pour les options globales, voir [Options globales](#global-options).


## `events:registrations:list`

```bash
bin/magento events:registrations:list
```

Répertorie les enregistrements d’événements dans votre projet App Builder

### Options

Pour les options globales, voir [Options globales](#global-options).


## `events:subscribe`

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [-d|--destination DESTINATION] [--hipaaAuditRequired] [--] <event-code>
```

S’abonne à l’événement

### Arguments

#### `event-code`

Code de l’événement

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--force`, `-f`

Force l&#39;abonnement à l&#39;événement spécifié, même s&#39;il n&#39;a pas été défini localement.

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--fields`

La liste des champs dans la payload des données d&#39;événement.

- Valeur par défaut : `[]`
- Requiert une valeur

#### `--parent`

Code d’événement parent pour un abonnement à un événement avec des règles ou comme alias.

- Requiert une valeur

#### `--rules`

Liste des règles pour l’abonnement à l’événement, où chaque règle est formatée en tant que « champ\|opérateur\|valeur ». Pour utiliser cette option, vous devez également spécifier l’option « parent ».

- Valeur par défaut : `[]`
- Requiert une valeur

#### `--priority`, `-p`

Accélère la transmission de cet événement. Spécifiez cette option pour les événements qui doivent être diffusés immédiatement. Par défaut, les événements sont envoyés par cron une fois par minute.

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--destination`, `-d`

Destination de cet événement. Spécifiez cette option pour les événements qui doivent être diffusés à la destination personnalisée.

- Valeur par défaut : `default`
- Requiert une valeur

#### `--hipaaAuditRequired`

Indique que l’événement contient des données soumises au contrôle HIPAA.

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `events:sync-events-metadata`

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

Synchroniser les métadonnées d’événement pour cette instance

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--delete`, `-d`

Suppression des métadonnées d’événement devenues inutiles

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `events:unsubscribe`

```bash
bin/magento events:unsubscribe <event-code>
```

Supprime l’abonnement à l’événement fourni

### Arguments

#### `event-code`

Code d’événement auquel se désabonner

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).


## `i18n:collect-phrases`

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

Découvre les expressions dans la base de code

### Arguments

#### `directory`

Chemin du répertoire à analyser. Pas nécessaire si l&#39;indicateur —magento est défini

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--output`, `-o`

Chemin (nom de fichier inclus) vers un fichier de sortie. Si aucun fichier n’est spécifié, la valeur par défaut est stdout.

- Requiert une valeur

#### `--magento`, `-m`

Utilisez le paramètre —magento pour analyser la base de code Magento actuelle. Omettez le paramètre si un répertoire est spécifié.

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `i18n:pack`

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

Enregistre le package de langue

### Arguments

#### `source`

Chemin d’accès au fichier du dictionnaire source avec les traductions

- Obligatoire


#### `locale`

Paramètres régionaux cibles pour le dictionnaire ; par exemple, « de_DE »

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--mode`, `-m`

Mode d’enregistrement pour dictionnaire - « remplacer » - remplacer le module linguistique par un nouveau - « fusionner » - fusionner les packages linguistiques, par défaut « remplacer »

- Valeur par défaut : `replace`
- Requiert une valeur

#### `--allow-duplicates`, `-d`

Utilisez le paramètre —allow-duplicates pour enregistrer les doublons de la traduction. Sinon, omettez le paramètre .

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `i18n:uninstall`

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

Désinstalle les packages de langue

### Arguments

#### `package`

Nom du package de langue

- Valeur par défaut : `[]`
- Obligatoire

- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--backup-code`, `-b`

Sauvegarde du code et des fichiers de configuration (à l’exclusion des fichiers temporaires)

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `indexer:info`

```bash
bin/magento indexer:info
```

Affiche les indexeurs autorisés

### Options

Pour les options globales, voir [Options globales](#global-options).


## `indexer:reindex`

```bash
bin/magento indexer:reindex [<index>...]
```

Réindexer les données

### Arguments

#### `index`

Liste séparée par des espaces de types d’index à appliquer à tous les index ou à omettre.

- Valeur par défaut : `[]`
- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).


## `indexer:reset`

```bash
bin/magento indexer:reset [<index>...]
```

Réinitialise le statut de l’indexeur sur non valide

### Arguments

#### `index`

Liste séparée par des espaces de types d’index à appliquer à tous les index ou à omettre.

- Valeur par défaut : `[]`
- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).


## `indexer:set-dimensions-mode`

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

Définir le mode des dimensions de l’indexeur

### Arguments

#### `indexer`

Nom de [l’indexeur catalog_product_price|catalogpermissions_category]


#### `mode`

Modes de dimension de l’indexeur catalog_product_price aucun, site web, customer_group, website_and_customer_group catalogpermissions_category aucun, customer_group

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `indexer:set-mode`

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

Définit le type de mode d’index

### Arguments

#### `mode`

Type de mode [indexeur en temps réel|planification]


#### `index`

Liste des types d’index séparés par des espaces, ou omettez de s’appliquer à tous les index.

- Faire défaut: `[]`
- Tableau

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `indexer:set-status`

```bash
bin/magento indexer:set-status <status> [<index>...]
```

Définit l’état de l’indexeur spécifié

### Arguments

#### `status`

Type [d’état de l’indexeur invalide|suspendu|valide]

- Obligatoire


#### `index`

Liste des types d’index séparés par des espaces, ou omettez de s’appliquer à tous les index.

- Faire défaut: `[]`
- Tableau

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `indexer:show-dimensions-mode`

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

Affiche le mode Dimension de l’indexeur

### Arguments

#### `indexer`

Liste des types d’index séparés par des espaces ou omettre pour s’appliquer à tous les index (catalog_product_price catalogpermissions_category)

- Faire défaut: `[]`
- Tableau

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `indexer:show-mode`

```bash
bin/magento indexer:show-mode [<index>...]
```

Affiche le mode Index

### Arguments

#### `index`

Liste des types d’index séparés par des espaces, ou omettez de s’appliquer à tous les index.

- Faire défaut: `[]`
- Tableau

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `indexer:status`

```bash
bin/magento indexer:status [<index>...]
```

Affiche l’état de l’indexeur

### Arguments

#### `index`

Liste des types d’index séparés par des espaces, ou omettez de s’appliquer à tous les index.

- Faire défaut: `[]`
- Tableau

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `info:adminuri`

```bash
bin/magento info:adminuri
```

Affiche l’URI Magento admin

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `info:backups:list`

```bash
bin/magento info:backups:list
```

Imprime la liste des fichiers de sauvegarde disponibles.

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `info:currency:list`

```bash
bin/magento info:currency:list
```

Affiche la liste des devises disponibles

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `info:dependencies:show-framework`

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

Affiche le nombre de dépendances sur Magento framework

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).

#### `--output`, `-o`

Nom de fichier du rapport

- Valeur par défaut : `framework-dependencies.csv`
- Requiert une valeur


## `info:dependencies:show-modules`

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

Affiche le nombre de dépendances entre les modules

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--output`, `-o`

Nom de fichier du rapport

- Faire défaut: `modules-dependencies.csv`
- Nécessite une valeur


## `info:dependencies:show-modules-circular`

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

Affiche le nombre de dépendances circulaires entre les modules

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--output`, `-o`

Nom de fichier du rapport

- Valeur par défaut : `modules-circular-dependencies.csv`
- Requiert une valeur


## `info:language:list`

```bash
bin/magento info:language:list
```

Affiche la liste des paramètres régionaux de langue disponibles

### Options

Pour les options globales, voir [Options globales](#global-options).


## `info:timezone:list`

```bash
bin/magento info:timezone:list
```

Affiche la liste des fuseaux horaires disponibles

### Options

Pour les options globales, voir [Options globales](#global-options).


## `inventory:reservation:create-compensations`

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

Créer des réserves à l’aide des arguments de compensation fournis

### Arguments

#### `compensations`

Liste des arguments de rémunération au format « ::: »

- Valeur par défaut : `[]`
- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--raw`, `-r`

Sortie brute

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `inventory:reservation:list-inconsistencies`

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

Afficher toutes les commandes et tous les produits présentant des incohérences de quantité vendable

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--complete-orders`, `-c`

Afficher uniquement les incohérences pour les commandes complètes

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--incomplete-orders`, `-i`

Afficher uniquement les incohérences pour les commandes incomplètes

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--bunch-size`, `-b`

Définit le nombre de commandes à charger simultanément

- Valeur par défaut : `50`
- Accepte une valeur

#### `--raw`, `-r`

Sortie brute

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `inventory-geonames:import`

```bash
bin/magento inventory-geonames:import <countries>...
```

Téléchargement et importation de noms géographiques pour l’algorithme de sélection de source

### Arguments

#### `countries`

Liste des codes pays à importer

- Valeur par défaut : `[]`
- Obligatoire

- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).


## `maintenance:allow-ips`

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

Définit les adresses IP exemptées du mode de maintenance

### Arguments

#### `ip`

Adresses IP autorisées

- Valeur par défaut : `[]`
- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--none`

Effacer les adresses IP autorisées

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--add`

Ajouter l’adresse IP à la liste existante

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `maintenance:disable`

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Désactive le mode de maintenance

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--ip`

Adresses IP autorisées (utilisez &#39;aucune&#39; pour effacer la liste des adresses IP autorisées)

- Valeur par défaut : `[]`
- Requiert une valeur

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `maintenance:enable`

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Active le mode de maintenance

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--ip`

Adresses IP autorisées (utilisez &#39;aucune&#39; pour effacer la liste des adresses IP autorisées)

- Valeur par défaut : `[]`
- Requiert une valeur

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `maintenance:status`

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Affiche l’état du mode de maintenance

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `media-content:sync`

```bash
bin/magento media-content:sync
```

Synchronisation du contenu avec les ressources

### Options

Pour les options globales, voir [Options globales](#global-options).


## `media-gallery:sync`

```bash
bin/magento media-gallery:sync
```

Synchroniser le stockage multimédia et les ressources multimédias dans la base de données

### Options

Pour les options globales, voir [Options globales](#global-options).


## `module:config:status`

```bash
bin/magento module:config:status
```

Vérifie la configuration des modules dans le fichier &#39;app/etc/config.php&#39; et indique s&#39;ils sont à jour ou non

### Options

Pour les options globales, voir [Options globales](#global-options).


## `module:disable`

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Désactive les modules spécifiés

### Arguments

#### `module`

Nom du module

- Valeur par défaut : `[]`
- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--force`, `-f`

Contournement de la vérification des dépendances

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--all`

Désactiver tous les modules

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--clear-static-content`, `-c`

Effacez les fichiers d’affichage statique générés. Nécessaire, si le ou les modules ont des fichiers de vue statiques

- Valeur par défaut : `false`
- N’accepte pas de valeur

#### `--magento-init-params`

Ajouter à n’importe quelle commande pour personnaliser Magento paramètres d’initialisation Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur


## `module:enable`

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Active les modules spécifiés

### Arguments

#### `module`

Nom du module

- Valeur par défaut : `[]`
- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--force`, `-f`

Contournement de la vérification des dépendances

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--all`

Activer tous les modules

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--clear-static-content`, `-c`

Effacez les fichiers d’affichage statique générés. Nécessaire, si le ou les modules ont des fichiers de vue statiques

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--magento-init-params`

Ajouter à n’importe quelle commande pour personnaliser Magento paramètres d’initialisation Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur


## `module:status`

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

Affiche l’état des modules

### Arguments

#### `module-names`

Nom de module facultatif

- Faire défaut: `[]`
- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--enabled`

Modules activés pour l’impression uniquement

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--disabled`

Modules désactivés d’impression seulement

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `module:uninstall`

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

Désinstalle les modules installés par le compositeur

### Arguments

#### `module`

Nom du module

- Valeur par défaut : `[]`
- Obligatoire

- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--remove-data`, `-r`

Supprimer les données installées par le(s) module(s)

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--backup-code`

Effectuez une sauvegarde du code et des fichiers de configuration (sauf fichiers temporaires)

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--backup-media`

Effectuez une sauvegarde multimédia

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--backup-db`

Effectuez une sauvegarde complète de la base de données

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--non-composer`

Tous les modules qui seront passés ici ne seront pas basés sur le compositeur

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--clear-static-content`, `-c`

Effacez les fichiers d’affichage statique générés. Nécessaire, si le ou les modules ont des fichiers d’affichage statique

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `newrelic:create:deploy-marker`

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

Vérifiez les entrées dans la file d’attente de déploiement et créez un marqueur de déploiement approprié.

### Arguments

#### `message`

Déployer le message ?

- Obligatoire


#### `change_log`

Journal des modifications ?

- Obligatoire


#### `user`

Utilisateur de déploiement


#### `revision`

Révision

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `queue:consumers:list`

```bash
bin/magento queue:consumers:list
```

Liste des consommateurs MessageQueue

```
This command shows list of MessageQueue consumers.
```

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `queue:consumers:restart`

```bash
bin/magento queue:consumers:restart
```

Redémarrage des consommateurs MessageQueue

```
Command put poison pill for MessageQueue consumers and force to restart them after next status check.
```

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `queue:consumers:start`

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

Démarrage de MessageQueue Consumer

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

### Arguments

#### `consumer`

Nom du client à démarrer.

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--max-messages`

Nombre de messages à traiter par le client avant la fin du processus. Si non spécifié - s’arrête après le traitement de tous les messages en file d’attente.

- Requiert une valeur

#### `--batch-size`

Nombre de messages par lot. Applicable uniquement au client par lots.

- Requiert une valeur

#### `--area-code`

La zone préférée (globale, adminhtml, etc.) par défaut est globale.

- Requiert une valeur

#### `--single-thread`

Cette option empêche l’exécution simultanée de plusieurs copies d’un client.

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--multi-process`

Nombre de processus par client.

- Accepte une valeur

#### `--pid-file-path`

Chemin d’accès au fichier d’enregistrement du PID (cette option est obsolète, utilisez plutôt —single-thread).

- Requiert une valeur


## `remote-storage:sync`

```bash
bin/magento remote-storage:sync
```

Synchronisez les fichiers multimédias avec le stockage distant.

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `saas:resync`

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync] [--by-ids BY-IDS] [--id-type ID-TYPE]
```

Resynchronise les données d’alimentation avec le service SaaS.

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).

#### `--feed`

Nom du flux à resynchroniser entièrement avec le service SaaS. Flux disponibles : Production de commande Payment Services, Sandbox de commande Payment Services, Production de statut de commande Payment Services, Sandbox de statut de commande Payment Services, Production de magasin Payment Services, Sandbox de magasin Payment Services

- Nécessite une valeur

#### `--no-reindex`

Exécutez une nouvelle soumission des données de flux au service SaaS uniquement. Ne réindexe pas. (Cette option ne s’applique pas aux produits, aux remplacements de produits, aux prix des flux)

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--cleanup-feed`

Forcer le nettoyage de la table de l’indexeur de flux avant la synchronisation.

- Faire défaut: `false`
- N’accepte aucune valeur

#### `--dry-run`

Exécution d’essai. Les données ne seront pas exportées. Pour enregistrer la payload dans le fichier journal var/log/saas-export.log, exécutez avec la variable d’environnement EXPORTER_EXTENDED_LOG=1.

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--thread-count`

Définissez le nombre de threads de synchronisation.

- Requiert une valeur

#### `--batch-size`

Définir la taille du lot de synchronisation

- Requiert une valeur

#### `--continue-resync`

Continuer la resynchronisation depuis la dernière position stockée (cette option s’applique aux produits, aux remplacements de produits, aux flux de prix).

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--by-ids`

Resynchroniser partiellement par la liste des identifiants fournis. (Cette option s’applique aux produits, aux remplacements de produit et aux flux de prix)

- Requiert une valeur

#### `--id-type`

Type des identifiants pour la resynchronisation partielle (par exemple : sku, productId, etc.)

- Requiert une valeur


## `sampledata:deploy`

```bash
bin/magento sampledata:deploy [--no-update]
```

Déployez des exemples de modules de données pour les installations Magento basées sur le compositeur.

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--no-update`

Mettez à jour composer.json sans exécuter la mise à jour du compositeur

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `sampledata:remove`

```bash
bin/magento sampledata:remove [--no-update]
```

Supprimer tous les exemples de packages de données de composer.json

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--no-update`

Mettez à jour composer.json sans exécuter la mise à jour du compositeur

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `sampledata:reset`

```bash
bin/magento sampledata:reset
```

Réinitialiser tous les exemples de modules de données pour la réinstallation

### Options

Pour les options globales, voir [Options globales](#global-options).


## `security:recaptcha:disable-for-user-forgot-password`

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

Désactiver reCAPTCHA pour le formulaire de mot de passe oublié de l’utilisateur administrateur

### Options

Pour les options globales, voir [Options globales](#global-options).


## `security:recaptcha:disable-for-user-login`

```bash
bin/magento security:recaptcha:disable-for-user-login
```

Désactiver reCAPTCHA pour le formulaire de connexion de l’utilisateur administrateur

### Options

Pour les options globales, voir [Options globales](#global-options).


## `security:tfa:google:set-secret`

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

Définissez le secret utilisé pour la génération du mot de passe à usage unique Google.

### Arguments

#### `user`

Nom d’utilisateur

- Obligatoire


#### `secret`

Secret

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).


## `security:tfa:providers`

```bash
bin/magento security:tfa:providers
```

Liste de tous les fournisseurs disponibles

### Options

Pour les options globales, voir [Options globales](#global-options).


## `security:tfa:reset`

```bash
bin/magento security:tfa:reset <user> <provider>
```

Réinitialiser la configuration pour un utilisateur

### Arguments

#### `user`

Nom d’utilisateur

- Obligatoire


#### `provider`

Code du fournisseur

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).


## `server:run`

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-wn|--workerNum [WORKERNUM]] [-dm|--dispatchMode [DISPATCHMODE]] [-mr|--maxRequests [MAXREQUESTS]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]] [-mwt|--maxWaitTime [MAXWAITTIME]] [--state-monitor]
```

Exécution du serveur d’applications

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--port`, `-p`

port sur lequel servir

- Valeur par défaut : `9501`
- Accepte une valeur

#### `--background`, `-b`

indicateur de mode d&#39;arrière-plan

- Valeur par défaut : `0`
- Accepte une valeur

#### `--workerNum`, `-wn`

Nombre de processus de travail à démarrer

- Faire défaut: `4`
- Accepte une valeur

#### `--dispatchMode`, `-dm`

Mode de distribution des connexions aux processus de travail

- Faire défaut: `3`
- Accepte une valeur

#### `--maxRequests`, `-mr`

Nombre maximum de requêtes avant le redémarrage du processus de travail

- Valeur par défaut : `10000`
- Accepte une valeur

#### `--area`, `-a`

zone du serveur d’applications

- Valeur par défaut : `graphql`
- Accepte une valeur

#### `--magento-init-params`, `-mip`

paramètres d’initialisation magento

- Valeur par défaut : «
- Accepte une valeur

#### `--maxWaitTime`, `-mwt`

la durée d&#39;attente des programmes de travail après le rechargement (par ex. config change) avant de les tuer

- Valeur par défaut : `3600`
- Accepte une valeur

#### `--state-monitor`

Activez la surveillance de l’état. N’utilisez cette option que pour déboguer des problèmes d’état.

- Faire défaut: `false`
- N’accepte pas de valeur


## `server:state-monitor:aggregate-output`

```bash
bin/magento server:state-monitor:aggregate-output
```

Sortie agrégée du moniteur d&#39;état d&#39;ApplicationServer

### Options

Pour les options globales, voir [Options globales](#global-options).


## `setup:backup`

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Sauvegarde de la base de code, du média et de la base de données de l’application Magento

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--code`

Sauvegarde du code et des fichiers de configuration (à l’exclusion des fichiers temporaires)

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--media`

Effectuer une sauvegarde du média

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--db`

Effectuer une sauvegarde complète de la base de données

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `setup:config:set`

```bash
bin/magento setup:config:set [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Crée ou modifie la configuration de déploiement

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--remote-storage-driver`

Pilote de stockage distant

- Requiert une valeur

#### `--remote-storage-prefix`

Préfixe de stockage distant

- Valeur par défaut : «
- Requiert une valeur

#### `--remote-storage-endpoint`

Point d’entrée de stockage distant

- Requiert une valeur

#### `--remote-storage-bucket`

Compartiment de stockage distant

- Requiert une valeur

#### `--remote-storage-region`

Région de stockage distante

- Requiert une valeur

#### `--remote-storage-key`

Clé d’accès au stockage distant

- Valeur par défaut : «
- Requiert une valeur

#### `--remote-storage-secret`

Clé secrète de stockage distant

- Valeur par défaut : «
- Requiert une valeur

#### `--remote-storage-path-style`

Style du chemin de stockage distant

- Valeur par défaut : `0`
- Requiert une valeur

#### `--backend-frontname`

Nom du front-end (sera généré automatiquement s’il est manquant)

- Requiert une valeur

#### `--enable-debug-logging`

Activer la journalisation du débogage

- Requiert une valeur

#### `--enable-syslog-logging`

Activer la journalisation syslog

- Requiert une valeur

#### `--id_salt`

Sel GraphQl

- Requiert une valeur

#### `--checkout-async`

Activer le traitement asynchrone des commandes ? 1 - Oui, 0 - Non

- Requiert une valeur

#### `--config-async`

Activer l’enregistrement de la configuration d’administration asynchrone ? 1 - Oui, 0 - Non

- Requiert une valeur

#### `--amqp-host`

Hôte de serveur AMP

- Valeur par défaut : «
- Requiert une valeur

#### `--amqp-port`

Port du serveur AMP

- Faire défaut: `5672`
- Nécessite une valeur

#### `--amqp-user`

Nom d’utilisateur du serveur Amqp

- Valeur par défaut : &#39;&#39;
- Nécessite une valeur

#### `--amqp-password`

Mot de passe du serveur Amqp

- Valeur par défaut : &#39;&#39;
- Nécessite une valeur

#### `--amqp-virtualhost`

Amqp virtualhost

- Faire défaut: `/`
- Nécessite une valeur

#### `--amqp-ssl`

Amap SSL

- Valeur par défaut : &#39;&#39;
- Nécessite une valeur

#### `--amqp-ssl-options`

Options SSL Amqp (JSON)

- Valeur par défaut : &#39;&#39;
- Nécessite une valeur

#### `--consumers-wait-for-messages`

Les consommateurs doivent-ils attendre un message de la file d’attente ? 1 - Oui, 0 - Non

- Nécessite une valeur

#### `--queue-default-connection`

Connexion par défaut aux files d’attente de messages. Peut être &#39;db&#39;, &#39;amqp&#39; ou un système de file d’attente personnalisé. Le système de file d’attente doit être installé et configuré, sinon les messages ne seront pas traités correctement.

- Nécessite une valeur

#### `--deferred-total-calculating`

Activer le calcul du total différé ? 1 - Oui, 0 - Non

- Requiert une valeur

#### `--key`

Clé de chiffrement

- Requiert une valeur

#### `--db-host`

Hôte du serveur de base de données

- Requiert une valeur

#### `--db-name`

Nom de la base

- Requiert une valeur

#### `--db-user`

Nom d&#39;utilisateur du serveur de base de données

- Requiert une valeur

#### `--db-engine`

Moteur de serveur de base de données

- Requiert une valeur

#### `--db-password`

Mot de passe du serveur de base de données

- Requiert une valeur

#### `--db-prefix`

Préfixe de table de base de données

- Nécessite une valeur

#### `--db-model`

Type de base

- Requiert une valeur

#### `--db-init-statements`

Ensemble initial de commandes de la base de données

- Requiert une valeur

#### `--skip-db-validation`, `-s`

Si spécifié, la validation de la connexion à la base de données est ignorée

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--http-cache-hosts`

Hôtes de cache http

- Requiert une valeur

#### `--db-ssl-key`

Chemin complet du fichier de clé cliente afin d&#39;établir la connexion à la base de données via SSL

- Valeur par défaut : &#39;&#39;
- Requiert une valeur

#### `--db-ssl-cert`

Chemin complet du fichier de certificat client afin d’établir une connexion de base de données via SSL

- Valeur par défaut : &#39;&#39;
- Nécessite une valeur

#### `--db-ssl-ca`

Chemin complet du fichier de certificat du serveur afin d’établir la connexion de base de données via SSL

- Valeur par défaut : «
- Requiert une valeur

#### `--db-ssl-verify`

Vérifier la certification du serveur

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--session-save`

Gestionnaire de sauvegarde de session

- Nécessite une valeur

#### `--session-save-redis-host`

Nom d’hôte complet, adresse IP ou chemin absolu si vous utilisez des sockets UNIX

- Requiert une valeur

#### `--session-save-redis-port`

Port d’écoute du serveur Redis

- Requiert une valeur

#### `--session-save-redis-password`

Mot de passe du serveur Redis

- Requiert une valeur

#### `--session-save-redis-timeout`

Délai d’expiration de connexion, en secondes

- Nécessite une valeur

#### `--session-save-redis-retries`

Nouvelles tentatives de connexion Redis.

- Nécessite une valeur

#### `--session-save-redis-persistent-id`

Chaîne unique permettant l’activation des connexions persistantes

- Nécessite une valeur

#### `--session-save-redis-db`

Numéro de la base de données Redis

- Requiert une valeur

#### `--session-save-redis-compression-threshold`

Seuil de compression Redis

- Requiert une valeur

#### `--session-save-redis-compression-lib`

Bibliothèque de compression Redis. Valeurs : gzip (par défaut), lzf, lz4, snappy

- Nécessite une valeur

#### `--session-save-redis-log-level`

Niveau de journalisation Redis. Valeurs : 0 (le moins verbeux) à 7 (le plus verbeux)

- Requiert une valeur

#### `--session-save-redis-max-concurrency`

Nombre maximum de processus pouvant attendre un verrouillage sur une session

- Requiert une valeur

#### `--session-save-redis-break-after-frontend`

Nombre de secondes à attendre avant d’essayer d’interrompre un verrouillage pour une session frontale

- Requiert une valeur

#### `--session-save-redis-break-after-adminhtml`

Nombre de secondes à attendre avant de tenter de rompre un verrou pour une session d’administrateur

- Requiert une valeur

#### `--session-save-redis-first-lifetime`

Durée de vie, en secondes, de la session pour les non-robots lors de la première écriture (utilisez 0 pour désactiver)

- Requiert une valeur

#### `--session-save-redis-bot-first-lifetime`

Durée de vie, en secondes, de la session des robots lors de la première écriture (utilisez 0 pour désactiver).

- Requiert une valeur

#### `--session-save-redis-bot-lifetime`

Durée de vie de la session des robots lors des écritures suivantes (utilisez 0 pour désactiver)

- Nécessite une valeur

#### `--session-save-redis-disable-locking`

Redis désactive le verrouillage. Valeurs : false (par défaut), true

- Nécessite une valeur

#### `--session-save-redis-min-lifetime`

Durée de vie min. de la session Redis, en secondes

- Requiert une valeur

#### `--session-save-redis-max-lifetime`

Durée de vie maximale de la session, en secondes

- Requiert une valeur

#### `--session-save-redis-sentinel-master`

maître Redis Sentinel

- Requiert une valeur

#### `--session-save-redis-sentinel-servers`

Serveurs Redis Sentinel, séparés par des virgules

- Requiert une valeur

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel, maître de vérification. Valeurs : false (par défaut), true

- Requiert une valeur

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel retente la connexion.

- Requiert une valeur

#### `--cache-backend`

Gestionnaire de cache par défaut

- Requiert une valeur

#### `--cache-backend-redis-server`

Serveur Redis

- Requiert une valeur

#### `--cache-backend-redis-db`

Numéro de base de données pour le cache

- Requiert une valeur

#### `--cache-backend-redis-port`

Port d’écoute du serveur Redis

- Requiert une valeur

#### `--cache-backend-redis-password`

Mot de passe du serveur Redis

- Requiert une valeur

#### `--cache-backend-redis-compress-data`

Définissez cette valeur sur 0 pour désactiver la compression (1 par défaut, activé)

- Requiert une valeur

#### `--cache-backend-redis-compression-lib`

Bibliothèque de compression à utiliser [snappy,lzf,l4z,zstd,gzip] (laisser vide pour déterminer automatiquement)

- Requiert une valeur

#### `--cache-backend-redis-use-lua`

Définissez sur 1 pour activer lua (0 par défaut, désactivé).

- Requiert une valeur

#### `--cache-backend-redis-use-lua-on-gc`

Définissez cette valeur sur 0 pour désactiver lua sur le nettoyage (la valeur par défaut est 1, activé)

- Requiert une valeur

#### `--cache-id-prefix`

Préfixe d’ID pour les clés du cache

- Requiert une valeur

#### `--allow-parallel-generation`

Autoriser la génération du cache de manière non bloquante

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--page-cache`

Gestionnaire de cache par défaut

- Requiert une valeur

#### `--page-cache-redis-server`

Serveur Redis

- Requiert une valeur

#### `--page-cache-redis-db`

Numéro de base de données pour le cache

- Requiert une valeur

#### `--page-cache-redis-port`

Port d’écoute du serveur Redis

- Requiert une valeur

#### `--page-cache-redis-password`

Mot de passe du serveur Redis

- Requiert une valeur

#### `--page-cache-redis-compress-data`

Définissez cette valeur sur 1 pour compresser le cache de page complet (utilisez 0 pour le désactiver).

- Requiert une valeur

#### `--page-cache-redis-compression-lib`

Bibliothèque de compression à utiliser [snappy,lzf,l4z,zstd,gzip] (laisser vide pour déterminer automatiquement)

- Requiert une valeur

#### `--page-cache-id-prefix`

Préfixe d’ID pour les clés du cache

- Requiert une valeur

#### `--lock-provider`

Verrouiller le nom du fournisseur

- Requiert une valeur

#### `--lock-db-prefix`

Préfixe de verrouillage spécifique à l’installation pour éviter les conflits de verrouillage

- Nécessite une valeur

#### `--lock-zookeeper-host`

Hôte et port pour la connexion au cluster Zookeeper. Par exemple : 127.0.0.1:2181

- Requiert une valeur

#### `--lock-zookeeper-path`

Chemin où Zookeeper enregistre les verrous. Le chemin par défaut est : /magento/locks

- Requiert une valeur

#### `--lock-file-path`

Chemin d’accès où les verrous de fichier seront enregistrés.

- Requiert une valeur

#### `--document-root-is-pub`

Indicateur à afficher : Pub est à la racine, peut être true ou false uniquement

- Requiert une valeur

#### `--backpressure-logger`

Dispositif de manutention d&#39;enregistreur de contre-pression

- Requiert une valeur

#### `--backpressure-logger-redis-server`

Serveur Redis

- Requiert une valeur

#### `--backpressure-logger-redis-port`

Port d’écoute du serveur Redis

- Requiert une valeur

#### `--backpressure-logger-redis-timeout`

Délai d’expiration du serveur Redis

- Requiert une valeur

#### `--backpressure-logger-redis-persistent`

Redis persistant

- Requiert une valeur

#### `--backpressure-logger-redis-db`

Numéro de la BD Redis

- Requiert une valeur

#### `--backpressure-logger-redis-password`

Mot de passe du serveur Redis

- Requiert une valeur

#### `--backpressure-logger-redis-user`

Utilisateur du serveur Redis

- Requiert une valeur

#### `--backpressure-logger-id-prefix`

Préfixe d’ID pour les clés

- Requiert une valeur

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `setup:db-data:upgrade`

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installe et met à niveau les données de la base de données

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `setup:db-declaration:generate-patch`

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

Générez un correctif et placez-le dans un dossier spécifique.

### Arguments

#### `module`

Nom du module

- Obligatoire


#### `patch`

Nom du correctif

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--revertable`

Vérifiez si le correctif est réversible ou non.

- Valeur par défaut : `false`
- Accepte une valeur

#### `--type`

Découvrez quel type de correctif doit être généré. Valeurs disponibles : `data`, `schema`.

- Faire défaut: `data`
- Accepte une valeur


## `setup:db-declaration:generate-whitelist`

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

Générer la liste blanche des tables et colonnes qui peuvent être modifiées par le programme d’installation de la déclaration

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).

#### `--module-name`

Nom du module dans lequel la liste blanche sera générée

- Faire défaut: `all`
- Accepte une valeur


## `setup:db-schema:add-slave`

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Déplacer les tables liées aux devis de retrait vers un serveur de base de données distinct

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--host`

Hôte du serveur de base de données esclave

- Valeur par défaut : `localhost`
- Requiert une valeur

#### `--dbname`

Nom de la base de données esclave

- Nécessite une valeur

#### `--username`

Nom d’utilisateur de la base de données esclave

- Valeur par défaut : `root`
- Nécessite une valeur

#### `--password`

Mot de passe de l&#39;utilisateur de la base de données esclave

- Accepte une valeur

#### `--connection`

Nom de la connexion esclave

- Faire défaut: `default`
- Accepte une valeur

#### `--resource`

Nom de la ressource esclave

- Faire défaut: `default`
- Accepte une valeur

#### `--maxAllowedLag`

Décalage maximal autorisé Connexion esclave (en secondes)

- Valeur par défaut : &#39;&#39;
- Accepte une valeur

#### `--magento-init-params`

Ajouter à n’importe quelle commande pour personnaliser Magento paramètres d’initialisation Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur


## `setup:db-schema:split-quote`

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Déplacez les tableaux associés aux devis de paiement vers un serveur de base de données distinct. Obsolète depuis 2.4.2 et sera supprimé

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).

#### `--host`

Extraire l’hôte du serveur de base de données

- Nécessite une valeur

#### `--dbname`

Nom de la base de données de sortie

- Nécessite une valeur

#### `--username`

Nom d’utilisateur de la base de données de sortie

- Nécessite une valeur

#### `--password`

Mot de passe d’utilisateur de la base de données de sortie

- Accepte une valeur

#### `--connection`

Nom de la connexion au paiement

- Faire défaut: `checkout`
- Accepte une valeur

#### `--resource`

Nom de la ressource de retrait

- Faire défaut: `checkout`
- Accepte une valeur

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `setup:db-schema:split-sales`

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Déplacez les tables liées aux ventes vers un serveur de base de données distinct. Obsolète depuis la version 2.4.2 et sera supprimé

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--host`

Hôte du serveur de base de données Sales

- Requiert une valeur

#### `--dbname`

Nom de la base de données des ventes

- Requiert une valeur

#### `--username`

Nom d’utilisateur de la base de données des ventes

- Nécessite une valeur

#### `--password`

Utilisateur de base de données des ventes passowrd

- Accepte une valeur

#### `--connection`

Nom de la connexion commerciale

- Faire défaut: `sales`
- Accepte une valeur

#### `--resource`

Nom de la ressource commerciale

- Faire défaut: `sales`
- Accepte une valeur

#### `--magento-init-params`

Ajouter à n’importe quelle commande pour personnaliser Magento paramètres d’initialisation Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `setup:db-schema:upgrade`

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installe et met à niveau le schéma de la base de données

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--convert-old-scripts`

Permet de convertir d’anciens scripts (InstallSchema, UpgradeSchema) au format db_schema.xml

- Valeur par défaut : `false`
- Accepte une valeur

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `setup:db:status`

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Vérifie si le schéma de base de données ou les données doivent être mis à niveau

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `setup:di:compile`

```bash
bin/magento setup:di:compile
```

Génère la configuration d’ID et toutes les classes manquantes qui peuvent être générées automatiquement

### Options

Pour les options globales, voir [Options globales](#global-options).


## `setup:install`

```bash
bin/magento setup:install [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installe l’application Magento

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--remote-storage-driver`

Pilote de stockage distant

- Requiert une valeur

#### `--remote-storage-prefix`

Préfixe de stockage à distance

- Valeur par défaut : &#39;&#39;
- Nécessite une valeur

#### `--remote-storage-endpoint`

Point de terminaison de stockage distant

- Nécessite une valeur

#### `--remote-storage-bucket`

Compartiment de stockage distant

- Requiert une valeur

#### `--remote-storage-region`

Région de stockage distante

- Requiert une valeur

#### `--remote-storage-key`

Clé d’accès au stockage distant

- Valeur par défaut : «
- Requiert une valeur

#### `--remote-storage-secret`

Clé secrète de stockage distant

- Valeur par défaut : «
- Requiert une valeur

#### `--remote-storage-path-style`

Style du chemin de stockage distant

- Valeur par défaut : `0`
- Requiert une valeur

#### `--backend-frontname`

Nom du front-end (sera généré automatiquement s’il est manquant)

- Requiert une valeur

#### `--enable-debug-logging`

Activer la journalisation du débogage

- Requiert une valeur

#### `--enable-syslog-logging`

Activer la journalisation syslog

- Requiert une valeur

#### `--id_salt`

Sel GraphQl

- Requiert une valeur

#### `--checkout-async`

Activer le traitement asynchrone des commandes ? 1 - Oui, 0 - Non

- Requiert une valeur

#### `--config-async`

Activer l’enregistrement de la configuration d’administration asynchrone ? 1 - Oui, 0 - Non

- Requiert une valeur

#### `--amqp-host`

Hôte de serveur AMP

- Valeur par défaut : «
- Requiert une valeur

#### `--amqp-port`

Port du serveur AMP

- Valeur par défaut : `5672`
- Requiert une valeur

#### `--amqp-user`

Nom d’utilisateur du serveur AMP

- Valeur par défaut : «
- Requiert une valeur

#### `--amqp-password`

Mot de passe du serveur AMP

- Valeur par défaut : «
- Requiert une valeur

#### `--amqp-virtualhost`

Amqp virtualhost

- Valeur par défaut : `/`
- Requiert une valeur

#### `--amqp-ssl`

Amap SSL

- Valeur par défaut : «
- Requiert une valeur

#### `--amqp-ssl-options`

Options SSL AMP (JSON)

- Valeur par défaut : «
- Requiert une valeur

#### `--consumers-wait-for-messages`

Les consommateurs doivent-ils attendre un message de la file d’attente ? 1 - Oui, 0 - Non

- Requiert une valeur

#### `--queue-default-connection`

Connexion par défaut aux files d&#39;attente des messages. Peut être &#39;db&#39;, &#39;amqp&#39; ou un système de file d&#39;attente personnalisé. Le système de file d&#39;attente doit être installé et configuré, sinon les messages ne seront pas traités correctement.

- Requiert une valeur

#### `--deferred-total-calculating`

Activer le calcul du total différé ? 1 - Oui, 0 - Non

- Requiert une valeur

#### `--key`

Clé de chiffrement

- Requiert une valeur

#### `--db-host`

Hôte du serveur de base de données

- Requiert une valeur

#### `--db-name`

nom de la base de données ;

- Requiert une valeur

#### `--db-user`

Nom d&#39;utilisateur du serveur de base de données

- Requiert une valeur

#### `--db-engine`

Moteur de serveur de base de données

- Requiert une valeur

#### `--db-password`

Mot de passe du serveur de base de données

- Requiert une valeur

#### `--db-prefix`

Préfixe de table de base de données

- Nécessite une valeur

#### `--db-model`

Type de base

- Requiert une valeur

#### `--db-init-statements`

Ensemble initial de commandes de la base de données

- Requiert une valeur

#### `--skip-db-validation`, `-s`

Si spécifié, la validation de la connexion à la base de données est ignorée

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--http-cache-hosts`

Hôtes de cache http

- Requiert une valeur

#### `--db-ssl-key`

Chemin complet du fichier de clé cliente afin d&#39;établir la connexion à la base de données via SSL

- Valeur par défaut : «
- Requiert une valeur

#### `--db-ssl-cert`

Chemin complet du fichier de certificat client pour établir la connexion à la base de données via SSL

- Valeur par défaut : «
- Requiert une valeur

#### `--db-ssl-ca`

Chemin complet du fichier de certificat du serveur pour établir la connexion à la base de données via SSL

- Valeur par défaut : «
- Requiert une valeur

#### `--db-ssl-verify`

Vérifier la certification du serveur

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--session-save`

Gestionnaire d’enregistrement de session

- Requiert une valeur

#### `--session-save-redis-host`

Nom d’hôte complet, adresse IP ou chemin absolu si vous utilisez des sockets UNIX

- Requiert une valeur

#### `--session-save-redis-port`

Port d’écoute du serveur Redis

- Requiert une valeur

#### `--session-save-redis-password`

Mot de passe du serveur Redis

- Nécessite une valeur

#### `--session-save-redis-timeout`

Délai d’expiration de connexion, en secondes

- Requiert une valeur

#### `--session-save-redis-retries`

Redis les reprises de connexion.

- Requiert une valeur

#### `--session-save-redis-persistent-id`

Chaîne unique permettant l’activation des connexions persistantes

- Nécessite une valeur

#### `--session-save-redis-db`

Numéro de la base de données Redis

- Nécessite une valeur

#### `--session-save-redis-compression-threshold`

Seuil de compression Redis

- Nécessite une valeur

#### `--session-save-redis-compression-lib`

Bibliothèque de compression Redis. Valeurs : gzip (par défaut), lzf, lz4, snappy

- Nécessite une valeur

#### `--session-save-redis-log-level`

Niveau de journalisation Redis. Valeurs : 0 (le moins verbeux) à 7 (le plus verbeux)

- Nécessite une valeur

#### `--session-save-redis-max-concurrency`

Nombre maximal de processus pouvant attendre un verrouillage sur une session

- Nécessite une valeur

#### `--session-save-redis-break-after-frontend`

Nombre de secondes à attendre avant d’essayer de rompre un verrou pour une session front-end

- Nécessite une valeur

#### `--session-save-redis-break-after-adminhtml`

Nombre de secondes à attendre avant d’essayer de briser un verrou pour une session d’administration

- Nécessite une valeur

#### `--session-save-redis-first-lifetime`

Durée de vie, en secondes, de la session pour les non-bots à la première écriture (utilisez 0 pour désactiver)

- Nécessite une valeur

#### `--session-save-redis-bot-first-lifetime`

Durée de vie, en secondes, de la session pour les robots lors de la première écriture (utilisez 0 pour désactiver)

- Nécessite une valeur

#### `--session-save-redis-bot-lifetime`

Durée de vie de la session des robots lors des écritures suivantes (utilisez 0 pour désactiver)

- Nécessite une valeur

#### `--session-save-redis-disable-locking`

Redis désactive le verrouillage. Valeurs : false (par défaut), true

- Requiert une valeur

#### `--session-save-redis-min-lifetime`

Durée de vie min. de la session Redis, en secondes

- Nécessite une valeur

#### `--session-save-redis-max-lifetime`

Durée de vie max. de la session Redis, en secondes

- Nécessite une valeur

#### `--session-save-redis-sentinel-master`

Maître Redis Sentinel

- Requiert une valeur

#### `--session-save-redis-sentinel-servers`

Serveurs Redis Sentinel, séparés par des virgules

- Requiert une valeur

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel, maître de vérification. Valeurs : false (par défaut), true

- Requiert une valeur

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel retente la connexion.

- Requiert une valeur

#### `--cache-backend`

Gestionnaire de cache par défaut

- Requiert une valeur

#### `--cache-backend-redis-server`

Serveur Redis

- Nécessite une valeur

#### `--cache-backend-redis-db`

Numéro de base de données du cache

- Nécessite une valeur

#### `--cache-backend-redis-port`

Port d’écoute du serveur Redis

- Nécessite une valeur

#### `--cache-backend-redis-password`

Mot de passe du serveur Redis

- Nécessite une valeur

#### `--cache-backend-redis-compress-data`

Définissez la valeur 0 pour désactiver la compression (1 par défaut, activé)

- Nécessite une valeur

#### `--cache-backend-redis-compression-lib`

Bibliothèque de compression à utiliser [snappy,lzf,l4z,zstd,gzip] (laisser vide pour déterminer automatiquement)

- Requiert une valeur

#### `--cache-backend-redis-use-lua`

Définissez sur 1 pour activer lua (0 par défaut, désactivé).

- Requiert une valeur

#### `--cache-backend-redis-use-lua-on-gc`

Définissez cette valeur sur 0 pour désactiver lua sur le nettoyage (la valeur par défaut est 1, activé)

- Requiert une valeur

#### `--cache-id-prefix`

Préfixe d’ID pour les clés du cache

- Requiert une valeur

#### `--allow-parallel-generation`

Autoriser la génération du cache de manière non bloquante

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--page-cache`

Gestionnaire de cache par défaut

- Nécessite une valeur

#### `--page-cache-redis-server`

Serveur Redis

- Requiert une valeur

#### `--page-cache-redis-db`

Numéro de base de données pour le cache

- Requiert une valeur

#### `--page-cache-redis-port`

Port d’écoute du serveur Redis

- Requiert une valeur

#### `--page-cache-redis-password`

Mot de passe du serveur Redis

- Requiert une valeur

#### `--page-cache-redis-compress-data`

Définissez cette valeur sur 1 pour compresser le cache de page complet (utilisez 0 pour le désactiver).

- Requiert une valeur

#### `--page-cache-redis-compression-lib`

Bibliothèque de compression à utiliser [snappy,lzf,l4z,zstd,gzip] (laisser vide pour déterminer automatiquement)

- Nécessite une valeur

#### `--page-cache-id-prefix`

Préfixe d’ID pour les clés du cache

- Requiert une valeur

#### `--lock-provider`

Verrouiller le nom du fournisseur

- Requiert une valeur

#### `--lock-db-prefix`

Préfixe de verrouillage spécifique à l’installation pour éviter les conflits de verrouillage

- Requiert une valeur

#### `--lock-zookeeper-host`

Hôte et port pour la connexion au cluster Zookeeper. Par exemple : 127.0.0.1:2181

- Requiert une valeur

#### `--lock-zookeeper-path`

Chemin où Zookeeper enregistre les verrous. Le chemin par défaut est : /magento/locks

- Requiert une valeur

#### `--lock-file-path`

Chemin d’accès où les verrous de fichier seront enregistrés.

- Requiert une valeur

#### `--document-root-is-pub`

Indicateur à afficher : Pub est à la racine, peut être true ou false uniquement

- Requiert une valeur

#### `--backpressure-logger`

Gestionnaire d’enregistreurs de contre-pression

- Nécessite une valeur

#### `--backpressure-logger-redis-server`

Serveur Redis

- Nécessite une valeur

#### `--backpressure-logger-redis-port`

Port d’écoute du serveur Redis

- Nécessite une valeur

#### `--backpressure-logger-redis-timeout`

Expiration du serveur Redis

- Nécessite une valeur

#### `--backpressure-logger-redis-persistent`

Redis persistant

- Nécessite une valeur

#### `--backpressure-logger-redis-db`

Numéro de base de données Redis

- Requiert une valeur

#### `--backpressure-logger-redis-password`

Mot de passe du serveur Redis

- Requiert une valeur

#### `--backpressure-logger-redis-user`

Utilisateur du serveur Redis

- Nécessite une valeur

#### `--backpressure-logger-id-prefix`

Préfixe d’identification pour les clés

- Requiert une valeur

#### `--base-url`

URL vers laquelle le magasin est censé être disponible. Obsolète, utilisez config:set avec le chemin web/unsecure/base_url

- Requiert une valeur

#### `--language`

Code de langue par défaut. Obsolète, utilisez config:set avec le chemin general/locale/code

- Requiert une valeur

#### `--timezone`

Code de fuseau horaire par défaut. Obsolète, utilisez config:set avec le chemin general/locale/timezone

- Requiert une valeur

#### `--currency`

Code de devise par défaut. Obsolète, utilisez config:set avec le chemin currency/options/base, currency/options/default et currency/options/allow .

- Requiert une valeur

#### `--use-rewrites`

Utilisez les réécritures. Obsolète, utilisez config:set avec le chemin web/seo/use_rewrites

- Nécessite une valeur

#### `--use-secure`

Utilisez des URL sécurisées. Activez cette option uniquement si SSL est disponible. Obsolète, utilisez config :set avec le chemin web/secure/use_in_frontend.

- Nécessite une valeur

#### `--base-url-secure`

URL de base de la connexion SSL. Obsolète, utilisez config:set avec le chemin web/secure/base_url

- Requiert une valeur

#### `--use-secure-admin`

Exécutez l’interface d’administration avec SSL. Obsolète, utilisez config:set avec le chemin web/secure/use_in_adminhtml

- Requiert une valeur

#### `--admin-use-security-key`

Indique s’il faut utiliser une fonction de « clé de sécurité » dans les formulaires et les URL d’administration Magento. Obsolète, utilisez config:set avec le chemin admin/security/use_form_key

- Requiert une valeur

#### `--admin-user`

Utilisateur administrateur

- Accepte une valeur

#### `--admin-password`

Mot de passe administrateur

- Accepte une valeur

#### `--admin-email`

Adresse e-mail de l&#39;administrateur

- Accepte une valeur

#### `--admin-firstname`

Prénom de l’administrateur

- Accepte une valeur

#### `--admin-lastname`

Nom de l’administrateur

- Accepte une valeur

#### `--search-engine`

Moteur de recherche. Valeurs : elasticsearch8, opensearch

- Requiert une valeur

#### `--elasticsearch-host`

Hôte du serveur Elasticsearch.

- Requiert une valeur

#### `--elasticsearch-port`

Port du serveur Elasticsearch.

- Requiert une valeur

#### `--elasticsearch-enable-auth`

Définissez sur 1 pour activer l’authentification. (la valeur par défaut est 0, désactivé)

- Requiert une valeur

#### `--elasticsearch-username`

Nom d’utilisateur Elasticsearch. Applicable uniquement si l’authentification HTTP est activée

- Requiert une valeur

#### `--elasticsearch-password`

Mot de passe Elasticsearch. Applicable uniquement si l’authentification HTTP est activée

- Requiert une valeur

#### `--elasticsearch-index-prefix`

Préfixe d’index Elasticsearch.

- Requiert une valeur

#### `--elasticsearch-timeout`

Timeout du serveur Elasticsearch.

- Requiert une valeur

#### `--opensearch-host`

Hôte du serveur OpenSearch.

- Requiert une valeur

#### `--opensearch-port`

Port du serveur OpenSearch.

- Requiert une valeur

#### `--opensearch-enable-auth`

Définissez sur 1 pour activer l’authentification. (la valeur par défaut est 0, désactivé)

- Requiert une valeur

#### `--opensearch-username`

Nom d’utilisateur OpenSearch. Applicable uniquement si l’authentification HTTP est activée

- Requiert une valeur

#### `--opensearch-password`

Mot de passe OpenSearch. Applicable uniquement si l’authentification HTTP est activée

- Requiert une valeur

#### `--opensearch-index-prefix`

Préfixe d’index OpenSearch.

- Requiert une valeur

#### `--opensearch-timeout`

Timeout du serveur OpenSearch.

- Requiert une valeur

#### `--cleanup-database`

Nettoyage de la base de données avant installation

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--sales-order-increment-prefix`

Préfixe du numéro de commande client

- Requiert une valeur

#### `--use-sample-data`

Utiliser les exemples de données

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--enable-modules`

Liste de noms de modules séparés par des virgules. Cela doit être inclus lors de l’installation. Paramètre magique disponible « all ».

- Accepte une valeur

#### `--disable-modules`

Liste de noms de modules séparés par des virgules. Cela doit être évité pendant l’installation. Paramètre magique disponible « all ».

- Accepte une valeur

#### `--convert-old-scripts`

Permet de convertir d’anciens scripts (InstallSchema, UpgradeSchema) au format db_schema.xml

- Valeur par défaut : `false`
- Accepte une valeur

#### `--interactive`, `-i`

Installation d’Interactive Magento

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--safe-mode`

Installation en toute sécurité de Magento avec des images mémoire sur les opérations destructives, comme la suppression de colonne

- Accepte une valeur

#### `--data-restore`

Restaurer les données supprimées des images mémoire

- Accepte une valeur

#### `--dry-run`

L’installation de Magento sera exécutée en mode d’exécution d’essai

- Valeur par défaut : `false`
- Accepte une valeur

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `setup:performance:generate-fixtures`

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

Génère des briquets

### Arguments

#### `profile`

Chemin d’accès au fichier de configuration du profil

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--skip-reindex`, `-s`

Ignorer la réindexation

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:rollback`

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Restauration de la base de code, du média et de la base de données de l’application Magento

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--code-file`, `-c`

Nom de base du fichier de sauvegarde du code dans var/backups

- Requiert une valeur

#### `--media-file`, `-m`

Nom de base du fichier de sauvegarde multimédia dans var/backups

- Requiert une valeur

#### `--db-file`, `-d`

Nom de base du fichier de sauvegarde de la base de données dans var/backup

- Requiert une valeur

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `setup:static-content:deploy`

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

Déploie des fichiers de vue statiques

### Arguments

#### `languages`

Liste séparée par des espaces de codes de langue ISO-639 pour lesquels générer des fichiers de vue statiques.

- Valeur par défaut : `[]`
- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--force`, `-f`

Déployez des fichiers dans n’importe quel mode.

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--strategy`, `-s`

Déployez des fichiers à l’aide de la stratégie spécifiée.

- Valeur par défaut : `quick`
- Accepte une valeur

#### `--area`, `-a`

Générer des fichiers uniquement pour les zones spécifiées.

- Valeur par défaut : `all`
- Accepte plusieurs valeurs

#### `--exclude-area`

Ne générez pas de fichiers pour les zones spécifiées.

- Valeur par défaut : `none`
- Accepte plusieurs valeurs

#### `--theme`, `-t`

Génère des fichiers d’affichage statique uniquement pour les thèmes spécifiés.

- Faire défaut: `all`
- Accepte plusieurs valeurs

#### `--exclude-theme`

Ne générez pas de fichiers pour les thèmes spécifiés.

- Faire défaut: `none`
- Accepte plusieurs valeurs

#### `--language`, `-l`

Génère des fichiers uniquement pour les langues spécifiées.

- Faire défaut: `all`
- Accepte plusieurs valeurs

#### `--exclude-language`

Ne générez pas de fichiers pour les langues spécifiées.

- Faire défaut: `none`
- Accepte plusieurs valeurs

#### `--jobs`, `-j`

Activez le traitement parallèle à l’aide du nombre de tâches spécifié.

- Faire défaut: `0`
- Accepte une valeur

#### `--max-execution-time`

Durée d’exécution maximale prévue du processus statique de déploiement (en secondes).

- Faire défaut: `900`
- Accepte une valeur

#### `--symlink-locale`

Créez des liens symboliques pour les fichiers de ces paramètres régionaux, qui sont transmis pour le déploiement, mais n’ont aucune personnalisation.

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--content-version`

La version personnalisée du contenu statique peut être utilisée si vous exécutez le déploiement sur plusieurs nœuds pour vous assurer que la version du contenu statique est identique et que la mise en cache fonctionne correctement.

- Nécessite une valeur

#### `--refresh-content-version-only`

L’actualisation de la version du contenu statique uniquement peut être utilisée pour actualiser le contenu statique dans le cache du navigateur et le cache CDN.

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--no-javascript`

Ne déployez pas JavaScript fichiers.

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--no-js-bundle`

Ne déployez pas JavaScript fichiers groupés.

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--no-css`

Ne déployez pas de fichiers CSS.

- Faire défaut: `false`
- N’accepte pas de valeur

#### `--no-less`

Ne déployez pas de fichiers LESS.

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--no-images`

Ne déployez pas d’images.

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--no-fonts`

Ne déployez pas de fichiers de polices.

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--no-html`

Ne déployez pas de fichiers HTML.

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--no-misc`

Ne déployez pas de fichiers d’autres types (.md, .jbf, .csv, etc.).

- Faire défaut: `false`
- N’accepte aucune valeur

#### `--no-html-minify`

Ne réduisez pas les fichiers HTML.

- Faire défaut: `false`
- N’accepte aucune valeur

#### `--no-parent`

Ne compilez pas les thèmes parents. Pris en charge uniquement dans les stratégies rapides et standard.

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:store-config:set`

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installe la configuration du magasin. Obsolète depuis la version 2.2.0. Utilisez plutôt config:set .

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--base-url`

URL vers laquelle le magasin est censé être disponible. Obsolète, utilisez config:set avec le chemin web/unsecure/base_url

- Requiert une valeur

#### `--language`

Code de langue par défaut. Obsolète, utilisez config :set avec le chemin general/locale/code

- Nécessite une valeur

#### `--timezone`

Code de fuseau horaire par défaut. Obsolète, utilisez config :set avec chemin general/locale/timezone

- Nécessite une valeur

#### `--currency`

Code de devise par défaut. Obsolète, utilisez config:set avec le chemin currency/options/base, currency/options/default et currency/options/allow .

- Requiert une valeur

#### `--use-rewrites`

Utilisez les réécritures. Obsolète, utilisez config:set avec le chemin web/seo/use_rewrites

- Requiert une valeur

#### `--use-secure`

Utilisez des URL sécurisées. Activez cette option uniquement si SSL est disponible. Obsolète, utilisez config :set avec le chemin web/secure/use_in_frontend.

- Nécessite une valeur

#### `--base-url-secure`

URL de base de la connexion SSL. Obsolète, utilisez config:set avec le chemin web/secure/base_url

- Requiert une valeur

#### `--use-secure-admin`

Exécutez l’interface d’administration avec SSL. Obsolète, utilisez config:set avec le chemin web/secure/use_in_adminhtml

- Requiert une valeur

#### `--admin-use-security-key`

S’il convient d’utiliser une fonctionnalité de « clé de sécurité » dans Magento URL et les formulaires d’administration. Obsolète, utilisez config :set avec le chemin admin/security/use_form_key

- Nécessite une valeur

#### `--magento-init-params`

Ajouter à n’importe quelle commande pour personnaliser Magento paramètres d’initialisation Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur


## `setup:uninstall`

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

Désinstalle l’application Magento

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `setup:upgrade`

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Met à niveau l’application Magento, les données de la base de données et le schéma

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--keep-generated`

Empêche la suppression des fichiers générés. Nous vous déconseillons d’utiliser cette option, sauf lors du déploiement en production. Pour plus d’informations, consultez votre intégrateur système ou votre administrateur.

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--convert-old-scripts`

Permet de convertir d’anciens scripts (InstallSchema, UpgradeSchema) au format db_schema.xml

- Valeur par défaut : `false`
- Accepte une valeur

#### `--safe-mode`

Installation en toute sécurité de Magento avec des images mémoire sur les opérations destructives, comme la suppression de colonne

- Accepte une valeur

#### `--data-restore`

Restaurer les données supprimées des images mémoire

- Accepte une valeur

#### `--dry-run`

L’installation de Magento sera exécutée en mode d’exécution d’essai

- Valeur par défaut : `false`
- Accepte une valeur

#### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation de Magento Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Requiert une valeur


## `store:list`

```bash
bin/magento store:list
```

Affiche la liste des magasins

### Options

Pour les options globales, voir [Options globales](#global-options).


## `store:website:list`

```bash
bin/magento store:website:list
```

Affiche la liste des sites Web

### Options

Pour les options globales, voir [Options globales](#global-options).


## `support:backup:code`

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

Création d’une sauvegarde de code

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--name`

Nom du vidage

- Accepte une valeur

#### `--output`, `-o`

Chemin de sortie

- Accepte une valeur

#### `--logs`, `-l`

Inclure les journaux

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `support:backup:db`

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

Créer une sauvegarde de base de données

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--name`

Nom du vidage

- Accepte une valeur

#### `--output`, `-o`

Chemin de sortie

- Accepte une valeur

#### `--logs`, `-l`

Inclure les journaux

- Valeur par défaut : `false`
- N’accepte aucune valeur

#### `--ignore-sanitize`, `-i`

Ignorer l’assainissement

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `support:utility:check`

```bash
bin/magento support:utility:check [--hide-paths]
```

Vérifier les utilitaires de sauvegarde requis

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--hide-paths`

Vérifier uniquement les utilitaires de console requis

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `support:utility:paths`

```bash
bin/magento support:utility:paths [-f|--force]
```

Création d’une liste de chemins d’accès aux utilitaires

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--force`, `-f`

Forcer

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `theme:uninstall`

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

Désinstalle le thème

### Arguments

#### `theme`

Chemin du thème. Le chemin d’accès au thème doit être spécifié comme chemin d’accès complet, à savoir zone/fournisseur/nom. Par exemple, frontend/Magento/blank

- Valeur par défaut : `[]`
- Obligatoire

- Tableau

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--backup-code`

Effectuez une sauvegarde du code (sauf fichiers temporaires)

- Faire défaut: `false`
- N’accepte aucune valeur

#### `--clear-static-content`, `-c`

Effacez les fichiers d’affichage statique générés.

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `varnish:vcl:generate`

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

Génère le code VCL de vernis et le répercute sur la ligne de commande

### Options

Pour les options globales, voir [Options globales](#global-options).

#### `--access-list`

Liste d’accès des adresses IP pouvant purger le vernis

- Valeur par défaut : `localhost`
- Requiert une valeur

#### `--backend-host`

Hôte du serveur principal Web

- Valeur par défaut : `localhost`
- Requiert une valeur

#### `--backend-port`

Port du serveur principal web

- Valeur par défaut : `8080`
- Requiert une valeur

#### `--export-version`

Version du fichier Vernis

- Valeur par défaut : `6`
- Requiert une valeur

#### `--grace-period`

Délai de grâce en secondes

- Valeur par défaut : `300`
- Requiert une valeur

#### `--input-file`

Fichier d’entrée à partir duquel générer la liste virtuelle

- Requiert une valeur

#### `--output-file`

Chemin d’accès au fichier pour écrire vcl

- Requiert une valeur


## `webhooks:dev:run`

```bash
bin/magento webhooks:dev:run <name> <payload>
```

Exécute un webhook enregistré à des fins de développement.

### Arguments

#### `name`

Nom du Webhook

- Obligatoire


#### `payload`

La payload webhook au format JSON

- Obligatoire

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `webhooks:generate:module`

```bash
bin/magento webhooks:generate:module
```

Générer des modules externes en fonction des enregistrements webhook

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `webhooks:info`

```bash
bin/magento webhooks:info [--depth [DEPTH]] [--] <webhook-name> [<webhook-type>]
```

Renvoie la payload du webhook spécifié.

### Arguments

#### `webhook-name`

Nom de la méthode Webhook

- Obligatoire


#### `webhook-type`

Type de Webhook (avant, après)

- Valeur par défaut : `before`

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).

#### `--depth`

Nombre de niveaux dans la charge utile webhook à renvoyer

- Faire défaut: `3`
- Accepte une valeur


## `webhooks:list`

```bash
bin/magento webhooks:list
```

Affiche la liste des webhooks souscrits

### Options

Pour connaître les options globales, reportez-vous à la section [Options globales](#global-options).


## `webhooks:list:all`

```bash
bin/magento webhooks:list:all <module_name>
```

Renvoie une liste des noms de méthode webhook pris en charge pour le module spécifié

### Arguments

#### `module_name`

Nom du module

- Obligatoire

### Options

Pour les options globales, voir [Options globales](#global-options).
