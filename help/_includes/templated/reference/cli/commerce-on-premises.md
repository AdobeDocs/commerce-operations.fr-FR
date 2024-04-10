---
source-git-commit: 755ea50a75924cc16f690ff888367abd305565e9
workflow-type: tm+mt
source-wordcount: '21455'
ht-degree: 0%

---
# bin/magento (Adobe Commerce on-premise)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->

**Version**: 2.4.7

Cette référence contient 141 commandes disponibles via le `bin/magento` outil de ligne de commande.
La liste initiale est générée automatiquement à l’aide de l’ `bin/magento list` dans Adobe Commerce.
Utiliser le [Ajout de commandes d’interface de ligne de commande](https://developer.adobe.com/commerce/php/development/cli-commands/) guide d’ajout d’une commande d’interface de ligne de commande personnalisée.

>[!NOTE]
>
>Vous pouvez appeler `bin/magento` Commandes de l’interface de ligne de commande utilisant des raccourcis au lieu du nom de commande complet. Par exemple, vous pouvez appeler `bin/magento setup:upgrade` utilisation de `bin/magento s:up`, `bin/magento s:upg`. Voir [syntaxe de raccourci](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) pour comprendre comment utiliser des raccourcis avec n’importe quelle commande d’interface de ligne de commande.

>[!NOTE]
>
>Cette référence est générée à partir de la base de code de l’application. Pour modifier le contenu, vous pouvez mettre à jour le code source pour l’implémentation de commande correspondante dans le [base de code](https://github.com/magento) Référencez et envoyez vos modifications pour révision. Une autre méthode consiste à _Donnez-nous votre avis_ (recherchez le lien en haut à droite). Pour les directives de contribution, voir [Cotisations](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

Commande interne pour fournir des suggestions d&#39;achèvement du shell

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

### `--shell`, `-s`

Le type de coque (« bash », « fish », « zsh »)

- Nécessite une valeur

### `--input`, `-i`

Tableau de jetons d’entrée (par exemple COMP_WORDS ou argv)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--current`, `-c`

Index du tableau « input » dans lequel se trouve le curseur (par exemple COMP_CWORD)

- Nécessite une valeur

### `--api-version`, `-a`

Version API du script d’achèvement

- Nécessite une valeur

### `--symfony`, `-S`

obsolète

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `completion`

Vider le script de fin du shell

```bash
bin/magento completion [--debug] [--] [<shell>]
```


### `shell`

Le type de shell (par exemple « bash »), la valeur de la variable d&#39;environnement « $SHELL » seront utilisés si cela n&#39;est pas indiqué


### `--debug`

Effectuer un suivi du journal de débogage d’achèvement

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `help`

Affichage de l’aide d’une commande

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

Nom de la commande

- Valeur par défaut : `help`


### `--format`

Le format de sortie (txt, xml, json ou md)

- Valeur par défaut : `txt`
- Nécessite une valeur

### `--raw`

Pour générer l’aide de la commande brute

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `list`

Commandes de liste

```bash
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```


### `namespace`

Nom de l’espace de noms


### `--raw`

Pour générer la liste de commandes brute

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--format`

Le format de sortie (txt, xml, json ou md)

- Valeur par défaut : `txt`
- Nécessite une valeur

### `--short`

Pour ignorer la description des arguments des commandes

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `admin:adobe-ims:disable`

Désactiver le module Adobe IMS

```bash
bin/magento admin:adobe-ims:disable
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `admin:adobe-ims:enable`

Activez le module Adobe IMS.

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

### `--organization-id`, `-o`

Définissez l’ID d’organisation pour la configuration Adobe IMS. Obligatoire lors de l’activation du module

- Accepte une valeur

### `--client-id`, `-c`

Définissez l’identifiant client pour la configuration Adobe IMS. Obligatoire lors de l’activation du module

- Accepte une valeur

### `--client-secret`, `-s`

Définissez le secret client pour la configuration Adobe IMS. Obligatoire lors de l’activation du module

- Accepte une valeur

### `--2fa`, `-t`

Vérifiez si 2FA est activé pour l’organisation dans Adobe Admin Console. Obligatoire lors de l’activation du module

- Accepte une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `admin:adobe-ims:info`

Informations de configuration du module Adobe IMS

```bash
bin/magento admin:adobe-ims:info
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `admin:adobe-ims:status`

Statut du module Adobe IMS

```bash
bin/magento admin:adobe-ims:status
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `admin:user:create`

Crée un administrateur

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--admin-user`

(Obligatoire) Utilisateur administrateur

- Nécessite une valeur

### `--admin-password`

(Obligatoire) Mot de passe administrateur

- Nécessite une valeur

### `--admin-email`

(Obligatoire) Adresse électronique de l’administrateur

- Nécessite une valeur

### `--admin-firstname`

(Obligatoire) Prénom de l’administrateur

- Nécessite une valeur

### `--admin-lastname`

(Obligatoire) Nom de l’administrateur

- Nécessite une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `admin:user:unlock`

Déverrouiller le compte administrateur

```bash
bin/magento admin:user:unlock <username>
```


### `username`

Nom d’utilisateur administrateur à déverrouiller

- Obligatoire

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `app:config:dump`

Créer un vidage de l’application

```bash
bin/magento app:config:dump [<config-types>...]
```


### `config-types`

Liste séparée par des espaces des types de configuration ou omettez de tout vider [étendues, système, thèmes, i18n]

- Valeur par défaut : `[]`

- Tableau

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `app:config:import`

Importer les données des fichiers de configuration partagés vers le stockage de données approprié

```bash
bin/magento app:config:import
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `app:config:status`

Vérifie si la propagation de la configuration nécessite une mise à jour

```bash
bin/magento app:config:status
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `braintree:migrate`

Migration des cartes stockées depuis une base de données Magento 1

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

### `--host`

Nom d’hôte/adresse IP. Port facultatif

- Nécessite une valeur

### `--dbname`

Nom de la base

- Nécessite une valeur

### `--username`

Nom d&#39;utilisateur de la base de données. Doit avoir un accès en lecture

- Nécessite une valeur

### `--password`

Mot de passe

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `cache:clean`

Nettoie type(s) de cache

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Liste séparée par des espaces des types de cache ou omettre de l’appliquer à tous les types de cache.

- Valeur par défaut : `[]`

- Tableau

### `--bootstrap`

ajouter ou remplacer des paramètres du bootstrap

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `cache:disable`

Désactive le ou les types de cache

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Liste séparée par des espaces des types de cache ou omettre de l’appliquer à tous les types de cache.

- Valeur par défaut : `[]`

- Tableau

### `--bootstrap`

ajouter ou remplacer des paramètres du bootstrap

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `cache:enable`

Active le ou les types de cache

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Liste séparée par des espaces des types de cache ou omettre de l’appliquer à tous les types de cache.

- Valeur par défaut : `[]`

- Tableau

### `--bootstrap`

ajouter ou remplacer des paramètres du bootstrap

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `cache:flush`

Vidange le stockage du cache utilisé par le ou les types de cache

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Liste séparée par des espaces des types de cache ou omettre de l’appliquer à tous les types de cache.

- Valeur par défaut : `[]`

- Tableau

### `--bootstrap`

ajouter ou remplacer des paramètres du bootstrap

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `cache:status`

Vérifie l’état du cache

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

### `--bootstrap`

ajouter ou remplacer des paramètres du bootstrap

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `catalog:images:resize`

Crée des images de produit redimensionnées.

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

### `--async`, `-a`

Redimensionnement d’une image en mode asynchrone

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--skip_hidden_images`

Ne pas traiter les images marquées comme masquées dans la page produit

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `catalog:product:attributes:cleanup`

Supprime les attributs de produit inutilisés.

```bash
bin/magento catalog:product:attributes:cleanup
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `cms:wysiwyg:restrict`

Définir s’il faut appliquer la validation du contenu du HTML utilisateur ou afficher un avertissement à la place

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```


### `restrict`

o\n

- Obligatoire

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `config:sensitive:set`

Définir des valeurs de configuration sensibles

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```


### `path`

Chemin de configuration par exemple group/section/field_name


### `value`

Valeur de configuration


### `--interactive`, `-i`

Activation du mode interactif pour définir toutes les variables sensibles

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--scope`

Portée de la configuration, si non définie, utiliser &#39;default&#39;

- Valeur par défaut : `default`
- Accepte une valeur

### `--scope-code`

Code d’étendue pour la configuration, chaîne vide par défaut

- Valeur par défaut : «
- Accepte une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `config:set`

Modifier la configuration du système

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```


### `path`

Chemin de configuration au format section/group/field_name

- Obligatoire

### `value`

Valeur de configuration

- Obligatoire

### `--scope`

Portée de la configuration (par défaut, site web ou magasin)

- Valeur par défaut : `default`
- Nécessite une valeur

### `--scope-code`

Code d&#39;étendue (obligatoire uniquement si l&#39;étendue n&#39;est pas &#39;default&#39;)

- Nécessite une valeur

### `--lock-env`, `-e`

Valeur de verrouillage qui empêche toute modification dans l&#39;Admin (sera enregistrée dans app/etc/env.php)

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--lock-config`, `-c`

Verrouiller et partager la valeur avec d&#39;autres installations, empêche toute modification dans l&#39;Admin (sera enregistré dans app/etc/config.php)

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--lock`, `-l`

Obsolète, utilisez plutôt l’option —lock-env .

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `config:show`

Affiche la valeur de configuration pour le chemin donné. Si le chemin n’est pas spécifié, toutes les valeurs enregistrées s’affichent

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```


### `path`

Chemin de configuration ; par exemple, section_id/group_id/field_id


### `--scope`

Portée de la configuration : si elle n’est pas spécifiée, la portée « par défaut » est utilisée

- Valeur par défaut : `default`
- Accepte une valeur

### `--scope-code`

Code d’étendue (obligatoire uniquement si l’étendue n’est pas `default`)

- Valeur par défaut : «
- Accepte une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `cron:install`

Génère et installe crontab pour l’utilisateur actuel

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

### `--force`, `-f`

Forcer les tâches d&#39;installation

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--non-optional`, `-d`

Installer uniquement les tâches non facultatives (par défaut)

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `cron:remove`

Supprime les tâches de crontab

```bash
bin/magento cron:remove
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `cron:run`

Exécute les traitements par planning

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

### `--group`

Exécuter les traitements uniquement à partir du groupe spécifié

- Nécessite une valeur

### `--exclude-group`

Exclure les traitements du groupe spécifié

- Valeur par défaut : `[]`
- Accepte plusieurs valeurs

### `--bootstrap`

Ajouter ou remplacer des paramètres du bootstrap

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `customer:hash:upgrade`

Mettre à niveau le hachage du client en fonction du dernier algorithme

```bash
bin/magento customer:hash:upgrade
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `deploy:mode:set`

Définissez le mode d’application.

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```


### `mode`

Mode d’application à définir. Les options disponibles sont « développeur » ou « production »

- Obligatoire

### `--skip-compilation`, `-s`

Ignore l’effacement et la régénération du contenu statique (code généré, CSS prétraité et ressources dans pub/static/)

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `deploy:mode:show`

Affiche le mode d&#39;application actuel.

```bash
bin/magento deploy:mode:show
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `dev:di:info`

Fournit des informations sur la configuration de l’injection de dépendance pour la commande .

```bash
bin/magento dev:di:info <class>
```


### `class`

Nom de la classe

- Obligatoire

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `dev:email:newsletter-compatibility-check`

Analyse les modèles de newsletter pour détecter d’éventuels problèmes de compatibilité d’utilisation des variables

```bash
bin/magento dev:email:newsletter-compatibility-check
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `dev:email:override-compatibility-check`

Analyse les remplacements du modèle d’e-mail à la recherche de problèmes potentiels de compatibilité d’utilisation des variables

```bash
bin/magento dev:email:override-compatibility-check
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `dev:profiler:disable`

Désactivez le profileur.

```bash
bin/magento dev:profiler:disable
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `dev:profiler:enable`

Activez le profileur.

```bash
bin/magento dev:profiler:enable [<type>]
```


### `type`

Type de profileur


### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `dev:query-log:disable`

Désactiver la journalisation des requêtes de base de données

```bash
bin/magento dev:query-log:disable
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `dev:query-log:enable`

Activer la journalisation des requêtes de base de données

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

### `--include-all-queries`

Enregistrer toutes les requêtes. [true\|false]

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

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `dev:source-theme:deploy`

Collecte et publie les fichiers sources pour le thème.

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```


### `file`

Fichiers à pré-traiter (le fichier doit être spécifié sans extension)

- Valeur par défaut : `css/styles-mcss/styles-l`

- Tableau

### `--type`

Type des fichiers sources : [moins]

- Valeur par défaut : `less`
- Nécessite une valeur

### `--locale`

Paramètre régional : [en_US]

- Valeur par défaut : `en_US`
- Nécessite une valeur

### `--area`

Zone : [frontend\|adminhtml]

- Valeur par défaut : `frontend`
- Nécessite une valeur

### `--theme`

Thème : [Fournisseur/thème]

- Valeur par défaut : `Magento/luma`
- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `dev:template-hints:disable`

Désactivez les indications du modèle front-end. Un vidage du cache peut être nécessaire.

```bash
bin/magento dev:template-hints:disable
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `dev:template-hints:enable`

Activez les indications du modèle front-end. Un vidage du cache peut être nécessaire.

```bash
bin/magento dev:template-hints:enable
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `dev:template-hints:status`

Afficher le statut des indications du modèle front-end.

```bash
bin/magento dev:template-hints:status
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `dev:tests:run`

Exécute les tests

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```


### `type`

Type de test à exécuter. Types disponibles : all, unit, integration-all, static, static-all, integrity, inheritance, default

- Valeur par défaut : `default`


### `--arguments`, `-c`

Arguments additionnels pour PHPUnit. Exemple : « -c&#39;—filter=MyTest&#39; » (sans espaces)

- Valeur par défaut : «
- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `dev:urn-catalog:generate`

Génère le catalogue d’URN vers les mappages *.xsd pour que l’IDE mette en surbrillance le format xml.

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```


### `path`

Chemin d’accès au fichier pour générer le catalogue. Pour PhpStorm, utilisez .idea/misc.xml

- Obligatoire

### `--ide`

Format de génération du catalogue. Pris en charge : [phpstorm, vscode]

- Valeur par défaut : `phpstorm`
- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `dev:xml:convert`

Convertit un fichier XML à l’aide de feuilles de style XSL

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```


### `xml-file`

Chemin d&#39;accès au fichier XML à transformer

- Obligatoire

### `processor`

Chemin d’accès à la feuille de style XSL à appliquer au fichier XML

- Obligatoire

### `--overwrite`, `-o`

Remplacer le fichier XML

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `downloadable:domains:add`

Ajouter des domaines à la liste autorisée des domaines téléchargeables

```bash
bin/magento downloadable:domains:add [<domains>...]
```


### `domains`

Nom des domaines

- Valeur par défaut : `[]`

- Tableau

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `downloadable:domains:remove`

Supprimer des domaines de la liste autorisée des domaines téléchargeables

```bash
bin/magento downloadable:domains:remove [<domains>...]
```


### `domains`

Noms de domaine

- Valeur par défaut : `[]`

- Tableau

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `downloadable:domains:show`

Afficher la liste autorisée des domaines téléchargeables

```bash
bin/magento downloadable:domains:show
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `encryption:payment-data:update`

Rechiffre les données de carte de crédit chiffrées avec le dernier chiffrement.

```bash
bin/magento encryption:payment-data:update
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `events:create-event-provider`

Créez un fournisseur d’événements personnalisé dans Événements d’Adobe I/O pour cette instance. Si vous ne spécifiez pas les options de libellé et de description, celles-ci doivent être définies dans le fichier système app/etc/event-types.json.

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]
```


```bash
bin/magento events:provider:create 
```

### `--label`

Un libellé pour définir votre fournisseur personnalisé.

- Accepte une valeur

### `--description`

Description de votre fournisseur.

- Accepte une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `events:generate:module`

Génération du module en fonction de la liste des modules externes

```bash
bin/magento events:generate:module
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `events:info`

Renvoie la payload de l’événement spécifié.

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```


### `event-code`

Code événement

- Obligatoire

### `--depth`

Nombre de niveaux dans la payload d&#39;événement à renvoyer

- Valeur par défaut : `2`
- Accepte une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `events:list`

Affiche la liste des événements avec abonnement

```bash
bin/magento events:list
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `events:list:all`

Renvoie une liste d’événements auxquels vous pouvez vous abonner définis dans le module spécifié

```bash
bin/magento events:list:all <module_name>
```


### `module_name`

Nom du module

- Obligatoire

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `events:metadata:populate`

Crée des métadonnées à l’Adobe I/O de la liste de configuration (configurations XML et d’application).

```bash
bin/magento events:metadata:populate
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `events:provider:info`

Renvoie des détails sur le fournisseur d’événements configuré

```bash
bin/magento events:provider:info
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `events:registrations:list`

Répertorie les enregistrements d’événements dans votre projet App Builder

```bash
bin/magento events:registrations:list
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `events:subscribe`

S’abonne à l’événement

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [-d|--destination DESTINATION] [--] <event-code>
```


### `event-code`

Code événement

- Obligatoire

### `--force`, `-f`

Force l&#39;abonnement à l&#39;événement spécifié, même s&#39;il n&#39;a pas été défini localement.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--fields`

Liste des champs de la payload des données d&#39;événement.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--parent`

Code d’événement parent pour un abonnement à un événement avec des règles.

- Nécessite une valeur

### `--rules`

Liste des règles pour l’abonnement à l’événement, où chaque règle est formatée en tant que « champ\|opérateur\|valeur ».

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--priority`, `-p`

Accélère la transmission de cet événement. Spécifiez cette option pour les événements qui doivent être diffusés immédiatement. Par défaut, les événements sont envoyés par cron une fois par minute.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--destination`, `-d`

Destination de cet événement. Spécifiez cette option pour les événements qui doivent être diffusés à la destination personnalisée.

- Valeur par défaut : `default`
- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `events:sync-events-metadata`

Synchroniser les métadonnées d’événement pour cette instance

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

### `--delete`, `-d`

Suppression des métadonnées d’événement devenues inutiles

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `events:unsubscribe`

Supprime l’abonnement à l’événement fourni

```bash
bin/magento events:unsubscribe <event-code>
```


### `event-code`

Code d’événement auquel se désabonner

- Obligatoire

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `i18n:collect-phrases`

Découvre les expressions dans la base de code

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```


### `directory`

Chemin du répertoire à analyser. Pas nécessaire si l&#39;indicateur —magento est défini


### `--output`, `-o`

Chemin (nom de fichier inclus) vers un fichier de sortie. Si aucun fichier n’est spécifié, la valeur par défaut est stdout.

- Nécessite une valeur

### `--magento`, `-m`

Utilisez le paramètre —magento pour analyser la base de code actuelle du Magento. Omettez le paramètre si un répertoire est spécifié.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `i18n:pack`

Enregistre le package de langue

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```


### `source`

Chemin d’accès au fichier du dictionnaire source avec les traductions

- Obligatoire

### `locale`

Paramètres régionaux cibles pour le dictionnaire ; par exemple, « de_DE »

- Obligatoire

### `--mode`, `-m`

Mode d’enregistrement pour dictionnaire - « remplacer » - remplacer le module linguistique par un nouveau - « fusionner » - fusionner les modules linguistiques, par défaut « remplacer »

- Valeur par défaut : `replace`
- Nécessite une valeur

### `--allow-duplicates`, `-d`

Utilisez le paramètre —allow-duplicates pour enregistrer les doublons de la traduction. Sinon, omettez le paramètre .

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `i18n:uninstall`

Désinstalle les packages de langue

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```


### `package`

Nom du package de langue

- Valeur par défaut : `[]`

- Obligatoire
- Tableau

### `--backup-code`, `-b`

Sauvegarde du code et des fichiers de configuration (à l’exclusion des fichiers temporaires)

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `indexer:info`

Affiche les indexeurs autorisés

```bash
bin/magento indexer:info
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `indexer:reindex`

Réindexer les données

```bash
bin/magento indexer:reindex [<index>...]
```


### `index`

Liste séparée par des espaces de types d’index ou omettre de l’appliquer à tous les index.

- Valeur par défaut : `[]`

- Tableau

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `indexer:reset`

Réinitialise le statut de l’indexeur sur non valide

```bash
bin/magento indexer:reset [<index>...]
```


### `index`

Liste séparée par des espaces de types d’index ou omettre de l’appliquer à tous les index.

- Valeur par défaut : `[]`

- Tableau

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `indexer:set-dimensions-mode`

Définir le mode des Dimensions de l’indexeur

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```


### `indexer`

Nom de l’indexeur [catalog_product_price|catalogpermissions_category]


### `mode`

Modes de dimension de l’indexeur catalog_product_price none,website,customer_group,website_and_customer_group catalogpermissions_category none,customer_group


### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `indexer:set-mode`

Définit le type de mode d’index

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```


### `mode`

Type de mode de l’indexeur [temps réel|planning]


### `index`

Liste séparée par des espaces de types d’index ou omettre de l’appliquer à tous les index.

- Valeur par défaut : `[]`

- Tableau

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `indexer:set-status`

Définit le statut de l’indexeur spécifié

```bash
bin/magento indexer:set-status <status> [<index>...]
```


### `status`

Type de statut de l&#39;indexeur [non valide|suspendu|valide]

- Obligatoire

### `index`

Liste séparée par des espaces de types d’index ou omettre de l’appliquer à tous les index.

- Valeur par défaut : `[]`

- Tableau

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `indexer:show-dimensions-mode`

Affiche le mode de Dimension de l&#39;indexeur

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```


### `indexer`

Liste séparée par des espaces de types d’index ou omettre de s’appliquer à tous les index (catalog_product_price,catalogpermissions_category)

- Valeur par défaut : `[]`

- Tableau

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `indexer:show-mode`

Affiche le mode Index

```bash
bin/magento indexer:show-mode [<index>...]
```


### `index`

Liste séparée par des espaces de types d’index ou omettre de l’appliquer à tous les index.

- Valeur par défaut : `[]`

- Tableau

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `indexer:status`

Affiche le statut de l&#39;indexeur

```bash
bin/magento indexer:status [<index>...]
```


### `index`

Liste séparée par des espaces de types d’index ou omettre de l’appliquer à tous les index.

- Valeur par défaut : `[]`

- Tableau

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `info:adminuri`

Affiche l’URI d’administration du Magento

```bash
bin/magento info:adminuri
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `info:backups:list`

Imprime la liste des fichiers de sauvegarde disponibles

```bash
bin/magento info:backups:list
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `info:currency:list`

Affiche la liste des devises disponibles

```bash
bin/magento info:currency:list
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `info:dependencies:show-framework`

Affiche le nombre de dépendances sur le framework du Magento

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

### `--output`, `-o`

Nom de fichier du rapport

- Valeur par défaut : `framework-dependencies.csv`
- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `info:dependencies:show-modules`

Affiche le nombre de dépendances entre les modules

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

### `--output`, `-o`

Nom de fichier du rapport

- Valeur par défaut : `modules-dependencies.csv`
- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `info:dependencies:show-modules-circular`

Affiche le nombre de dépendances circulaires entre les modules

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

### `--output`, `-o`

Nom de fichier du rapport

- Valeur par défaut : `modules-circular-dependencies.csv`
- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `info:language:list`

Affiche la liste des langues locales disponibles

```bash
bin/magento info:language:list
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `info:timezone:list`

Affiche la liste des fuseaux horaires disponibles

```bash
bin/magento info:timezone:list
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `inventory:reservation:create-compensations`

Créer des réserves par arguments de compensation fournis

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```


### `compensations`

Liste des arguments de compensation au format « \&lt;order_increment_id>:\&lt;sku>:\&lt;quantity>:\&lt;stock-id>«

- Valeur par défaut : `[]`

- Tableau

### `--raw`, `-r`

Sortie brute

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `inventory:reservation:list-inconsistencies`

Afficher toutes les commandes et tous les produits avec des incohérences de quantité vendable

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

### `--complete-orders`, `-c`

Afficher uniquement les incohérences pour les commandes complètes

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--incomplete-orders`, `-i`

Afficher uniquement les incohérences pour les commandes incomplètes

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--bunch-size`, `-b`

Définit le nombre de commandes à charger simultanément

- Valeur par défaut : `50`
- Accepte une valeur

### `--raw`, `-r`

Sortie brute

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `inventory-geonames:import`

Téléchargement et importation de noms géographiques pour l’algorithme de sélection de source

```bash
bin/magento inventory-geonames:import <countries>...
```


### `countries`

Liste des codes pays à importer

- Valeur par défaut : `[]`

- Obligatoire
- Tableau

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `maintenance:allow-ips`

Définit les adresses IP exemptées du mode de maintenance

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```


### `ip`

Adresses IP autorisées

- Valeur par défaut : `[]`

- Tableau

### `--none`

Effacer les adresses IP autorisées

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--add`

Ajouter l’adresse IP à la liste existante

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `maintenance:disable`

Désactive le mode de maintenance

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Adresses IP autorisées (utilisez « aucune » pour effacer la liste d’adresses IP autorisées)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `maintenance:enable`

Active le mode de maintenance

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Adresses IP autorisées (utilisez « aucune » pour effacer la liste d’adresses IP autorisées)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `maintenance:status`

Affiche l’état du mode de maintenance

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `media-content:sync`

Synchronisation du contenu avec les ressources

```bash
bin/magento media-content:sync
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `media-gallery:sync`

Synchroniser le stockage multimédia et les ressources multimédias dans la base de données

```bash
bin/magento media-gallery:sync
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `module:config:status`

Vérifie la configuration des modules dans le fichier &#39;app/etc/config.php&#39; et indique s&#39;ils sont à jour ou non

```bash
bin/magento module:config:status
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `module:disable`

Désactive les modules spécifiés

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

Nom du module

- Valeur par défaut : `[]`

- Tableau

### `--force`, `-f`

Contournement de la vérification des dépendances

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--all`

Désactiver tous les modules

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--clear-static-content`, `-c`

Effacez les fichiers d’affichage statique générés. Nécessaire, si le ou les modules ont des fichiers de vue statiques

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `module:enable`

Active les modules spécifiés

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

Nom du module

- Valeur par défaut : `[]`

- Tableau

### `--force`, `-f`

Contournement de la vérification des dépendances

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--all`

Activer tous les modules

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--clear-static-content`, `-c`

Effacez les fichiers d’affichage statique générés. Nécessaire, si le ou les modules ont des fichiers de vue statiques

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `module:status`

Affiche le statut des modules

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```


### `module-names`

Nom du module optionnel

- Valeur par défaut : `[]`

- Tableau

### `--enabled`

Imprimer uniquement les modules activés

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--disabled`

Imprimer uniquement les modules désactivés

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `module:uninstall`

Désinstalle les modules installés par le compositeur

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```


### `module`

Nom du module

- Valeur par défaut : `[]`

- Obligatoire
- Tableau

### `--remove-data`, `-r`

Supprimer les données installées par le(s) module(s)

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--backup-code`

Sauvegarde du code et des fichiers de configuration (à l’exclusion des fichiers temporaires)

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--backup-media`

Effectuer une sauvegarde du média

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--backup-db`

Effectuer une sauvegarde complète de la base de données

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--non-composer`

Tous les modules qui seront passés ici ne seront pas basés sur le compositeur

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--clear-static-content`, `-c`

Effacez les fichiers d’affichage statique générés. Nécessaire, si le ou les modules ont des fichiers de vue statiques

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `newrelic:create:deploy-marker`

Recherchez des entrées dans la file d’attente de déploiement et créez un marqueur de déploiement approprié.

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```


### `message`

Déployer le message ?

- Obligatoire

### `change_log`

Journal des modifications ?

- Obligatoire

### `user`

Utilisateur du déploiement


### `revision`

Révision


### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `queue:consumers:list`

Liste des consommateurs MessageQueue

```bash
bin/magento queue:consumers:list
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `queue:consumers:restart`

Redémarrez les consommateurs MessageQueue

```bash
bin/magento queue:consumers:restart
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `queue:consumers:start`

Démarrer le client MessageQueue

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```


### `consumer`

Nom du client à démarrer.

- Obligatoire

### `--max-messages`

Nombre de messages à traiter par le client avant la fin du processus. Si non spécifié - s&#39;arrête après le traitement de tous les messages en file d&#39;attente.

- Nécessite une valeur

### `--batch-size`

Nombre de messages par lot. Applicable uniquement au consommateur par lots.

- Nécessite une valeur

### `--area-code`

La zone préférée (globale, adminhtml, etc.) par défaut est globale.

- Nécessite une valeur

### `--single-thread`

Cette option empêche l’exécution simultanée de plusieurs copies d’un client.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--multi-process`

Nombre de processus par client.

- Accepte une valeur

### `--pid-file-path`

Chemin d’accès au fichier pour l’enregistrement du PID (cette option est obsolète, utilisez —single-thread à la place)

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `remote-storage:sync`

Synchroniser les fichiers multimédias avec le stockage distant.

```bash
bin/magento remote-storage:sync
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `saas:resync`

Resynchronise les données de flux avec le service SaaS.

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync]
```

### `--feed`

Nom du flux pour resynchroniser complètement avec le service SaaS. Flux disponibles : Production de commande de services de paiement, Sandbox de commande de services de paiement, Production de statut de commande de services de paiement, Sandbox de statut de commande de services de paiement, Production de magasin de services de paiement, Sandbox de magasin de services de paiement

- Nécessite une valeur

### `--no-reindex`

Exécutez la re-soumission des données de flux au service SaaS uniquement. Ne se réindexe pas. (Cette option ne s’applique pas aux produits, aux remplacements de produits, aux flux de prix)

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--cleanup-feed`

Forcer le nettoyage de la table de l’indexeur de flux avant la synchronisation.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--dry-run`

Exécution d’essai. Les données ne seront pas exportées. Pour enregistrer la payload dans le fichier journal var/log/saas-export.log, exécutez avec la variable d’environnement EXPORTER_EXTENDED_LOG=1.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--thread-count`

Définissez le nombre de threads de synchronisation.

- Nécessite une valeur

### `--batch-size`

Définir la taille du lot de synchronisation

- Nécessite une valeur

### `--continue-resync`

Continuer la resynchronisation depuis la dernière position stockée (cette option s’applique aux produits, aux remplacements de produits, aux flux de prix)

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `sampledata:deploy`

Déployer des exemples de modules de données pour les installations de Magento basé sur un compositeur

```bash
bin/magento sampledata:deploy [--no-update]
```

### `--no-update`

Mettre à jour composer.json sans exécuter la mise à jour du compositeur

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `sampledata:remove`

Supprimer tous les exemples de packages de données de composer.json

```bash
bin/magento sampledata:remove [--no-update]
```

### `--no-update`

Mettre à jour composer.json sans exécuter la mise à jour du compositeur

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `sampledata:reset`

Réinitialiser tous les exemples de modules de données pour la réinstallation

```bash
bin/magento sampledata:reset
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `security:recaptcha:disable-for-user-forgot-password`

Désactiver reCAPTCHA pour formulaire de mot de passe oublié pour l’utilisateur administrateur

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `security:recaptcha:disable-for-user-login`

Désactiver reCAPTCHA pour le formulaire de connexion de l’utilisateur administrateur

```bash
bin/magento security:recaptcha:disable-for-user-login
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `security:tfa:google:set-secret`

Définissez le secret utilisé pour la génération du mot de passe à usage unique Google.

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```


### `user`

Nom d’utilisateur

- Obligatoire

### `secret`

Secret

- Obligatoire

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `security:tfa:providers`

Liste de tous les fournisseurs disponibles

```bash
bin/magento security:tfa:providers
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `security:tfa:reset`

Réinitialiser la configuration pour un utilisateur

```bash
bin/magento security:tfa:reset <user> <provider>
```


### `user`

Nom d’utilisateur

- Obligatoire

### `provider`

Code fournisseur

- Obligatoire

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `server:run`

Exécution du serveur d’applications

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-wn|--workerNum [WORKERNUM]] [-dm|--dispatchMode [DISPATCHMODE]] [-mr|--maxRequests [MAXREQUESTS]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]] [-mwt|--maxWaitTime [MAXWAITTIME]] [--state-monitor]
```

### `--port`, `-p`

port sur lequel servir

- Valeur par défaut : `9501`
- Accepte une valeur

### `--background`, `-b`

indicateur de mode arrière-plan

- Valeur par défaut : `0`
- Accepte une valeur

### `--workerNum`, `-wn`

nombre de processus de travail à démarrer

- Valeur par défaut : `4`
- Accepte une valeur

### `--dispatchMode`, `-dm`

mode de répartition des connexions aux processus de travail

- Valeur par défaut : `3`
- Accepte une valeur

### `--maxRequests`, `-mr`

nombre maximal de requêtes avant le redémarrage du processus de travail

- Valeur par défaut : `10000`
- Accepte une valeur

### `--area`, `-a`

zone du serveur d’applications

- Valeur par défaut : `graphql`
- Accepte une valeur

### `--magento-init-params`, `-mip`

paramètres init d’amorçage magento

- Valeur par défaut : «
- Accepte une valeur

### `--maxWaitTime`, `-mwt`

la durée d&#39;attente des programmes de travail après le rechargement (par ex. config change) avant de les tuer

- Valeur par défaut : `3600`
- Accepte une valeur

### `--state-monitor`

Activez la surveillance de l’état. N’utilisez cette option que pour les problèmes d’état de débogage.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `server:state-monitor:aggregate-output`

Sortie agrégée du moniteur d&#39;état d&#39;ApplicationServer

```bash
bin/magento server:state-monitor:aggregate-output
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:backup`

Sauvegarde de la base de code, du média et de la base de données de l&#39;application Magento

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code`

