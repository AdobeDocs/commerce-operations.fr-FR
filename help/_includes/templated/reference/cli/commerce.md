---
source-git-commit: 23d55385046de18b238c90f6a99be692f1ce7561
workflow-type: tm+mt
source-wordcount: '19853'
ht-degree: 0%

---
# magento-cloud (Adobe Commerce sur l’infrastructure cloud)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Version**: 1.40.0

Cette référence contient 129 commandes disponibles via le `magento-cloud` outil de ligne de commande.
La liste initiale est générée automatiquement à l’aide de la fonction `magento-cloud list` à l’édition.

>[!NOTE]
>
>Cette référence est générée à partir du code base de l’application. Pour modifier le contenu, vous pouvez mettre à jour le code source de l’implémentation de la commande correspondante dans le [codebase](https://github.com/magento) et envoyer vos modifications pour révision. Une autre méthode consiste à _Donnez-nous vos commentaires_ (trouvez le lien en haut à droite). Pour obtenir des instructions sur les contributions, voir [Contributions au code](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_completion`

point d’extrémité BASH.

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

### `--generate-hook`, `-g`

Générez le code BASH qui configure la fin de cette application.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--program`, `-p`

Nom du programme qui doit déclencher l’achèvement &lt;comment>(chemin d’accès absolu à l’application par défaut)&lt;/comment>.

- Nécessite une valeur

### `--multiple`, `-m`

Le point d’extension généré peut être utilisé pour plusieurs applications.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--shell-type`

Définissez le type de shell (zsh ou bash). Dans le cas contraire, cette valeur est déterminée automatiquement.

- Accepte une valeur


## `bot`

Cloud Robot Magento

```bash
magento-cloud bot [--party] [--parrot]
```

### `--party`



- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--parrot`



- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `clear-cache`

Effacer le cache de l’interface de ligne de commande

```bash
magento-cloud clear-cache
```


```bash
clearcache
```


```bash
cc
```

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `decode`

Décodez une chaîne codée telle que MAGENTO_CLOUD_VARIABLES

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```


### `value`

La valeur de la variable à décoder

- Obligatoire

### `--property`, `-P`

La propriété à afficher dans la variable

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `docs`

Ouvrir la documentation en ligne

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```


### `search`

Termes de recherche

- Valeur par défaut : `[]`

- Tableau

### `--browser`

Navigateur à utiliser pour ouvrir l’URL. Définissez 0 pour aucun.

- Nécessite une valeur

### `--pipe`

Extrayez l’URL vers stdout.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `help`

Affiche l’aide d’une commande

```bash
help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

Nom de la commande

- Valeur par défaut : `help`


### `--format`

Format de sortie (txt, xml, json ou md)

- Valeur par défaut : `txt`
- Nécessite une valeur

### `--raw`

Pour générer l’aide de la commande brute

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `legacy-migrate`

Migration depuis la structure de fichiers héritée

```bash
magento-cloud legacy-migrate [--no-backup]
```

### `--no-backup`

Ne créez pas de sauvegarde du projet.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `list`

Commandes Listes

```bash
list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
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
- Nécessite une valeur


## `multi`

Exécution d’une commande sur plusieurs projets

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd>
```


### `cmd`

Commande à exécuter

- Obligatoire

### `--projects`, `-p`

Une liste d’ID de projet, séparés par des virgules et/ou un espace blanc

- Nécessite une valeur

### `--continue`

Poursuivre l’exécution des commandes même en cas d’exception

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--sort`

Une propriété par laquelle trier la liste des options de projet

- Valeur par défaut : `title`
- Nécessite une valeur

### `--reverse`

Inverser l’ordre des options du projet

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `web`

Ouverture de l’interface utilisateur web

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

### `--browser`

Navigateur à utiliser pour ouvrir l’URL. Définissez 0 pour aucun.

- Nécessite une valeur

### `--pipe`

Extrayez l’URL vers stdout.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `welcome`

Bienvenue dans Magento Cloud

```bash
magento-cloud welcome
```

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `winky`



```bash
magento-cloud winky
```

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `activity:cancel`

Annulation d’une activité

```bash
magento-cloud activity:cancel [--type TYPE] [--exclude-type EXCLUDE-TYPE] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

ID d’activité. La valeur par défaut est l’activité annulable la plus récente.


### `--type`

Filtrer par type (lors de la sélection d’une activité par défaut). Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--exclude-type`

Exclure par type (lors de la sélection d’une activité par défaut). Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--all`, `-a`

Vérifier les activités récentes sur tous les environnements (lors de la sélection d’une activité par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `activity:get`

Affichage d’informations détaillées sur une seule activité

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```


### `id`

ID d’activité. La valeur par défaut est l’activité la plus récente.


### `--property`, `-P`

La propriété à afficher

- Nécessite une valeur

### `--type`

Filtrer par type (lors de la sélection d’une activité par défaut). Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--exclude-type`

Exclure par type (lors de la sélection d’une activité par défaut). Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--state`

Filtrer par état (lors de la sélection d’une activité par défaut) : in_progress, en attente, terminé ou annulé. Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--result`

Filtrer par résultat (lors de la sélection d&#39;une activité par défaut) : succès ou échec

- Nécessite une valeur

### `--incomplete`, `-i`

N’incluez que les activités incomplètes (lors de la sélection d’une activité par défaut). Ceci est un raccourci pour &lt;info>—state=in_progress,pending&lt;/info>

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--all`, `-a`

Vérifier les activités récentes sur tous les environnements (lors de la sélection d’une activité par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `activity:list`

Obtention d’une liste des activités pour un environnement ou un projet

```bash
magento-cloud activity:list [-t|--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```


```bash
activities
```


```bash
act
```

### `--type`, `-t`

Filtrer les activités par type Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--exclude-type`, `-x`

Exclure les activités par type. Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--limit`

Limiter le nombre de résultats affichés

- Valeur par défaut : `10`
- Nécessite une valeur

### `--start`

Seules les activités créées avant cette date seront répertoriées.

- Nécessite une valeur

### `--state`

Filtrage des activités par état : in_progress, en attente, terminé ou annulé. Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--result`

Filtrer les activités par résultat : succès ou échec

- Nécessite une valeur

### `--incomplete`, `-i`

Ne répertorier que les activités incomplètes

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--all`, `-a`

Liste des activités dans tous les environnements

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `activity:log`

Afficher le journal d’une activité

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

ID d’activité. La valeur par défaut est l’activité la plus récente.


### `--refresh`

Intervalle d’actualisation de l’activité (secondes). Définissez cette variable sur 0 pour désactiver l’actualisation.

- Valeur par défaut : `3`
- Nécessite une valeur

### `--timestamps`, `-t`

Afficher un horodatage en regard de chaque message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--type`

Filtrer par type (lors de la sélection d’une activité par défaut). Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--exclude-type`

Exclure par type (lors de la sélection d’une activité par défaut). Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--state`

Filtrer par état (lors de la sélection d’une activité par défaut) : in_progress, en attente, terminé ou annulé. Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--result`

Filtrer par résultat (lors de la sélection d&#39;une activité par défaut) : succès ou échec

- Nécessite une valeur

### `--incomplete`, `-i`

N’incluez que les activités incomplètes (lors de la sélection d’une activité par défaut). Ceci est un raccourci pour &lt;info>—state=in_progress,pending&lt;/info>

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--all`, `-a`

Vérifier les activités récentes sur tous les environnements (lors de la sélection d’une activité par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `api:curl`

Exécution d’une requête cURL authentifiée sur l’API Cloud Magento

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [--] [<path>]
```


### `path`

Chemin de l’API


### `--request`, `-X`

La méthode de requête à utiliser

- Nécessite une valeur

### `--data`, `-d`

Données à envoyer

- Nécessite une valeur

### `--include`, `-i`

Inclure les en-têtes dans la sortie

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--head`, `-I`

Récupération des en-têtes uniquement

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--disable-compression`

N’utilisez pas l’indicateur curl —compressé

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--enable-glob`

Activez l’extension métacaractère curl (supprimez l’indicateur —globoff ).

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--fail`, `-f`

Échec sans sortie sur une réponse d’erreur

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--header`, `-H`

En-tête(s) supplémentaire(s)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `app:config-get`

Affichage de la configuration d’une application

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

### `--property`, `-P`

La propriété de configuration à afficher

- Nécessite une valeur

### `--refresh`

Actualisation ou non du cache

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--identity-file`, `-i`

[Option obsolète, non utilisée]

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `app:list`

Liste des applications dans le projet

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```


```bash
apps
```

### `--refresh`

Actualisation ou non du cache

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `auth:api-token-login`

Connexion à Magento Cloud à l’aide d’un jeton API

```bash
magento-cloud auth:api-token-login
```

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `auth:browser-login`

Connexion à Magento Cloud via un navigateur

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```


```bash
login
```

### `--force`, `-f`

Connectez-vous à nouveau, même si vous êtes déjà connecté.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--browser`

Navigateur à utiliser pour ouvrir l’URL. Définissez 0 pour aucun.

- Nécessite une valeur

### `--pipe`

Extrayez l’URL vers stdout.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `auth:info`

Afficher les informations de votre compte

```bash
magento-cloud auth:info [--no-auto-login] [-P|--property PROPERTY] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<property>]
```


### `property`

Propriété du compte à afficher


### `--no-auto-login`

Ignore la connexion automatique. Aucun résultat ne sera affiché s’il n’est pas connecté et le code de sortie sera 0, en supposant aucune autre erreur.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--property`, `-P`

Propriété du compte à afficher (syntaxe alternative)

- Nécessite une valeur

### `--refresh`

Actualisation ou non du cache

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `auth:logout`

Déconnexion de Magento Cloud

```bash
magento-cloud logout [-a|--all] [--other]
```


```bash
logout
```

### `--all`, `-a`

Déconnexion de toutes les sessions locales

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--other`

Déconnexion à partir d’autres sessions locales

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLÈTE ]&lt;/> Connexion à Magento Cloud à l’aide d’un nom d’utilisateur et d’un mot de passe

```bash
magento-cloud auth:password-login
```


```bash
auth:login
```

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `auth:token`

Obtention d’un jeton d’accès OAuth 2 pour les demandes aux API Cloud Magento

```bash
magento-cloud auth:token
```

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `blackfire:setup`

Configuration de l’intégration de Blackfire.io pour le projet

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

### `--server_id`

ID du serveur

- Nécessite une valeur

### `--server_token`

Jeton de serveur

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `certificate:add`

Ajout d’un certificat SSL au projet

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

### `--cert`

Chemin d’accès au fichier de certificat

- Nécessite une valeur

### `--key`

Le chemin d’accès au fichier de clé privée du certificat

- Nécessite une valeur

### `--chain`

Chemin d’accès au fichier de chaîne de certificats

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `certificate:delete`

Suppression d’un certificat du projet

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <id>
```


### `id`

L’ID de certificat (ou le début de celui-ci)

- Obligatoire

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `certificate:get`

Affichage d’un certificat

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] <id>
```


### `id`

L’ID de certificat (ou le début de celui-ci)

- Obligatoire

### `--property`, `-P`

La propriété de certificat à afficher

- Nécessite une valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `certificate:list`

Liste des certificats de projet

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```


```bash
certificates
```


```bash
certs
```

### `--domain`

Filtrage par nom de domaine (recherche non sensible à la casse)

- Nécessite une valeur

### `--exclude-domain`

Exclure des certificats, par nom de domaine (recherche non sensible à la casse)

- Nécessite une valeur

### `--issuer`

Filtrage par émetteur

- Nécessite une valeur

### `--only-auto`

Afficher uniquement les certificats configurés automatiquement

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-auto`

Afficher uniquement les certificats ajoutés manuellement

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--ignore-expiry`

Afficher les certificats expirés et non expirés

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--only-expired`

Afficher uniquement les certificats expirés

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-expired`

Afficher uniquement les certificats non expirés (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--pipe-domains`

Ne renvoient qu’une liste de noms de domaine couverts par les certificats

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `commit:get`

Afficher les détails de validation

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<commit>]
```


### `commit`

La validation SHA. Cela peut également accepter les suffixes &quot;HEAD&quot; et caret (^) ou tilde (~) pour les validations parentes.

- Valeur par défaut : `HEAD`


### `--property`, `-P`

La propriété commit à afficher.

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--format`

OBSOLÈTE

- Nécessite une valeur

### `--columns`

OBSOLÈTE

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

OBSOLÈTE

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `commit:list`

Validation de liste

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```


```bash
commits
```


### `commit`

SHA de validation Git de départ. Cela peut également accepter les suffixes &quot;HEAD&quot; et caret (^) ou tilde (~) pour les validations parentes.


### `--limit`

Nombre de validations à afficher.

- Valeur par défaut : `10`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `db:dump`

Créer un vidage local de la base distante

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```


```bash
sql-dump
```


```bash
environment:sql-dump
```

### `--schema`

Le schéma à vider. Omettez d’utiliser le schéma par défaut (généralement &quot;main&quot;).

- Nécessite une valeur

### `--file`, `-f`

Un nom de fichier personnalisé pour la sauvegarde

- Nécessite une valeur

### `--directory`, `-d`

Un répertoire personnalisé pour la vidage

- Nécessite une valeur

### `--gzip`, `-z`

Compresser la vidure à l’aide de gzip

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--timestamp`, `-t`

Ajouter un horodatage au nom de fichier de vidage

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--stdout`, `-o`

Sortie à STDOUT au lieu d’un fichier

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--table`

Tableau(s) à inclure

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--exclude-table`

Tableau(s) à exclure

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--schema-only`

vidage des schémas uniquement, sans données

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--charset`

Encodage du jeu de caractères pour le vidage

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--relationship`, `-r`

Relation de service à utiliser

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `db:size`

Estimation de l’utilisation du disque d’une base de données

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

### `--bytes`, `-B`

Afficher les tailles en octets.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--cleanup`, `-C`

Vérifiez si les tableaux peuvent être nettoyés et affichez-moi des recommandations (InnoDb uniquement).

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--relationship`, `-r`

Relation de service à utiliser

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `db:sql`

Exécution SQL sur la base distante

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```


```bash
sql
```


```bash
environment:sql
```


### `query`

Instruction SQL à exécuter


### `--raw`

Générer une sortie brute non tabulaire

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--schema`

Le schéma à utiliser. Omettez d’utiliser le schéma par défaut (généralement &quot;main&quot;). Transmettez une chaîne vide pour ne pas utiliser de schéma.

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--relationship`, `-r`

Relation de service à utiliser

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `domain:add`

Ajouter un nouveau domaine au projet

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nom de domaine

- Obligatoire

### `--cert`

Chemin d’accès au fichier de certificat pour ce domaine

- Nécessite une valeur

### `--key`

Le chemin d’accès au fichier de clé privée pour le certificat fourni.

- Nécessite une valeur

### `--chain`

Le chemin d’accès au fichier ou aux fichiers de la chaîne de certificat pour le certificat fourni

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `domain:delete`

Suppression d’un domaine du projet

```bash
magento-cloud domain:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nom de domaine

- Obligatoire

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `domain:get`

Affichage des informations détaillées d’un domaine

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```


### `name`

Nom de domaine


### `--property`, `-P`

Propriété de domaine à afficher

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `domain:list`

Obtention d’une liste de tous les domaines

```bash
magento-cloud domains [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```


```bash
domains
```

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `domain:update`

Mettre à jour un domaine

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nom de domaine

- Obligatoire

### `--cert`

Chemin d’accès au fichier de certificat pour ce domaine

- Nécessite une valeur

### `--key`

Le chemin d’accès au fichier de clé privée pour le certificat fourni.

- Nécessite une valeur

### `--chain`

Le chemin d’accès au fichier ou aux fichiers de la chaîne de certificat pour le certificat fourni

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:activate`

Activation d’un environnement

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


### `environment`

Environnement(s) à activer

- Valeur par défaut : `[]`

- Tableau

### `--parent`

Définition d’un nouveau parent d’environnement avant activation

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:branch`

Branchement d’un environnement

```bash
magento-cloud branch [--title TITLE] [--type TYPE] [--force] [--no-clone-parent] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```


```bash
branch
```


### `id`

ID (nom de branche) du nouvel environnement


### `parent`

Parent du nouvel environnement


### `--title`

Titre du nouvel environnement

- Nécessite une valeur

### `--type`

Type du nouvel environnement

- Nécessite une valeur

### `--force`

Créez un environnement même si la branche ne peut pas être extraite localement

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-clone-parent`

Ne pas cloner les données de la branche parente

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:checkout`

Vérification d’un environnement

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```


```bash
checkout
```


### `id`

L’identifiant de l’environnement à extraire. Par exemple : &quot;sprint2&quot;


### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:curl`

Exécution d’une requête cURL authentifiée sur l’API d’un environnement

```bash
magento-cloud environment:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

Chemin de l’API


### `--request`, `-X`

La méthode de requête à utiliser

- Nécessite une valeur

### `--data`, `-d`

Données à envoyer

- Nécessite une valeur

### `--include`, `-i`

Inclure les en-têtes dans la sortie

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--head`, `-I`

Récupération des en-têtes uniquement

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--disable-compression`

N’utilisez pas l’indicateur curl —compressé

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--enable-glob`

Activez l’extension métacaractère curl (supprimez l’indicateur —globoff ).

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--fail`, `-f`

Échec sans sortie sur une réponse d’erreur

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--header`, `-H`

En-tête(s) supplémentaire(s)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:delete`

Suppression d’un environnement

```bash
magento-cloud environment:delete [--delete-branch] [--no-delete-branch] [--inactive] [--merged] [--type TYPE] [--exclude EXCLUDE] [--exclude-type EXCLUDE-TYPE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


```bash
environment:deactivate
```


### `environment`

Environnement(s) à supprimer. Le caractère % peut être utilisé comme caractère générique. Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`

- Tableau

### `--delete-branch`

Suppression de la ou des branches Git distantes

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-delete-branch`

Ne supprimez pas la ou les branches Git distantes

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--inactive`

Suppression de tous les environnements inactifs

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--merged`

Suppression de tous les environnements fusionnés

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--type`

Type(s) d’environnement dont la suppression doit être effectuée Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces blancs.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--exclude`

Environnement(s) à ne pas supprimer. Le caractère % peut être utilisé comme caractère générique. Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--exclude-type`

Type(s) d’environnement dont la suppression est obligatoire Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces blancs.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:http-access`

Mise à jour des paramètres d’accès HTTP pour un environnement

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```


```bash
httpaccess
```

### `--access`

Restriction d’accès au format &quot;permission:address&quot;. Utilisez 0 pour effacer toutes les adresses.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--auth`

Informations d’identification HTTP Basic auth au format &quot;nom d’utilisateur:mot de passe&quot;. Utilisez 0 pour effacer toutes les informations d’identification.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--enabled`

Si le contrôle d’accès doit être activé : 1 pour activer, 0 pour désactiver

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:info`

Lecture ou définition des propriétés d’un environnement

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```


```bash
environment:metadata
```


### `property`

Nom de la propriété


### `value`

Définir une nouvelle valeur pour la propriété


### `--refresh`

Actualisation ou non du cache

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:init`

Initialisation d’un environnement à partir d’un référentiel Git public

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```


### `url`

URL d’un référentiel Git

- Obligatoire

### `--profile`

Nom du profil

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:list`

Obtention d’une liste des environnements

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--type TYPE] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```


```bash
environments
```


```bash
env
```

### `--no-inactive`, `-I`

Ne pas afficher les environnements inactifs

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--pipe`

Générer une liste simple d’identifiants d’environnement.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--refresh`

Actualisation ou non de la liste.

- Valeur par défaut : `1`
- Nécessite une valeur

### `--sort`

Propriété à trier par

- Valeur par défaut : `title`
- Nécessite une valeur

### `--reverse`

Tri dans l’ordre inverse (décroissant)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--type`

Vous pouvez filtrer la liste par type d&#39;environnement. Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:logs`

Lecture des journaux d’un environnement

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [--] [<type>]
```


```bash
log
```


```bash
logs
```


### `type`

Le type de journal, par exemple &quot;access&quot; ou &quot;error&quot;


### `--lines`

Le nombre de lignes à afficher

- Valeur par défaut : `100`
- Nécessite une valeur

### `--tail`

Quitter le journal en continu

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--worker`

Nom du travailleur

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:merge`

Fusionner un environnement

```bash
magento-cloud merge [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```


```bash
merge
```


### `environment`

Environnement à fusionner


### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:push`

Push code to a environment

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--branch] [--parent PARENT] [--type TYPE] [--no-clone-parent] [-W|--no-wait] [--wait] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```


```bash
push
```


### `source`

Référence source : un nom de branche ou un hachage de validation ;

- Valeur par défaut : `HEAD`


### `--target`

Nom de la branche cible

- Nécessite une valeur

### `--force`, `-f`

Autoriser des mises à jour non rapides

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--force-with-lease`

Autoriser les mises à jour à transfert rapide, si la branche de suivi à distance est à jour

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--set-upstream`, `-u`

Définir l’environnement cible comme amont pour la branche source

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--activate`

Activez l’environnement avant d’effectuer des opérations

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--branch`

OBSOLÈTE : alias de —activate

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--parent`

Définissez le nouveau parent d’environnement (utilisé uniquement avec —activate).

- Nécessite une valeur

### `--type`

Définissez le type d’environnement (utilisé uniquement avec —activate ).

- Nécessite une valeur

### `--no-clone-parent`

Ne pas cloner les données de la branche parente (utilisé uniquement avec —activate)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:redeploy`

Redéployer un environnement

```bash
magento-cloud redeploy [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```


```bash
redeploy
```

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:relationships`

Afficher les relations d’un environnement

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```


```bash
relationships
```


### `environment`

L&#39;environnement


### `--property`, `-P`

La propriété de relation à afficher

- Nécessite une valeur

### `--refresh`

Actualisation ou non des relations

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:scp`

Copie de fichiers vers et depuis l’environnement actuel à l’aide de scp

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```


```bash
scp
```


### `files`

Fichiers à copier. Utilisez la télécommande : pour définir des emplacements distants.

- Valeur par défaut : `[]`

- Tableau

### `--recursive`, `-r`

Copier récursivement des répertoires entiers

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--worker`

Nom du travailleur

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:set-remote`

Définir l’environnement distant à mapper à une branche

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```


### `environment`

Nom de la machine de l’environnement. Définissez cette variable sur 0 pour supprimer le mappage d’une branche.

- Obligatoire

### `branch`

La branche Git à mapper (par défaut la branche actuelle)


### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:ssh`

SSH vers l’environnement actuel

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```


```bash
ssh
```


### `cmd`

Commande à exécuter sur l’environnement.

- Valeur par défaut : `[]`

- Tableau

### `--pipe`

Ne sortez que l’URL SSH.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--all`

Sortez toutes les URL SSH (pour chaque application).

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--worker`

Nom du travailleur

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:synchronize`

Synchroniser le code et/ou les données d’un environnement avec son parent

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```


```bash
sync
```


### `synchronize`

Eléments à synchroniser : &quot;code&quot;, &quot;données&quot; ou les deux

- Valeur par défaut : `[]`

- Tableau

### `--rebase`

Synchroniser le code en rebasant au lieu de fusionner

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:url`

Obtention des URL publiques d’un environnement

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```


```bash
url
```

### `--primary`, `-1`

Ne renvoie que l’URL de l’itinéraire Principal

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--browser`

Navigateur à utiliser pour ouvrir l’URL. Définissez 0 pour aucun.

- Nécessite une valeur

### `--pipe`

Extrayez l’URL vers stdout.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `environment:xdebug`

Ouvrir un tunnel vers Xdebug sur l’environnement

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```


```bash
xdebug
```

### `--port`

Le port local

- Valeur par défaut : `9000`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--worker`

Nom du travailleur

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `integration:activity:get`

Affichage d’informations détaillées sur une seule activité d’intégration

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```


### `integration`

Identifiant d’intégration. Laissez vide pour effectuer une sélection dans une liste.


### `activity`

ID d’activité. La valeur par défaut est l’activité d’intégration la plus récente.


### `--property`, `-P`

La propriété à afficher

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

[Option obsolète, non utilisée]

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `integration:activity:list`

Obtention d’une liste des activités pour une intégration

```bash
magento-cloud i:act [--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```


```bash
i:act
```


```bash
integration:activities
```


### `id`

Identifiant d’intégration. Laissez vide pour effectuer une sélection dans une liste.


### `--type`

Filtrez les activités par type. Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--exclude-type`, `-x`

Exclure les activités par type. Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--limit`

Limiter le nombre de résultats affichés

- Valeur par défaut : `10`
- Nécessite une valeur

### `--start`

Seules les activités créées avant cette date seront répertoriées.

- Nécessite une valeur

### `--state`

Filtrage des activités par état. Si une seule valeur est spécifiée, elle sera divisée par des virgules ou des espaces.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--result`

Filtrage des activités par résultat

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

[Option obsolète, non utilisée]

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `integration:activity:log`

Afficher le journal d’une activité d’intégration

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```


### `integration`

Identifiant d’intégration. Laissez vide pour effectuer une sélection dans une liste.


### `activity`

ID d’activité. La valeur par défaut est l’activité d’intégration la plus récente.


### `--timestamps`, `-t`

Afficher un horodatage en regard de chaque message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

[Option obsolète, non utilisée]

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `integration:add`

Ajout d’une intégration au projet

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

### `--type`

Le type d&#39;intégration (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;webhook&#39;, &#39;health.email&#39;, &#39;health.pagerdevoir&#39;, &#39;health.slack&#39;, &#39;health.webhook&#39;, &#39;script&#39;)

- Nécessite une valeur

### `--base-url`

URL de base de l’installation du serveur

- Nécessite une valeur

### `--username`

Nom d’utilisateur du serveur Bitbucket

- Nécessite une valeur

### `--token`

Un jeton d’accès pour l’intégration

- Nécessite une valeur

### `--key`

Une clé de consommateur OAuth pour Bitbucket

- Nécessite une valeur

### `--secret`

Un secret de consommateur OAuth pour Bitbucket

- Nécessite une valeur

### `--server-project`

Le projet (par ex. &#39;namespace/repo&#39;)

- Nécessite une valeur

### `--repository`

Le référentiel à suivre (par exemple, &#39;propriétaire/référentiel&#39;)

- Nécessite une valeur

### `--build-merge-requests`

GitLab : créer des requêtes de fusion en tant qu’environnements ;

- Valeur par défaut : `true`
- Nécessite une valeur

### `--build-pull-requests`

Créer chaque demande d’extraction en tant qu’environnement

- Valeur par défaut : `true`
- Nécessite une valeur

### `--build-draft-pull-requests`

Création de requêtes d’extraction de brouillons

- Valeur par défaut : `true`
- Nécessite une valeur

### `--build-pull-requests-post-merge`

Créer des requêtes d’extraction en fonction de leur état de post-fusion

- Valeur par défaut : `false`
- Nécessite une valeur

### `--build-wip-merge-requests`

GitLab : créer des requêtes de fusion en cours

- Valeur par défaut : `true`
- Nécessite une valeur

### `--merge-requests-clone-parent-data`

GitLab : données de clone pour les requêtes de fusion

- Valeur par défaut : `true`
- Nécessite une valeur

### `--pull-requests-clone-parent-data`

Cloner les données de l’environnement parent pour les demandes d’extraction

- Valeur par défaut : `true`
- Nécessite une valeur

### `--resync-pull-requests`

Resynchroniser les données de l’environnement des demandes d’extraction sur chaque version

- Valeur par défaut : `false`
- Nécessite une valeur

### `--fetch-branches`

Récupérer toutes les branches à partir de la distante (en tant qu’environnements inactifs)

- Valeur par défaut : `true`
- Nécessite une valeur

### `--prune-branches`

Supprimer les branches qui n’existent pas sur le site distant

- Valeur par défaut : `true`
- Nécessite une valeur

### `--url`

Webhook : URL de réception des données JSON

- Nécessite une valeur

### `--shared-key`

Webhook : la clé secrète partagée JWS ;

- Nécessite une valeur

### `--file`

Nom d’un fichier local qui contient le script à charger.

- Nécessite une valeur

### `--events`

Liste des événements sur lesquels agir, par exemple environment.push

- Valeur par défaut : `*`
- Nécessite une valeur

### `--states`

Liste des états sur lesquels agir, par exemple en attente, en cours, terminé

- Valeur par défaut : `complete`
- Nécessite une valeur

### `--environments`

Les identifiants d’environnement à inclure

- Valeur par défaut : `*`
- Nécessite une valeur

### `--excluded-environments`

Les identifiants d’environnement à exclure

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--from-address`

[Facultatif] Adresse de l’expéditeur personnalisée pour les e-mails d’alerte

- Nécessite une valeur

### `--recipients`

Adresse(s) email(s) du destinataire

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--channel`

Canal Slack

- Nécessite une valeur

### `--routing-key`

Clé de routage PagerDuty

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `integration:delete`

Suppression d’une intégration d’un projet

```bash
magento-cloud integration:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

ID d’intégration. Laissez vide pour effectuer une sélection dans une liste.


### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `integration:get`

Affichage des détails d’une intégration

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<id>]
```


### `id`

Identifiant d’intégration. Laissez vide pour effectuer une sélection dans une liste.


### `--property`, `-P`

La propriété d’intégration à afficher

- Accepte une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `integration:list`

Affichage d’une liste des intégrations de projet

```bash
magento-cloud integrations [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```


```bash
integrations
```

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `integration:update`

Mettre à jour une intégration

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

ID de l’intégration à mettre à jour


### `--type`

Le type d&#39;intégration (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;webhook&#39;, &#39;health.email&#39;, &#39;health.pagerdevoir&#39;, &#39;health.slack&#39;, &#39;health.webhook&#39;, &#39;script&#39;)

- Nécessite une valeur

### `--base-url`

URL de base de l’installation du serveur

- Nécessite une valeur

### `--username`

Nom d’utilisateur du serveur Bitbucket

- Nécessite une valeur

### `--token`

Un jeton d’accès pour l’intégration

- Nécessite une valeur

### `--key`

Une clé de consommateur OAuth pour Bitbucket

- Nécessite une valeur

### `--secret`

Un secret de consommateur OAuth pour Bitbucket

- Nécessite une valeur

### `--server-project`

Le projet (par ex. &#39;namespace/repo&#39;)

- Nécessite une valeur

### `--repository`

Le référentiel à suivre (par exemple, &#39;propriétaire/référentiel&#39;)

- Nécessite une valeur

### `--build-merge-requests`

GitLab : créer des requêtes de fusion en tant qu’environnements ;

- Valeur par défaut : `true`
- Nécessite une valeur

### `--build-pull-requests`

Créer chaque demande d’extraction en tant qu’environnement

- Valeur par défaut : `true`
- Nécessite une valeur

### `--build-draft-pull-requests`

Création de requêtes d’extraction de brouillons

- Valeur par défaut : `true`
- Nécessite une valeur

### `--build-pull-requests-post-merge`

Créer des requêtes d’extraction en fonction de leur état de post-fusion

- Valeur par défaut : `false`
- Nécessite une valeur

### `--build-wip-merge-requests`

GitLab : créer des requêtes de fusion en cours

- Valeur par défaut : `true`
- Nécessite une valeur

### `--merge-requests-clone-parent-data`

GitLab : données de clone pour les requêtes de fusion

- Valeur par défaut : `true`
- Nécessite une valeur

### `--pull-requests-clone-parent-data`

Cloner les données de l’environnement parent pour les demandes d’extraction

- Valeur par défaut : `true`
- Nécessite une valeur

### `--resync-pull-requests`

Resynchroniser les données de l’environnement des demandes d’extraction sur chaque version

- Valeur par défaut : `false`
- Nécessite une valeur

### `--fetch-branches`

Récupérer toutes les branches à partir de la distante (en tant qu’environnements inactifs)

- Valeur par défaut : `true`
- Nécessite une valeur

### `--prune-branches`

Supprimer les branches qui n’existent pas sur le site distant

- Valeur par défaut : `true`
- Nécessite une valeur

### `--url`

Webhook : URL de réception des données JSON

- Nécessite une valeur

### `--shared-key`

Webhook : la clé secrète partagée JWS ;

- Nécessite une valeur

### `--file`

Nom d’un fichier local qui contient le script à charger.

- Nécessite une valeur

### `--events`

Liste des événements sur lesquels agir, par exemple environment.push

- Valeur par défaut : `*`
- Nécessite une valeur

### `--states`

Liste des états sur lesquels agir, par exemple en attente, en cours, terminé

- Valeur par défaut : `complete`
- Nécessite une valeur

### `--environments`

Les identifiants d’environnement à inclure

- Valeur par défaut : `*`
- Nécessite une valeur

### `--excluded-environments`

Les identifiants d’environnement à exclure

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--from-address`

[Facultatif] Adresse de l’expéditeur personnalisée pour les e-mails d’alerte

- Nécessite une valeur

### `--recipients`

Adresse(s) email(s) du destinataire

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--channel`

Canal Slack

- Nécessite une valeur

### `--routing-key`

Clé de routage PagerDuty

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `integration:validate`

Validation d’une intégration existante

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--host HOST] [--] [<id>]
```


### `id`

Identifiant d’intégration. Laissez vide pour effectuer une sélection dans une liste.


### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `local:build`

Créer localement le projet actuel

```bash
magento-cloud build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```


```bash
build
```


### `app`

Spécification des applications à créer

- Valeur par défaut : `[]`

- Tableau

### `--abslinks`, `-a`

Utiliser des liens absolus

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--source`, `-s`

Répertoire source. La valeur par défaut est la racine du projet actuel.

- Nécessite une valeur

### `--destination`, `-d`

La destination, à laquelle la racine web de chaque application sera associée par un lien symbolique. Valeur par défaut : _www

- Nécessite une valeur

### `--copy`, `-c`

Copiez dans un répertoire de build, au lieu de créer un lien symbolique à partir de la source

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--clone`

Utilisation de Git pour cloner l’HEAD actuel dans le répertoire de génération

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--run-deploy-hooks`

Exécuter le déploiement et/ou les hooks post_deploy

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-clean`

Ne pas supprimer les anciennes versions

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-archive`

Ne pas créer ni utiliser d’archive de version

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-backup`

Ne pas sauvegarder le build précédent

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-cache`

Désactiver la mise en cache

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-build-hooks`

N’exécutez pas les crochets après la génération

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-deps`

N’installez pas de dépendances de build localement

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--working-copy`

Drush : utiliser git pour cloner un référentiel de chaque module Drupal plutôt que de simplement télécharger une version ;

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--concurrency`

Drush : définir le nombre de projets simultanés qui seront traités simultanément ;

- Valeur par défaut : `4`
- Nécessite une valeur

### `--lock`

Drush : créer ou mettre à jour un fichier de verrouillage (disponible uniquement avec Drush version 7+) ;

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `local:clean`

Supprimer les anciennes versions de projet

```bash
magento-cloud clean [--keep KEEP] [--max-age MAX-AGE] [--include-active]
```


```bash
clean
```

### `--keep`

Le nombre maximal de versions à conserver

- Valeur par défaut : `5`
- Nécessite une valeur

### `--max-age`

Âge maximum des versions, en secondes. Ignoré si non défini.

- Nécessite une valeur

### `--include-active`

Supprimer également le ou les principaux build

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `local:dir`

Recherche de la racine de projet locale

```bash
magento-cloud dir [<subdir>]
```


```bash
dir
```


### `subdir`

Le sous-répertoire à trouver (&#39;local&#39;, &#39;web&#39; ou &#39;shared&#39;)


### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `mount:download`

Téléchargement de fichiers à partir d’un montage à l’aide de la synchronisation

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

### `--all`, `-a`

Téléchargement depuis toutes les montures

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--mount`, `-m`

Le montage (en tant que chemin relatif à l’application)

- Nécessite une valeur

### `--target`

Répertoire vers lequel les fichiers seront téléchargés. Si —all est utilisé, le chemin de montage est ajouté

- Nécessite une valeur

### `--source-path`

Utilisez le chemin d’accès source du montage (plutôt que le chemin d’accès au montage) comme sous-répertoire de la cible, lorsque —all est utilisé.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--delete`

Suppression des fichiers superflus dans le répertoire cible

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--exclude`

Fichier(s) à exclure du téléchargement (modèle)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--include`

Fichier(s) à inclure dans le téléchargement (modèle)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--refresh`

Actualisation ou non du cache

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--worker`

Nom du travailleur

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `mount:list`

Obtention d’une liste de montages

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```


```bash
mounts
```

### `--paths`

Sortie des chemins de montage uniquement (une par ligne)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--refresh`

Actualisation ou non du cache

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--worker`

Nom du travailleur

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `mount:size`

Vérification de l’utilisation des supports sur le disque

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

### `--bytes`, `-B`

Afficher les tailles en octets

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--refresh`

Actualisation du cache

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--worker`

Nom du travailleur

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `mount:upload`

Chargement de fichiers sur un montage à l’aide de la synchronisation

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

### `--source`

Répertoire contenant les fichiers à charger

- Nécessite une valeur

### `--mount`, `-m`

Le montage (en tant que chemin relatif à l’application)

- Nécessite une valeur

### `--delete`

Suppression des fichiers superflus dans le montage

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--exclude`

Fichier(s) à exclure du transfert (modèle)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--include`

Fichier(s) à inclure dans le transfert (modèle)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--refresh`

Actualisation ou non du cache

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--worker`

Nom du travailleur

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `project:clear-build-cache`

Effacer le cache de création d’un projet

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT] [--host HOST]
```

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `project:curl`

Exécution d’une requête cURL authentifiée sur l’API d’un projet

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [-p|--project PROJECT] [--host HOST] [--] [<path>]
```


### `path`

Chemin de l’API


### `--request`, `-X`

La méthode de requête à utiliser

- Nécessite une valeur

### `--data`, `-d`

Données à envoyer

- Nécessite une valeur

### `--include`, `-i`

Inclure les en-têtes dans la sortie

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--head`, `-I`

Récupération des en-têtes uniquement

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--disable-compression`

N’utilisez pas l’indicateur curl —compressé

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--enable-glob`

Activez l’extension métacaractère curl (supprimez l’indicateur —globoff ).

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--fail`, `-f`

Échec sans sortie sur une réponse d’erreur

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--header`, `-H`

En-tête(s) supplémentaire(s)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `project:get`

Clonage local d’un projet

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [--host HOST] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```


```bash
get
```


### `project`

ID de projet


### `directory`

Répertoire vers lequel effectuer le clonage. Valeur par défaut du titre du projet.


### `--environment`, `-e`

ID d’environnement à cloner. La valeur par défaut est le projet ou le premier environnement disponible.

- Nécessite une valeur

### `--depth`

Créez un clone superficiel : limiter le nombre de validations dans l’historique ;

- Nécessite une valeur

### `--build`

Création du projet après clonage

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `project:info`

Lecture ou définition des propriétés d’un projet

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```


```bash
project:metadata
```


### `property`

Nom de la propriété


### `value`

Définir une nouvelle valeur pour la propriété


### `--refresh`

Actualisation ou non du cache

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `project:list`

Obtenir la liste de tous les projets principaux

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--page PAGE] [--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```


```bash
projects
```


```bash
pro
```

### `--pipe`

Permet de générer une liste simple d’ID de projet. Cela désactive la pagination.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--host`

Filtrer par nom d’hôte de région (correspondance exacte)

- Nécessite une valeur

### `--title`

Filtrage par titre (recherche non sensible à la casse)

- Nécessite une valeur

### `--my`

Afficher uniquement les projets que vous possédez

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--refresh`

Actualisation ou non de la liste

- Valeur par défaut : `1`
- Nécessite une valeur

### `--sort`

Propriété à trier par

- Valeur par défaut : `title`
- Nécessite une valeur

### `--reverse`

Tri dans l’ordre inverse (décroissant)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--page`

Numéro de page (à partir de 1)

- Valeur par défaut : `1`
- Nécessite une valeur

### `--count`

Nombre de projets à afficher par page. La valeur par défaut est basée sur la hauteur du terminal. Utilisez 0 pour désactiver la pagination.

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `project:set-remote`

Définition du projet distant pour le référentiel Git actuel

```bash
magento-cloud project:set-remote [<project>]
```


### `project`

ID de projet


### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLÈTE ]&lt;/> Supprimer une variable d’un projet

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nom de variable

- Obligatoire

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLÈTE ]&lt;/> Afficher la ou les variables d’un projet

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```


```bash
project-variables
```


```bash
pvget
```


```bash
project:variable:list
```


### `name`

Nom de la variable


### `--pipe`

Générer la valeur de variable complète uniquement (un &quot;nom&quot; doit être spécifié)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLÈTE ]&lt;/> Définition d’une variable pour un projet

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name> <value>
```


```bash
pvset
```


### `name`

Nom de variable

- Obligatoire

### `value`

La valeur de la variable

- Obligatoire

### `--json`

Marquer la valeur comme JSON

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-visible-build`

Ne pas exposer cette variable au moment de la création

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no-visible-runtime`

Ne pas exposer cette variable au moment de l’exécution

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `repo:cat`

Lecture d’un fichier dans le référentiel de projet

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] <path>
```


### `path`

Chemin d’accès au fichier

- Obligatoire

### `--commit`, `-c`

La validation SHA. Cela peut également accepter les suffixes &quot;HEAD&quot; et caret (^) ou tilde (~) pour les validations parentes.

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `repo:ls`

Liste des fichiers dans le référentiel du projet

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

Chemin d’accès à un sous-répertoire


### `--directories`, `-d`

Afficher uniquement les répertoires

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--files`, `-f`

Afficher les fichiers uniquement

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--git-style`

Sortie de style similaire à &quot;git ls-tree&quot;

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--commit`, `-c`

La validation SHA. Cela peut également accepter les suffixes &quot;HEAD&quot; et caret (^) ou tilde (~) pour les validations parentes.

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `repo:read`

Lecture d’un répertoire ou d’un fichier dans le référentiel de projet

```bash
magento-cloud read [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<path>]
```


```bash
read
```


### `path`

Chemin d’accès au répertoire ou au fichier


### `--commit`, `-c`

La validation SHA. Cela peut également accepter les suffixes &quot;HEAD&quot; et caret (^) ou tilde (~) pour les validations parentes.

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `route:get`

Affichage d’informations détaillées sur un itinéraire

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```


### `route`

URL d’origine de l’itinéraire


### `--id`

Identifiant d’itinéraire à sélectionner

- Nécessite une valeur

### `--primary`, `-1`

Sélectionner l’itinéraire Principal

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--property`, `-P`

La propriété à afficher

- Nécessite une valeur

### `--refresh`

Contournement du cache des itinéraires

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

[Option obsolète, non utilisée]

- Nécessite une valeur

### `--identity-file`, `-i`

[Option obsolète, non utilisée]

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `route:list`

Liste de toutes les routes d’un environnement

```bash
magento-cloud routes [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<environment>]
```


```bash
routes
```


```bash
environment:routes
```


### `environment`

ID d’environnement


### `--refresh`

Contournement du cache des itinéraires

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `self:install`

Installation ou mise à jour des fichiers de configuration de l’interface de ligne de commande

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```


```bash
local:install
```

### `--shell-type`

Type de shell pour la saisie semi-automatique (bash ou zsh).

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `self:stats`

Affichage des statistiques sur les téléchargements de modules GitHub

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

### `--page`, `-p`

Numéro de page

- Valeur par défaut : `1`
- Nécessite une valeur

### `--count`, `-c`

Résultats par page (max : 100)

- Valeur par défaut : `20`
- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `self:update`

Mettre à jour l’interface de ligne de commande vers la dernière version

```bash
magento-cloud self-update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```


```bash
self-update
```


```bash
update
```

### `--no-major`

Mise à jour uniquement entre les versions mineures ou les versions de correctif

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--unstable`

Mise à jour vers une nouvelle version instable, le cas échéant

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--manifest`

Remplacement de l’emplacement du fichier manifeste

- Nécessite une valeur

### `--current-version`

Remplacer la version actuelle

- Nécessite une valeur

### `--timeout`

Délai d’expiration de la vérification de version

- Valeur par défaut : `30`
- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `service:list`

Liste des services du projet

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```


```bash
services
```

### `--refresh`

Actualisation ou non du cache

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `service:mongo:dump`

Création d’un vidage d’archive binaire de données à partir de MongoDB

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongodump
```

### `--collection`, `-c`

La collection à vider

- Nécessite une valeur

### `--gzip`, `-z`

Compresser la vidure à l’aide de gzip

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--stdout`, `-o`

Sortie à STDOUT au lieu d’un fichier

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--relationship`, `-r`

Relation de service à utiliser

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `service:mongo:export`

Exporter des données depuis MongoDB

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongoexport
```

### `--collection`, `-c`

La collection à exporter

- Nécessite une valeur

### `--jsonArray`

Exportation des données sous la forme d’un tableau JSON unique

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--type`

Le type d&#39;export, par exemple &quot;csv&quot;

- Nécessite une valeur

### `--fields`, `-f`

Champs à exporter

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--relationship`, `-r`

Relation de service à utiliser

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `service:mongo:restore`

Restauration d’un vidage d’archive binaire de données dans MongoDB

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongorestore
```

### `--collection`, `-c`

La collection à restaurer

- Nécessite une valeur

### `--relationship`, `-r`

Relation de service à utiliser

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `service:mongo:shell`

Utilisation du conteneur MongoDB

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongo
```

### `--eval`

Transmettre un fragment JavaScript au conteneur

- Nécessite une valeur

### `--relationship`, `-r`

Relation de service à utiliser

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `service:redis-cli`

Accès à l’interface de ligne de commande Redis

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```


```bash
redis
```


### `args`

Arguments à ajouter à la commande Redis


### `--relationship`, `-r`

Relation de service à utiliser

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Basculer entre les sessions

```bash
magento-cloud session:switch [<id>]
```


### `id`

Le nouvel ID de session


### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `snapshot:create`

Créer un instantané d’un environnement

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```


```bash
backup
```


```bash
backup:create
```


```bash
environment:backup
```


### `environment`

L&#39;environnement


### `--live`

Sauvegarde en direct : n’arrêtez pas l’environnement. Si cette option est définie, l’environnement est exécuté et ouvert aux connexions pendant la sauvegarde. Cela réduit les temps d’arrêt, au risque de sauvegarder les données dans un état incohérent.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `snapshot:list`

Liste des instantanés disponibles d’un environnement

```bash
magento-cloud snapshots [--limit LIMIT] [--start START] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```


```bash
snapshots
```


```bash
backups
```


```bash
backup:list
```

### `--limit`

Limiter le nombre d&#39;instantanés à répertorier

- Nécessite une valeur

### `--start`

[Obsolète] - cette option n’est pas utilisée

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `snapshot:restore`

Restauration d’un instantané d’environnement

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```


```bash
environment:restore
```


```bash
backup:restore
```


### `snapshot`

Nom de l’instantané. La valeur par défaut est la plus récente.


### `--target`

Environnement vers lequel restaurer. Par défaut, l’environnement actuel de l’instantané

- Nécessite une valeur

### `--branch-from`

Si —target n’existe pas encore, cela indique le parent du nouvel environnement.

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Exécution d’une opération source

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```


### `operation`

Nom de l’opération

- Obligatoire

### `--variable`

Variable à définir pendant l’opération, au format &lt;info>type:name=value&lt;/info>

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `ssh-cert:info`

Affichage d’informations sur le certificat SSH actuel

```bash
magento-cloud ssh-cert:info [--no-refresh] [-P|--property PROPERTY] [--date-fmt DATE-FMT]
```

### `--no-refresh`

Ne pas actualiser le certificat s’il n’est pas valide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--property`, `-P`

La propriété de certificat à afficher

- Nécessite une valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `ssh-cert:load`

Génération d’un certificat SSH

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

### `--refresh-only`

Actualisez uniquement le certificat, si nécessaire (n’écrivez pas de configuration SSH).

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--new`

Forcer l’actualisation du certificat

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--new-key`

[Obsolète] Utilisez —new à la place

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `ssh-key:add`

Ajout d’une nouvelle clé SSH

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```


### `path`

Chemin d’accès à une clé publique SSH existante


### `--name`

Nom permettant d’identifier la clé

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `ssh-key:delete`

Suppression d’une clé SSH

```bash
magento-cloud ssh-key:delete [<id>]
```


### `id`

ID de la clé SSH à supprimer


### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `ssh-key:list`

Obtention d’une liste des clés SSH dans votre compte

```bash
magento-cloud ssh-keys [--format FORMAT] [--columns COLUMNS] [--no-header]
```


```bash
ssh-keys
```

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `subscription:info`

Lecture ou modification des propriétés d’abonnement

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<property>] [<value>]
```


### `property`

Nom de la propriété


### `value`

Définir une nouvelle valeur pour la propriété


### `--id`, `-s`

ID d’abonnement

- Nécessite une valeur

### `--date-fmt`

Format de date (en tant que chaîne de format de date PHP)

- Valeur par défaut : `c`
- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `tunnel:close`

Fermer les tunnels SSH

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

### `--all`, `-a`

Fermer tous les tunnels

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `tunnel:info`

Affichage des informations de relation pour les tunnels SSH

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

### `--property`, `-P`

La propriété de relation à afficher

- Nécessite une valeur

### `--encode`, `-c`

Sortie sous forme de JSON encodé en base64

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `tunnel:list`

Liste des tunnels SSH

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```


```bash
tunnels
```

### `--all`, `-a`

Afficher tous les tunnels

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `tunnel:open`

Ouvrir les tunnels SSH aux relations d’une application

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

### `--gateway-ports`, `-g`

Autoriser les hôtes distants à se connecter aux ports transférés locaux

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `tunnel:single`

Ouvrir un tunnel SSH unique vers une relation d’application

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

### `--port`

Le port local

- Nécessite une valeur

### `--gateway-ports`, `-g`

Autoriser les hôtes distants à se connecter aux ports transférés locaux

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--app`, `-A`

Nom de l’application distante

- Nécessite une valeur

### `--relationship`, `-r`

Relation de service à utiliser

- Nécessite une valeur

### `--identity-file`, `-i`

Une identité SSH (clé privée) à utiliser

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `user:add`

Ajout d’un utilisateur au projet

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

Adresse électronique de l’utilisateur


### `--role`, `-r`

Rôle de projet de l’utilisateur (&#39;admin&#39; ou &#39;viewer&#39;) ou rôle de type d’environnement (par exemple : &quot;staging:contributor&quot; ou &quot;production:viewer&quot;). Pour supprimer un utilisateur d’un type d’environnement, définissez le rôle sur &quot;aucun&quot;. Le caractère % peut être utilisé comme caractère générique pour le type d’environnement, par exemple &#39;%:viewer&#39; pour donner à l&#39;utilisateur le rôle &#39;viewer&#39; sur tous les types. Le rôle peut être abrégé, par exemple : &#39;production:v&#39;.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `user:delete`

Suppression d’un utilisateur du projet

```bash
magento-cloud user:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <email>
```


### `email`

Adresse électronique de l’utilisateur

- Obligatoire

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `user:get`

Affichage du ou des rôles d’un utilisateur

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```


```bash
user:role
```


### `email`

Adresse électronique de l’utilisateur


### `--level`, `-l`

Le niveau de rôle (&#39;projet&#39; ou &#39;environnement&#39;)

- Nécessite une valeur

### `--pipe`

Extraire le rôle sur stdout (après avoir apporté des modifications)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--role`, `-r`

[Obsolète : utilisateur:mettre à jour pour modifier le ou les rôles d’un utilisateur]

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `user:list`

Liste des utilisateurs de projet

```bash
magento-cloud users [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```


```bash
users
```

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `user:update`

Mise à jour du ou des rôles utilisateur sur un projet

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

Adresse électronique de l’utilisateur


### `--role`, `-r`

Rôle de projet de l’utilisateur (&#39;admin&#39; ou &#39;viewer&#39;) ou rôle de type d’environnement (par exemple : &quot;staging:contributor&quot; ou &quot;production:viewer&quot;). Pour supprimer un utilisateur d’un type d’environnement, définissez le rôle sur &quot;aucun&quot;. Le caractère % peut être utilisé comme caractère générique pour le type d’environnement, par exemple &#39;%:viewer&#39; pour donner à l&#39;utilisateur le rôle &#39;viewer&#39; sur tous les types. Le rôle peut être abrégé, par exemple : &#39;production:v&#39;.

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `variable:create`

Création d’une variable

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```


### `name`

Nom de variable


### `--level`, `-l`

Niveau auquel définir la variable (&#39;projet&#39; ou &#39;environnement&#39;)

- Nécessite une valeur

### `--name`

Nom de variable

- Nécessite une valeur

### `--value`

Valeur de la variable

- Nécessite une valeur

### `--json`

Si la variable est au format JSON

- Valeur par défaut : `false`
- Nécessite une valeur

### `--sensitive`

Si la variable est sensible

- Valeur par défaut : `false`
- Nécessite une valeur

### `--prefix`

Préfixe du nom de variable (par ex. &#39;none&#39; ou &#39;env:&#39;)

- Valeur par défaut : `none`
- Nécessite une valeur

### `--enabled`

Indique si la variable doit être activée.

- Valeur par défaut : `true`
- Nécessite une valeur

### `--inheritable`

Si la variable est héritable par les environnements enfants

- Valeur par défaut : `true`
- Nécessite une valeur

### `--visible-build`

Si la variable doit être visible au moment de la création

- Nécessite une valeur

### `--visible-runtime`

Si la variable doit être visible au moment de l’exécution

- Valeur par défaut : `true`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `variable:delete`

Suppression d’une variable

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nom de variable

- Obligatoire

### `--level`, `-l`

Au niveau de la variable (&#39;projet&#39;, &#39;environnement&#39;, &#39;p&#39; ou &#39;e&#39;)

- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLÈTE ]&lt;/> Désactivation d’une variable activée au niveau de l’environnement

```bash
magento-cloud variable:disable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nom de la variable

- Obligatoire

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLÈTE ]&lt;/> Activation d’une variable de niveau environnement désactivée

```bash
magento-cloud variable:enable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nom de la variable

- Obligatoire

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `variable:get`

Affichage d’une variable

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```


```bash
vget
```


### `name`

Nom de la variable


### `--property`, `-P`

Affichage d’une propriété de variable unique

- Nécessite une valeur

### `--level`, `-l`

Au niveau de la variable (&#39;projet&#39;, &#39;environnement&#39;, &#39;p&#39; ou &#39;e&#39;)

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--pipe`

[Option obsolète] Générer la valeur de variable uniquement

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `variable:list`

Variables de liste

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```


```bash
variables
```


```bash
var
```

### `--level`, `-l`

Au niveau de la variable (&#39;projet&#39;, &#39;environnement&#39;, &#39;p&#39; ou &#39;e&#39;)

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLÈTE ]&lt;/> Définition d’une variable pour un environnement

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```


```bash
vset
```


### `name`

Nom de variable

- Obligatoire

### `value`

La valeur de la variable

- Obligatoire

### `--json`

Marquer la valeur comme JSON

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--disabled`

Marquer la variable comme désactivée

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `variable:update`

Mise à jour d’une variable

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nom de variable

- Obligatoire

### `--level`, `-l`

Au niveau de la variable (&#39;projet&#39;, &#39;environnement&#39;, &#39;p&#39; ou &#39;e&#39;)

- Nécessite une valeur

### `--value`

Valeur de la variable

- Nécessite une valeur

### `--json`

Si la variable est au format JSON

- Valeur par défaut : `false`
- Nécessite une valeur

### `--sensitive`

Si la variable est sensible

- Valeur par défaut : `false`
- Nécessite une valeur

### `--enabled`

Indique si la variable doit être activée.

- Valeur par défaut : `true`
- Nécessite une valeur

### `--inheritable`

Si la variable est héritable par les environnements enfants

- Valeur par défaut : `true`
- Nécessite une valeur

### `--visible-build`

Si la variable doit être visible au moment de la création

- Nécessite une valeur

### `--visible-runtime`

Si la variable doit être visible au moment de l’exécution

- Valeur par défaut : `true`
- Nécessite une valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--no-wait`, `-W`

N’attendez pas la fin de l’opération.

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--wait`

Attente de la fin de l’opération (par défaut)

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur


## `worker:list`

Obtention d’une liste de tous les programmes de travail déployés

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```


```bash
workers
```

### `--refresh`

Actualisation ou non du cache

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--project`, `-p`

ID ou URL du projet

- Nécessite une valeur

### `--host`

Nom d’hôte de l’API du projet

- Nécessite une valeur

### `--environment`, `-e`

ID d’environnement

- Nécessite une valeur

### `--format`

Format de sortie (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; ou &quot;plain&quot;)

- Valeur par défaut : `table`
- Nécessite une valeur

### `--columns`

Colonnes à afficher (liste séparée par des virgules ou valeurs multiples)

- Valeur par défaut : `[]`
- Nécessite une valeur

### `--no-header`

Ne pas générer l’en-tête du tableau

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--help`, `-h`

Afficher ce message d’aide

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--quiet`, `-q`

Ne sortez aucun message

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--verbose`, `-v|-vv|-vvv`

Augmenter la verbalisation des messages

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--version`, `-V`

Afficher cette version de l’application

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--yes`, `-y`

Répondez &quot;oui&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur

### `--no`, `-n`

Répondez &quot;non&quot; à toute question oui/non ; désactiver l&#39;interaction

- Valeur par défaut : `false`
- N’accepte pas de valeur