Sauvegarde du code et des fichiers de configuration (à l’exclusion des fichiers temporaires)

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--media`

Effectuer une sauvegarde du média

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--db`

Effectuer une sauvegarde complète de la base de données

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:config:set`

Crée ou modifie la configuration de déploiement

```bash
bin/magento setup:config:set [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--enable-debug-logging`

Activer la journalisation du débogage

- Nécessite une valeur

### `--enable-syslog-logging`

Activer la journalisation syslog

- Nécessite une valeur

### `--backend-frontname`

Nom du front-end (sera généré automatiquement s’il est manquant)

- Nécessite une valeur

### `--remote-storage-driver`

Pilote de stockage distant

- Nécessite une valeur

### `--remote-storage-prefix`

Préfixe de stockage distant

- Valeur par défaut : «
- Nécessite une valeur

### `--remote-storage-endpoint`

Point d’entrée du stockage distant

- Nécessite une valeur

### `--remote-storage-bucket`

Compartiment de stockage distant

- Nécessite une valeur

### `--remote-storage-region`

Région de stockage distante

- Nécessite une valeur

### `--remote-storage-key`

Clé d’accès au stockage distant

- Valeur par défaut : «
- Nécessite une valeur

### `--remote-storage-secret`

Clé secrète de stockage distant

- Valeur par défaut : «
- Nécessite une valeur

### `--remote-storage-path-style`

Style du chemin de stockage distant

- Valeur par défaut : `0`
- Nécessite une valeur

### `--id_salt`

GraphQl Salt

- Nécessite une valeur

### `--config-async`

Activer l’enregistrement de la configuration d’administration asynchrone ? 1 - Oui, 0 - Non

- Nécessite une valeur

### `--checkout-async`

Activer le traitement asynchrone des commandes ? 1 - Oui, 0 - Non

- Nécessite une valeur

### `--amqp-host`

Hôte du serveur AMP

- Valeur par défaut : «
- Nécessite une valeur

### `--amqp-port`

Port du serveur AMP

- Valeur par défaut : `5672`
- Nécessite une valeur

### `--amqp-user`

Nom d’utilisateur du serveur AMP

- Valeur par défaut : «
- Nécessite une valeur

### `--amqp-password`

Mot de passe du serveur AMP

- Valeur par défaut : «
- Nécessite une valeur

### `--amqp-virtualhost`

Amqp virtualhost

- Valeur par défaut : `/`
- Nécessite une valeur

### `--amqp-ssl`

Amapp SSL

- Valeur par défaut : «
- Nécessite une valeur

### `--amqp-ssl-options`

Options SSL AMP (JSON)

- Valeur par défaut : «
- Nécessite une valeur

### `--consumers-wait-for-messages`

Les consommateurs doivent-ils attendre un message de la file d’attente ? 1 - Oui, 0 - Non

- Nécessite une valeur

### `--queue-default-connection`

Connexion par défaut aux files d&#39;attente des messages. Peut être &#39;db&#39;, &#39;amqp&#39; ou un système de file d&#39;attente personnalisé. Le système de file d&#39;attente doit être installé et configuré, sinon les messages ne seront pas traités correctement.

- Nécessite une valeur

### `--deferred-total-calculating`

Activer le calcul du total différé ? 1 - Oui, 0 - Non

- Nécessite une valeur

### `--key`

Clé de chiffrement

- Nécessite une valeur

### `--db-host`

Hôte du serveur de base de données

- Nécessite une valeur

### `--db-name`

Nom de la base

- Nécessite une valeur

### `--db-user`

Nom d&#39;utilisateur du serveur de base de données

- Nécessite une valeur

### `--db-engine`

Moteur de serveur de base de données

- Nécessite une valeur

### `--db-password`

Mot de passe du serveur de base de données

- Nécessite une valeur

### `--db-prefix`

Préfixe de table de base de données

- Nécessite une valeur

### `--db-model`

Type de base

- Nécessite une valeur

### `--db-init-statements`

Ensemble initial de commandes de la base de données

- Nécessite une valeur

### `--skip-db-validation`, `-s`

Si spécifié, la validation de la connexion à la base de données est ignorée

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--http-cache-hosts`

Hôtes de cache http

- Nécessite une valeur

### `--db-ssl-key`

Chemin complet du fichier de clé cliente afin d&#39;établir la connexion de base de données via SSL

- Valeur par défaut : «
- Nécessite une valeur

### `--db-ssl-cert`

Chemin complet du fichier de certificat client pour établir la connexion de base de données via SSL

- Valeur par défaut : «
- Nécessite une valeur

### `--db-ssl-ca`

Chemin complet du fichier de certificat du serveur pour établir la connexion à la base de données via SSL

- Valeur par défaut : «
- Nécessite une valeur

### `--db-ssl-verify`

Vérifier la certification du serveur

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--session-save`

Gestionnaire d’enregistrement de session

- Nécessite une valeur

### `--session-save-redis-host`

Nom d’hôte complet, adresse IP ou chemin absolu si vous utilisez des sockets UNIX

- Nécessite une valeur

### `--session-save-redis-port`

Port d’écoute du serveur Redis

- Nécessite une valeur

### `--session-save-redis-password`

Mot de passe du serveur Redis

- Nécessite une valeur

### `--session-save-redis-timeout`

Timeout de connexion, en secondes

- Nécessite une valeur

### `--session-save-redis-persistent-id`

Chaîne unique pour activer les connexions persistantes

- Nécessite une valeur

### `--session-save-redis-db`

Numéro de la base de données Redis

- Nécessite une valeur

### `--session-save-redis-compression-threshold`

Seuil de recompression

- Nécessite une valeur

### `--session-save-redis-compression-lib`

Bibliothèque de compression Redis. Valeurs : gzip (par défaut), lzf, lz4, snappy

- Nécessite une valeur

### `--session-save-redis-log-level`

Niveau de journalisation Redis. Valeurs : de 0 (le moins détaillé) à 7 (le plus détaillé)

- Nécessite une valeur

### `--session-save-redis-max-concurrency`

Nombre maximum de processus pouvant attendre un verrou sur une session

- Nécessite une valeur

### `--session-save-redis-break-after-frontend`

Nombre de secondes à attendre avant d’essayer d’interrompre un verrou pour une session front-end

- Nécessite une valeur

### `--session-save-redis-break-after-adminhtml`

Nombre de secondes à attendre avant d’essayer de rompre un verrou pour une session d’administrateur

- Nécessite une valeur

### `--session-save-redis-first-lifetime`

Durée de vie, en secondes, de la session pour les non-robots lors de la première écriture (utilisez 0 pour désactiver)

- Nécessite une valeur

### `--session-save-redis-bot-first-lifetime`

Durée de vie, en secondes, de la session des robots lors de la première écriture (utilisez 0 pour désactiver).

- Nécessite une valeur

### `--session-save-redis-bot-lifetime`

Durée de vie de la session pour les robots lors des écritures suivantes (utilisez 0 pour désactiver)

- Nécessite une valeur

### `--session-save-redis-disable-locking`

Redis désactiver le verrouillage. Valeurs : false (par défaut), true

- Nécessite une valeur

### `--session-save-redis-min-lifetime`

Durée de vie de la session de reprise, en secondes

- Nécessite une valeur

### `--session-save-redis-max-lifetime`

Durée de vie maximale de la session Redis, en secondes

- Nécessite une valeur

### `--session-save-redis-sentinel-master`

Maître Redis Sentinel

- Nécessite une valeur

### `--session-save-redis-sentinel-servers`

Serveurs Redis Sentinel, séparés par des virgules

- Nécessite une valeur

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel Vérifier le maître. Valeurs : false (par défaut), true

- Nécessite une valeur

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel reprises de connexion.

- Nécessite une valeur

### `--cache-backend`

Gestionnaire de cache par défaut

- Nécessite une valeur

### `--cache-backend-redis-server`

Serveur Redis

- Nécessite une valeur

### `--cache-backend-redis-db`

Numéro de base de données pour le cache

- Nécessite une valeur

### `--cache-backend-redis-port`

Port d’écoute du serveur Redis

- Nécessite une valeur

### `--cache-backend-redis-password`

Mot de passe du serveur Redis

- Nécessite une valeur

### `--cache-backend-redis-compress-data`

Définissez sur 0 pour désactiver la compression (1 par défaut, activé).

- Nécessite une valeur

### `--cache-backend-redis-compression-lib`

Bibliothèque de compression à utiliser [snappy,lzf,l4z,zstd,gzip] (laisser vide pour déterminer automatiquement)

- Nécessite une valeur

### `--cache-backend-redis-use-lua`

Définissez sur 1 pour activer lua (0 par défaut, désactivé).

- Nécessite une valeur

### `--cache-id-prefix`

Préfixe d’ID pour les clés de cache

- Nécessite une valeur

### `--allow-parallel-generation`

Autoriser la génération du cache de manière non bloquante

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--page-cache`

Gestionnaire de cache par défaut

- Nécessite une valeur

### `--page-cache-redis-server`

Serveur Redis

- Nécessite une valeur

### `--page-cache-redis-db`

Numéro de base de données pour le cache

- Nécessite une valeur

### `--page-cache-redis-port`

Port d’écoute du serveur Redis

- Nécessite une valeur

### `--page-cache-redis-password`

Mot de passe du serveur Redis

- Nécessite une valeur

### `--page-cache-redis-compress-data`

Définissez cette valeur sur 1 pour compresser le cache de page complet (utilisez 0 pour le désactiver).

- Nécessite une valeur

### `--page-cache-redis-compression-lib`

Bibliothèque de compression à utiliser [snappy,lzf,l4z,zstd,gzip] (laisser vide pour déterminer automatiquement)

- Nécessite une valeur

### `--page-cache-id-prefix`

Préfixe d’ID pour les clés de cache

- Nécessite une valeur

### `--lock-provider`

Verrouiller le nom du fournisseur

- Nécessite une valeur

### `--lock-db-prefix`

Préfixe de verrou spécifique à l’installation pour éviter les conflits de verrou

- Nécessite une valeur

### `--lock-zookeeper-host`

Hôte et port pour la connexion au cluster Zookeeper. Par exemple : 127.0.0.1:2181

- Nécessite une valeur

### `--lock-zookeeper-path`

Chemin où Zookeeper enregistrera les verrous. Le chemin par défaut est : /magento/locks

- Nécessite une valeur

### `--lock-file-path`

Chemin d’accès où le fichier sera verrouillé.

- Nécessite une valeur

### `--document-root-is-pub`

Indicateur à afficher : Pub est à la racine, peut être vrai ou faux uniquement

- Nécessite une valeur

### `--backpressure-logger`

Dispositif de manutention d&#39;un enregistreur de contre-pression

- Nécessite une valeur

### `--backpressure-logger-redis-server`

Serveur Redis

- Nécessite une valeur

### `--backpressure-logger-redis-port`

Port d’écoute du serveur Redis

- Nécessite une valeur

### `--backpressure-logger-redis-timeout`

Délai d’expiration du serveur Redis

- Nécessite une valeur

### `--backpressure-logger-redis-persistent`

Redis persistant

- Nécessite une valeur

### `--backpressure-logger-redis-db`

Numéro de la BD Redis

- Nécessite une valeur

### `--backpressure-logger-redis-password`

Mot de passe du serveur Redis

- Nécessite une valeur

### `--backpressure-logger-redis-user`

Utilisateur Redis server

- Nécessite une valeur

### `--backpressure-logger-id-prefix`

Préfixe d’ID pour les clés

- Nécessite une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:db-data:upgrade`

Installe et met à niveau les données de la base de données

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:db-declaration:generate-patch`

Générez un correctif et placez-le dans un dossier spécifique.

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```


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

Découvrez quel type de correctif doit être généré. Valeurs disponibles : `data`, `schema`.

- Valeur par défaut : `data`
- Accepte une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:db-declaration:generate-whitelist`

Générer une liste blanche des tables et colonnes pouvant être modifiées par le programme d&#39;installation de la déclaration

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

### `--module-name`

Nom du module dans lequel la liste autorisée sera générée

- Valeur par défaut : `all`
- Accepte une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:db-schema:add-slave`

Déplacer les tables liées aux devis de passage en caisse vers un serveur DB distinct

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Hôte du serveur de base de données esclave

- Valeur par défaut : `localhost`
- Nécessite une valeur

### `--dbname`

Nom de la base de données esclave

- Nécessite une valeur

### `--username`

Nom d&#39;utilisateur de la base de données esclave

- Valeur par défaut : `root`
- Nécessite une valeur

### `--password`

Mot de passe de l&#39;utilisateur de la base de données esclave

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

Connexion d&#39;esclave de décalage max. autorisée (en secondes)

- Valeur par défaut : «
- Accepte une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:db-schema:split-quote`

Déplacez les tables liées aux devis de passage en caisse vers un serveur de base de données distinct. Obsolète depuis la version 2.4.2 et sera supprimé

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Extraction de l’hôte du serveur de base de données

- Nécessite une valeur

### `--dbname`

Extraction du nom de la base de données

- Nécessite une valeur

### `--username`

Nom d&#39;utilisateur de la base de données de passage en caisse

- Nécessite une valeur

### `--password`

Extraction du mot de passe utilisateur de la base de données

- Accepte une valeur

### `--connection`

Extraction du nom de la connexion

- Valeur par défaut : `checkout`
- Accepte une valeur

### `--resource`

Nom de la ressource de passage en caisse

- Valeur par défaut : `checkout`
- Accepte une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:db-schema:split-sales`

Déplacer les tables liées aux ventes vers un serveur de base de données distinct. Obsolète depuis la version 2.4.2 et sera supprimé

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Hôte du serveur de base de données Sales

- Nécessite une valeur

### `--dbname`

Nom de la base de données des ventes

- Nécessite une valeur

### `--username`

Nom d’utilisateur de la base de données des ventes

- Nécessite une valeur

### `--password`

Mot de passe de l’utilisateur de la base de données Sales

- Accepte une valeur

### `--connection`

Nom de la connexion de vente

- Valeur par défaut : `sales`
- Accepte une valeur

### `--resource`

Nom de la ressource de vente

- Valeur par défaut : `sales`
- Accepte une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:db-schema:upgrade`

Installe et met à niveau le schéma de base de données

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--convert-old-scripts`

Permet de convertir d’anciens scripts (InstallSchema, UpgradeSchema) au format db_schema.xml

- Valeur par défaut : `false`
- Accepte une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:db:status`

Vérifie si le schéma ou les données de la base de données doivent être mis à niveau

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:di:compile`

Génère la configuration d’ID et toutes les classes manquantes qui peuvent être générées automatiquement

```bash
bin/magento setup:di:compile
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:install`

Installe l’application du Magento

```bash
bin/magento setup:install [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--enable-debug-logging`

Activer la journalisation du débogage

- Nécessite une valeur

### `--enable-syslog-logging`

Activer la journalisation syslog

- Nécessite une valeur

### `--backend-frontname`

Nom du front-end (sera généré automatiquement s’il est manquant)

- Nécessite une valeur

### `--remote-storage-driver`

Pilote de stockage distant

- Nécessite une valeur

### `--remote-storage-prefix`

Préfixe de stockage distant

- Valeur par défaut : «
- Nécessite une valeur

### `--remote-storage-endpoint`

Point d’entrée du stockage distant

- Nécessite une valeur

### `--remote-storage-bucket`

Compartiment de stockage distant

- Nécessite une valeur

### `--remote-storage-region`

Région de stockage distante

- Nécessite une valeur

### `--remote-storage-key`

Clé d’accès au stockage distant

- Valeur par défaut : «
- Nécessite une valeur

### `--remote-storage-secret`

Clé secrète de stockage distant

- Valeur par défaut : «
- Nécessite une valeur

### `--remote-storage-path-style`

Style du chemin de stockage distant

- Valeur par défaut : `0`
- Nécessite une valeur

### `--id_salt`

GraphQl Salt

- Nécessite une valeur

### `--config-async`

Activer l’enregistrement de la configuration d’administration asynchrone ? 1 - Oui, 0 - Non

- Nécessite une valeur

### `--checkout-async`

Activer le traitement asynchrone des commandes ? 1 - Oui, 0 - Non

- Nécessite une valeur

### `--amqp-host`

Hôte du serveur AMP

- Valeur par défaut : «
- Nécessite une valeur

### `--amqp-port`

Port du serveur AMP

- Valeur par défaut : `5672`
- Nécessite une valeur

### `--amqp-user`

Nom d’utilisateur du serveur AMP

- Valeur par défaut : «
- Nécessite une valeur

### `--amqp-password`

Mot de passe du serveur AMP

- Valeur par défaut : «
- Nécessite une valeur

### `--amqp-virtualhost`

Amqp virtualhost

- Valeur par défaut : `/`
- Nécessite une valeur

### `--amqp-ssl`

Amapp SSL

- Valeur par défaut : «
- Nécessite une valeur

### `--amqp-ssl-options`

Options SSL AMP (JSON)

- Valeur par défaut : «
- Nécessite une valeur

### `--consumers-wait-for-messages`

Les consommateurs doivent-ils attendre un message de la file d’attente ? 1 - Oui, 0 - Non

- Nécessite une valeur

### `--queue-default-connection`

Connexion par défaut aux files d&#39;attente des messages. Peut être &#39;db&#39;, &#39;amqp&#39; ou un système de file d&#39;attente personnalisé. Le système de file d&#39;attente doit être installé et configuré, sinon les messages ne seront pas traités correctement.

- Nécessite une valeur

### `--deferred-total-calculating`

Activer le calcul du total différé ? 1 - Oui, 0 - Non

- Nécessite une valeur

### `--key`

Clé de chiffrement

- Nécessite une valeur

### `--db-host`

Hôte du serveur de base de données

- Nécessite une valeur

### `--db-name`

Nom de la base

- Nécessite une valeur

### `--db-user`

Nom d&#39;utilisateur du serveur de base de données

- Nécessite une valeur

### `--db-engine`

Moteur de serveur de base de données

- Nécessite une valeur

### `--db-password`

Mot de passe du serveur de base de données

- Nécessite une valeur

### `--db-prefix`

Préfixe de table de base de données

- Nécessite une valeur

### `--db-model`

Type de base

- Nécessite une valeur

### `--db-init-statements`

Ensemble initial de commandes de la base de données

- Nécessite une valeur

### `--skip-db-validation`, `-s`

Si spécifié, la validation de la connexion à la base de données est ignorée

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--http-cache-hosts`

Hôtes de cache http

- Nécessite une valeur

### `--db-ssl-key`

Chemin complet du fichier de clé cliente afin d&#39;établir la connexion de base de données via SSL

- Valeur par défaut : «
- Nécessite une valeur

### `--db-ssl-cert`

Chemin complet du fichier de certificat client pour établir la connexion de base de données via SSL

- Valeur par défaut : «
- Nécessite une valeur

### `--db-ssl-ca`

Chemin complet du fichier de certificat du serveur pour établir la connexion à la base de données via SSL

- Valeur par défaut : «
- Nécessite une valeur

### `--db-ssl-verify`

Vérifier la certification du serveur

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--session-save`

Gestionnaire d’enregistrement de session

- Nécessite une valeur

### `--session-save-redis-host`

Nom d’hôte complet, adresse IP ou chemin absolu si vous utilisez des sockets UNIX

- Nécessite une valeur

### `--session-save-redis-port`

Port d’écoute du serveur Redis

- Nécessite une valeur

### `--session-save-redis-password`

Mot de passe du serveur Redis

- Nécessite une valeur

### `--session-save-redis-timeout`

Timeout de connexion, en secondes

- Nécessite une valeur

### `--session-save-redis-persistent-id`

Chaîne unique pour activer les connexions persistantes

- Nécessite une valeur

### `--session-save-redis-db`

Numéro de la base de données Redis

- Nécessite une valeur

### `--session-save-redis-compression-threshold`

Seuil de recompression

- Nécessite une valeur

### `--session-save-redis-compression-lib`

Bibliothèque de compression Redis. Valeurs : gzip (par défaut), lzf, lz4, snappy

- Nécessite une valeur

### `--session-save-redis-log-level`

Niveau de journalisation Redis. Valeurs : de 0 (le moins détaillé) à 7 (le plus détaillé)

- Nécessite une valeur

### `--session-save-redis-max-concurrency`

Nombre maximum de processus pouvant attendre un verrou sur une session

- Nécessite une valeur

### `--session-save-redis-break-after-frontend`

Nombre de secondes à attendre avant d’essayer d’interrompre un verrou pour une session front-end

- Nécessite une valeur

### `--session-save-redis-break-after-adminhtml`

Nombre de secondes à attendre avant d’essayer de rompre un verrou pour une session d’administrateur

- Nécessite une valeur

### `--session-save-redis-first-lifetime`

Durée de vie, en secondes, de la session pour les non-robots lors de la première écriture (utilisez 0 pour désactiver)

- Nécessite une valeur

### `--session-save-redis-bot-first-lifetime`

Durée de vie, en secondes, de la session des robots lors de la première écriture (utilisez 0 pour désactiver).

- Nécessite une valeur

### `--session-save-redis-bot-lifetime`

Durée de vie de la session pour les robots lors des écritures suivantes (utilisez 0 pour désactiver)

- Nécessite une valeur

### `--session-save-redis-disable-locking`

Redis désactiver le verrouillage. Valeurs : false (par défaut), true

- Nécessite une valeur

### `--session-save-redis-min-lifetime`

Durée de vie de la session de reprise, en secondes

- Nécessite une valeur

### `--session-save-redis-max-lifetime`

Durée de vie maximale de la session Redis, en secondes

- Nécessite une valeur

### `--session-save-redis-sentinel-master`

Maître Redis Sentinel

- Nécessite une valeur

### `--session-save-redis-sentinel-servers`

Serveurs Redis Sentinel, séparés par des virgules

- Nécessite une valeur

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel Vérifier le maître. Valeurs : false (par défaut), true

- Nécessite une valeur

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel reprises de connexion.

- Nécessite une valeur

### `--cache-backend`

Gestionnaire de cache par défaut

- Nécessite une valeur

### `--cache-backend-redis-server`

Serveur Redis

- Nécessite une valeur

### `--cache-backend-redis-db`

Numéro de base de données pour le cache

- Nécessite une valeur

### `--cache-backend-redis-port`

Port d’écoute du serveur Redis

- Nécessite une valeur

### `--cache-backend-redis-password`

Mot de passe du serveur Redis

- Nécessite une valeur

### `--cache-backend-redis-compress-data`

Définissez sur 0 pour désactiver la compression (1 par défaut, activé).

- Nécessite une valeur

### `--cache-backend-redis-compression-lib`

Bibliothèque de compression à utiliser [snappy,lzf,l4z,zstd,gzip] (laisser vide pour déterminer automatiquement)

- Nécessite une valeur

### `--cache-backend-redis-use-lua`

Définissez sur 1 pour activer lua (0 par défaut, désactivé).

- Nécessite une valeur

### `--cache-id-prefix`

Préfixe d’ID pour les clés de cache

- Nécessite une valeur

### `--allow-parallel-generation`

Autoriser la génération du cache de manière non bloquante

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--page-cache`

Gestionnaire de cache par défaut

- Nécessite une valeur

### `--page-cache-redis-server`

Serveur Redis

- Nécessite une valeur

### `--page-cache-redis-db`

Numéro de base de données pour le cache

- Nécessite une valeur

### `--page-cache-redis-port`

Port d’écoute du serveur Redis

- Nécessite une valeur

### `--page-cache-redis-password`

Mot de passe du serveur Redis

- Nécessite une valeur

### `--page-cache-redis-compress-data`

Définissez cette valeur sur 1 pour compresser le cache de page complet (utilisez 0 pour le désactiver).

- Nécessite une valeur

### `--page-cache-redis-compression-lib`

Bibliothèque de compression à utiliser [snappy,lzf,l4z,zstd,gzip] (laisser vide pour déterminer automatiquement)

- Nécessite une valeur

### `--page-cache-id-prefix`

Préfixe d’ID pour les clés de cache

- Nécessite une valeur

### `--lock-provider`

Verrouiller le nom du fournisseur

- Nécessite une valeur

### `--lock-db-prefix`

Préfixe de verrou spécifique à l’installation pour éviter les conflits de verrou

- Nécessite une valeur

### `--lock-zookeeper-host`

Hôte et port pour la connexion au cluster Zookeeper. Par exemple : 127.0.0.1:2181

- Nécessite une valeur

### `--lock-zookeeper-path`

Chemin où Zookeeper enregistrera les verrous. Le chemin par défaut est : /magento/locks

- Nécessite une valeur

### `--lock-file-path`

Chemin d’accès où le fichier sera verrouillé.

- Nécessite une valeur

### `--document-root-is-pub`

Indicateur à afficher : Pub est à la racine, peut être vrai ou faux uniquement

- Nécessite une valeur

### `--backpressure-logger`

Dispositif de manutention d&#39;un enregistreur de contre-pression

- Nécessite une valeur

### `--backpressure-logger-redis-server`

Serveur Redis

- Nécessite une valeur

### `--backpressure-logger-redis-port`

Port d’écoute du serveur Redis

- Nécessite une valeur

### `--backpressure-logger-redis-timeout`

Délai d’expiration du serveur Redis

- Nécessite une valeur

### `--backpressure-logger-redis-persistent`

Redis persistant

- Nécessite une valeur

### `--backpressure-logger-redis-db`

Numéro de la BD Redis

- Nécessite une valeur

### `--backpressure-logger-redis-password`

Mot de passe du serveur Redis

- Nécessite une valeur

### `--backpressure-logger-redis-user`

Utilisateur Redis server

- Nécessite une valeur

### `--backpressure-logger-id-prefix`

Préfixe d’ID pour les clés

- Nécessite une valeur

### `--base-url`

URL vers laquelle le magasin est censé être disponible. Obsolète, utilisez config:set avec le chemin web/unsecure/base_url

- Nécessite une valeur

### `--language`

Code de langue par défaut. Obsolète, utilisez config:set avec le chemin general/locale/code

- Nécessite une valeur

### `--timezone`

Code de fuseau horaire par défaut. Obsolète, utilisez config:set avec le chemin general/locale/timezone

- Nécessite une valeur

### `--currency`

Code de devise par défaut. Obsolète, utilisez config:set avec le chemin currency/options/base, currency/options/default et currency/options/allow .

- Nécessite une valeur

### `--use-rewrites`

Utiliser les réécritures. Obsolète, utilisez config:set avec le chemin web/seo/use_rewrites

- Nécessite une valeur

### `--use-secure`

Utilisez des URL sécurisées. Activez cette option uniquement si SSL est disponible. Obsolète, utiliser config:set avec le chemin web/secure/use_in_frontend

- Nécessite une valeur

### `--base-url-secure`

URL de base de la connexion SSL. Obsolète, utilisez config:set avec le chemin web/secure/base_url

- Nécessite une valeur

### `--use-secure-admin`

Exécutez l’interface d’administration avec SSL. Obsolète, utilisez config:set avec le chemin web/secure/use_in_adminhtml

- Nécessite une valeur

### `--admin-use-security-key`

Si la fonction « clé de sécurité » doit être utilisée dans les formulaires et les URL d’administration de Magento. Obsolète, utilisez config:set avec le chemin admin/security/use_form_key

- Nécessite une valeur

### `--admin-user`

Utilisateur administrateur

- Accepte une valeur

### `--admin-password`

Mot de passe administrateur

- Accepte une valeur

### `--admin-email`

Adresse e-mail de l’administrateur

- Accepte une valeur

### `--admin-firstname`

Prénom de l’administrateur

- Accepte une valeur

### `--admin-lastname`

Nom de famille de l’administrateur

- Accepte une valeur

### `--search-engine`

Moteur de recherche. Valeurs : elasticsearch7, elasticsearch8, opensearch

- Nécessite une valeur

### `--elasticsearch-host`

Hôte de serveur Elasticsearch.

- Nécessite une valeur

### `--elasticsearch-port`

Port du serveur Elasticsearch.

- Nécessite une valeur

### `--elasticsearch-enable-auth`

Définissez sur 1 pour activer l’authentification. (la valeur par défaut est 0, désactivé)

- Nécessite une valeur

### `--elasticsearch-username`

Nom d’utilisateur Elasticsearch. Applicable uniquement si l’authentification HTTP est activée

- Nécessite une valeur

### `--elasticsearch-password`

Mot de passe Elasticsearch. Applicable uniquement si l’authentification HTTP est activée

- Nécessite une valeur

### `--elasticsearch-index-prefix`

Préfixe d’index Elasticsearch.

- Nécessite une valeur

### `--elasticsearch-timeout`

Timeout du serveur Elasticsearch.

- Nécessite une valeur

### `--opensearch-host`

Hôte du serveur OpenSearch.

- Nécessite une valeur

### `--opensearch-port`

Port du serveur OpenSearch.

- Nécessite une valeur

### `--opensearch-enable-auth`

Définissez sur 1 pour activer l’authentification. (la valeur par défaut est 0, désactivé)

- Nécessite une valeur

### `--opensearch-username`

Nom d’utilisateur OpenSearch. Applicable uniquement si l’authentification HTTP est activée

- Nécessite une valeur

### `--opensearch-password`

Mot de passe OpenSearch. Applicable uniquement si l’authentification HTTP est activée

- Nécessite une valeur

### `--opensearch-index-prefix`

Préfixe d’index OpenSearch.

- Nécessite une valeur

### `--opensearch-timeout`

Timeout du serveur OpenSearch.

- Nécessite une valeur

### `--cleanup-database`

Nettoyage de la base de données avant installation

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--sales-order-increment-prefix`

Préfixe du numéro de commande client

- Nécessite une valeur

### `--use-sample-data`

Utiliser les exemples de données

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--enable-modules`

Liste de noms de modules séparés par des virgules. Cela doit être inclus lors de l’installation. Paramètre magique disponible « all ».

- Accepte une valeur

### `--disable-modules`

Liste de noms de modules séparés par des virgules. Cela doit être évité lors de l’installation. Paramètre magique disponible « all ».

- Accepte une valeur

### `--convert-old-scripts`

Permet de convertir d’anciens scripts (InstallSchema, UpgradeSchema) au format db_schema.xml

- Valeur par défaut : `false`
- Accepte une valeur

### `--interactive`, `-i`

Installation du Magento interactif

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--safe-mode`

Installation sûre du Magento avec des vidages sur les opérations destructives, comme l&#39;enlèvement de colonne

- Accepte une valeur

### `--data-restore`

Restaurer les données supprimées des images mémoire

- Accepte une valeur

### `--dry-run`

L’installation du Magento sera exécutée en mode d’exécution d’essai

- Valeur par défaut : `false`
- Accepte une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:performance:generate-fixtures`

Génère des brides

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```


### `profile`

Chemin d’accès au fichier de configuration du profil

- Obligatoire

### `--skip-reindex`, `-s`

Ignorer la réindexation

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:rollback`

Restauration de la base de code, du média et de la base de données de l’application Magento

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code-file`, `-c`

Nom de base du fichier de sauvegarde du code dans var/backups

- Nécessite une valeur

### `--media-file`, `-m`

Nom de base du fichier de sauvegarde multimédia dans var/backups

- Nécessite une valeur

### `--db-file`, `-d`

Nom de base du fichier de sauvegarde de la base de données dans var/backup

- Nécessite une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:static-content:deploy`

Déploie des fichiers d’affichage statiques

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```


### `languages`

Liste séparée par des espaces de codes de langue ISO-639 pour lesquels générer des fichiers de vue statiques.

- Valeur par défaut : `[]`

- Tableau

### `--force`, `-f`

Déployez des fichiers dans n’importe quel mode.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--strategy`, `-s`

Déployez des fichiers à l’aide de la stratégie spécifiée.

- Valeur par défaut : `quick`
- Accepte une valeur

### `--area`, `-a`

Générer des fichiers uniquement pour les zones spécifiées.

- Valeur par défaut : `all`
- Accepte plusieurs valeurs

### `--exclude-area`

Ne générez pas de fichiers pour les zones spécifiées.

- Valeur par défaut : `none`
- Accepte plusieurs valeurs

### `--theme`, `-t`

Générer des fichiers d’affichage statiques pour les thèmes spécifiés uniquement.

- Valeur par défaut : `all`
- Accepte plusieurs valeurs

### `--exclude-theme`

Ne pas générer de fichiers pour les thèmes spécifiés

- Valeur par défaut : `none`
- Accepte plusieurs valeurs

### `--language`, `-l`

Générer des fichiers uniquement pour les langues spécifiées.

- Valeur par défaut : `all`
- Accepte plusieurs valeurs

### `--exclude-language`

Ne générez pas de fichiers pour les langues spécifiées.

- Valeur par défaut : `none`
- Accepte plusieurs valeurs

### `--jobs`, `-j`

Activez le traitement parallèle en utilisant le nombre de tâches spécifié.

- Valeur par défaut : `0`
- Accepte une valeur

### `--max-execution-time`

Durée d&#39;exécution maximale attendue du processus statique de déploiement (en secondes).

- Valeur par défaut : `900`
- Accepte une valeur

### `--symlink-locale`

Créez des liens symboliques pour les fichiers de ces paramètres régionaux, qui sont transmis pour déploiement, mais n’ont aucune personnalisation.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--content-version`

Une version personnalisée du contenu statique peut être utilisée si vous exécutez le déploiement sur plusieurs nœuds afin de vous assurer que la version du contenu statique est identique et que la mise en cache fonctionne correctement.

- Nécessite une valeur

### `--refresh-content-version-only`

L’actualisation de la version de contenu statique uniquement peut être utilisée pour actualiser le contenu statique dans le cache du navigateur et le cache du réseau CDN.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-javascript`

Ne déployez pas de fichiers JavaScript.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-js-bundle`

Ne déployez pas de fichiers de bundle JavaScript.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-css`

Ne déployez pas de fichiers CSS.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-less`

Ne déployez pas de fichiers LESS.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-images`

Ne déployez pas d’images.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-fonts`

Ne déployez pas de fichiers de polices.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-html`

Ne déployez pas de fichiers de HTML.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-misc`

Ne déployez pas de fichiers d’autres types (.md, .jbf, .csv, etc.).

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-html-minify`

Ne minimisez pas les fichiers de HTML.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-parent`

Ne compilez pas les thèmes parents. Pris en charge uniquement dans les stratégies rapides et standard.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:store-config:set`

Installe la configuration du magasin. Obsolète depuis la version 2.2.0. Utilisez plutôt config:set .

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--base-url`

URL vers laquelle le magasin est censé être disponible. Obsolète, utilisez config:set avec le chemin web/unsecure/base_url

- Nécessite une valeur

### `--language`

Code de langue par défaut. Obsolète, utilisez config:set avec le chemin general/locale/code

- Nécessite une valeur

### `--timezone`

Code de fuseau horaire par défaut. Obsolète, utilisez config:set avec le chemin general/locale/timezone

- Nécessite une valeur

### `--currency`

Code de devise par défaut. Obsolète, utilisez config:set avec le chemin currency/options/base, currency/options/default et currency/options/allow .

- Nécessite une valeur

### `--use-rewrites`

Utiliser les réécritures. Obsolète, utilisez config:set avec le chemin web/seo/use_rewrites

- Nécessite une valeur

### `--use-secure`

Utilisez des URL sécurisées. Activez cette option uniquement si SSL est disponible. Obsolète, utiliser config:set avec le chemin web/secure/use_in_frontend

- Nécessite une valeur

### `--base-url-secure`

URL de base de la connexion SSL. Obsolète, utilisez config:set avec le chemin web/secure/base_url

- Nécessite une valeur

### `--use-secure-admin`

Exécutez l’interface d’administration avec SSL. Obsolète, utilisez config:set avec le chemin web/secure/use_in_adminhtml

- Nécessite une valeur

### `--admin-use-security-key`

Si la fonction « clé de sécurité » doit être utilisée dans les formulaires et les URL d’administration de Magento. Obsolète, utilisez config:set avec le chemin admin/security/use_form_key

- Nécessite une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:uninstall`

Désinstalle l’application du Magento

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `setup:upgrade`

Met à niveau l’application du Magento, les données de la base de données et le schéma

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--keep-generated`

Empêche la suppression des fichiers générés. Nous déconseillons d’utiliser cette option, sauf lors du déploiement en production. Pour plus d&#39;informations, consultez votre intégrateur système ou votre administrateur.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--convert-old-scripts`

Permet de convertir d’anciens scripts (InstallSchema, UpgradeSchema) au format db_schema.xml

- Valeur par défaut : `false`
- Accepte une valeur

### `--safe-mode`

Installation sûre du Magento avec des vidages sur les opérations destructives, comme l&#39;enlèvement de colonne

- Accepte une valeur

### `--data-restore`

Restaurer les données supprimées des images mémoire

- Accepte une valeur

### `--dry-run`

L’installation du Magento sera exécutée en mode d’exécution d’essai

- Valeur par défaut : `false`
- Accepte une valeur

### `--magento-init-params`

Ajoutez à n’importe quelle commande pour personnaliser les paramètres d’initialisation du Magento. Par exemple : « MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache »

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `store:list`

Affiche la liste des magasins

```bash
bin/magento store:list
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `store:website:list`

Affiche la liste des sites web

```bash
bin/magento store:website:list
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `support:backup:code`

Création d’une sauvegarde de code

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

### `--name`

Nom du vidage

- Accepte une valeur

### `--output`, `-o`

Chemin de sortie

- Accepte une valeur

### `--logs`, `-l`

Inclure les logs

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `support:backup:db`

Créer une sauvegarde de base de données

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

### `--name`

Nom du vidage

- Accepte une valeur

### `--output`, `-o`

Chemin de sortie

- Accepte une valeur

### `--logs`, `-l`

Inclure les logs

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ignore-sanitize`, `-i`

Ignorer l’assainissement

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `support:utility:check`

Vérifier les utilitaires de sauvegarde requis

```bash
bin/magento support:utility:check [--hide-paths]
```

### `--hide-paths`

Vérifier uniquement les utilitaires de console requis

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `support:utility:paths`

Création d’une liste de chemins d’accès aux utilitaires

```bash
bin/magento support:utility:paths [-f|--force]
```

### `--force`, `-f`

Forcer

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `theme:uninstall`

Désinstalle le thème

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```


### `theme`

Chemin du thème. Le chemin d’accès au thème doit être spécifié comme chemin d’accès complet, à savoir zone/fournisseur/nom. Par exemple, frontend/Magento/blank

- Valeur par défaut : `[]`

- Obligatoire
- Tableau

### `--backup-code`

Effectuer une sauvegarde du code (à l’exclusion des fichiers temporaires)

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--clear-static-content`, `-c`

Effacez les fichiers d’affichage statique générés.

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `varnish:vcl:generate`

Génère le code VCL de vernis et le répercute sur la ligne de commande

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

### `--access-list`

Liste d’accès des adresses IP pouvant purger le vernis

- Valeur par défaut : `localhost`
- Nécessite une valeur

### `--backend-host`

Hôte du serveur principal Web

- Valeur par défaut : `localhost`
- Nécessite une valeur

### `--backend-port`

Port du serveur principal web

- Valeur par défaut : `8080`
- Nécessite une valeur

### `--export-version`

Version du fichier Vernis

- Valeur par défaut : `6`
- Nécessite une valeur

### `--grace-period`

Délai de grâce en secondes

- Valeur par défaut : `300`
- Nécessite une valeur

### `--input-file`

Fichier d’entrée à partir duquel générer la VCI

- Nécessite une valeur

### `--output-file`

Chemin d&#39;accès au fichier d&#39;écriture de vcl

- Nécessite une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `webhooks:dev:run`

Exécute un webhook enregistré à des fins de développement.

```bash
bin/magento webhooks:dev:run <name> <payload>
```


### `name`

Nom du Webhook

- Obligatoire

### `payload`

Payload webhook au format JSON

- Obligatoire

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `webhooks:generate:module`

Générer des modules externes en fonction des enregistrements webhook

```bash
bin/magento webhooks:generate:module
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `webhooks:info`

Renvoie la payload du webhook spécifié.

```bash
bin/magento webhooks:info [--depth [DEPTH]] [--] <webhook-name> [<webhook-type>]
```


### `webhook-name`

Nom de la méthode Webhook

- Obligatoire

### `webhook-type`

Type de Webhook (avant, après)

- Valeur par défaut : `before`


### `--depth`

Nombre de niveaux dans la payload du webhook à renvoyer

- Valeur par défaut : `3`
- Accepte une valeur

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `webhooks:list`

Affiche la liste des Webhooks abonnés

```bash
bin/magento webhooks:list
```

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur


## `webhooks:list:all`

Renvoie une liste des noms de méthode webhook pris en charge pour le module spécifié

```bash
bin/magento webhooks:list:all <module_name>
```


### `module_name`

Nom du module

- Obligatoire

### `--help`, `-h`

Afficher l’aide pour la commande donnée. Si aucune commande n&#39;est fournie, afficher l&#39;aide pour le \&lt;info>list\&lt;/info> commande

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--quiet`, `-q`

Ne pas générer de message

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--verbose`, `-v|-vv|-vvv`

Augmentez la verbosité des messages : 1 pour une sortie normale, 2 pour une sortie plus détaillée et 3 pour le débogage

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--version`, `-V`

Afficher cette version de l&#39;application

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--ansi`

Forcer (ou désactiver —no-ansi) la sortie ANSI

- N’accepte aucune valeur

### `--no-ansi`

Ignorer l’option « —ansi »

- Valeur par défaut : `false`
- N’accepte aucune valeur

### `--no-interaction`, `-n`

Ne pas poser de question interactive

- Valeur par défaut : `false`
- N’accepte aucune valeur
