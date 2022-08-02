---
title: Remplacement des paramètres de configuration
description: Découvrez comment utiliser les variables d’environnement pour remplacer les paramètres de configuration.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---


# Remplacement des paramètres de configuration

Cette rubrique explique comment dériver un nom de variable d’environnement connaissant un chemin de configuration. Vous pouvez remplacer les paramètres de configuration Adobe Commerce à l’aide de variables d’environnement. Par exemple, vous pouvez remplacer la valeur de l’URL active d’un processeur de paiement sur votre système de production.

Vous pouvez remplacer la valeur de _any_ configuration à l’aide des variables d’environnement ; Adobe vous recommande toutefois de conserver des paramètres cohérents à l’aide du fichier de configuration partagé, `config.php`et le fichier de configuration spécifique au système, `env.php`, comme décrit dans [Présentation générale du déploiement](../deployment/overview.md).

>[!TIP]
>
>Consultez la section [Configuration des environnements](https://devdocs.magento.com/cloud/env/variables-intro.html) dans la _Guide Commerce Cloud_ pour plus d’informations sur l’utilisation des variables dans Adobe Commerce sur l’infrastructure cloud.

## Variables d’environnement

Un nom de variable d’environnement se compose de son étendue suivie de son chemin de configuration dans un format particulier. Les sections suivantes expliquent comment déterminer plus en détail un nom de variable.

Vous pouvez utiliser des variables pour l’une des opérations suivantes :

- [Valeurs sensibles](config-reference-sens.md) doit être défini à l’aide de variables d’environnement ou de la variable [`magento config:sensitive:set`](../cli/set-configuration-values.md) .
- Les valeurs propres au système doivent être définies à l’aide des éléments suivants :

   - Variables d’environnement
   - Le [`magento config:set`](../cli/set-configuration-values.md) command
   - L’administrateur suivi de la fonction [`magento app:config:dump` command](../cli/export-configuration.md)

Les chemins de configuration se trouvent dans :

- [Référence des chemins de configuration sensibles et spécifiques au système](config-reference-sens.md)
- [Référence des chemins de configuration des paiements](config-reference-payment.md)
- [Référence des chemins de configuration de l’extension B2B Commerce](config-reference-b2b.md)
- [Autres références de chemins de configuration](config-reference-general.md)

### Noms de variables

Le format général des noms de variable des paramètres système suit :

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` peut être :

- Portée globale (c’est-à-dire le paramètre global pour _all_ portées)

   Les variables de portée globale ont le format suivant :

   `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Portée spécifique (c’est-à-dire que le paramètre affecte uniquement une vue de magasin ou un site web spécifique)

   Les variables de portée de vue de magasin, par exemple, ont le format suivant :

   `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

   Pour plus d’informations sur les portées, voir :

   - [Étape 1 : Recherche de la valeur de portée du site web ou de la vue de magasin](#step-1-find-the-website-or-store-view-scope-value)
   - [Rubrique du Guide de l’utilisateur de Commerce sur la portée](https://docs.magento.com/user-guide/configuration/scope.html)
   - [Référence rapide sur la portée](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` est le chemin de configuration avec des caractères de soulignement doubles remplacés par `/`. Pour plus d’informations, voir [Étape 2 : Définition des variables système](#step-2-set-global-website-or-store-view-variables).

### Format de variable

`<SCOPE>` est séparé de `<SYSTEM__VARIABLE__NAME>` par deux caractères de soulignement.

`<SYSTEM__VARIABLE__NAME>` est dérivé d’un paramètre de configuration _chemin de configuration_, qui est un `/` chaîne délimitée qui identifie de manière unique un paramètre particulier. Remplacer chaque `/` dans le chemin de configuration avec deux caractères de soulignement pour créer la variable système.

Si un chemin de configuration contient un caractère de soulignement, celui-ci reste dans la variable .

Vous trouverez une liste complète des chemins de configuration dans :

- [Référence des chemins de configuration sensibles et spécifiques au système](config-reference-sens.md)
- [Référence des chemins de configuration des paiements](config-reference-payment.md)
- [Référence des chemins de configuration de l’extension B2B de Commerce Enterprise](config-reference-b2b.md)
- [Autres références de chemins de configuration](config-reference-general.md)

## Étape 1 : Recherche de la valeur de portée du site web ou de la vue de magasin

Cette section explique comment rechercher et définir des valeurs de configuration système par _scope_ (vue de magasin ou site web). Pour définir des variables de portée globale, voir [Étape 2 : Définir des variables d’affichage globales, de site web ou de magasin](#step-2-set-global-website-or-store-view-variables).

Les valeurs de portée proviennent de la variable `store`, `store_group`, et `store_website` des tables.

- Le `store` spécifie les noms et codes des vues de magasin
- Le `store_website` spécifie les noms et codes de site web

Vous pouvez également trouver les valeurs de code à l’aide de l’Admin.

Comment lire le tableau :

- `Path in Admin` column

   Les valeurs situées avant la virgule sont des chemins d’accès dans la navigation Admin. Les valeurs après la virgule sont des options dans le volet de droite.

- `Variable name` est le nom de la variable d’environnement correspondante.

   Vous avez la possibilité de spécifier les valeurs système de ces paramètres de configuration en tant que variables d’environnement si vous le souhaitez.

   - Le nom complet de la variable est toujours ALL CAPS
   - Commencer un nom de variable par `CONFIG__` (notez deux caractères de soulignement)
   - Vous trouverez la variable `<STORE_VIEW_CODE>` ou `<WEBSITE_CODE>` d’un nom de variable dans la base de données Admin ou Commerce, comme indiqué dans les sections suivantes.
   - Vous pouvez trouver `<SYSTEM__VARIABLE__NAME>` comme décrit dans [Étape 2 : Définir des variables d’affichage globales, de site web ou de magasin](#step-2-set-global-website-or-store-view-variables).

### Recherche d’un site web ou d’une portée d’affichage de magasin dans l’Admin

Le tableau suivant résume la manière de trouver la valeur d’affichage de site web ou de magasin dans l’administrateur.

| Description | Chemin d’accès dans Admin | Nom de variable |
|--------------|--------------|----------------------|
| Créer, modifier et supprimer des vues de magasin | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Créer, modifier et supprimer des sites web | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

Par exemple, pour trouver un site web ou stocker la valeur de portée de vue dans l’administrateur :

1. Connectez-vous à l’administrateur en tant qu’utilisateur autorisé à consulter des sites web.
1. Cliquez sur **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Cliquez sur le nom d’un site web ou d’une vue de magasin.

   Le volet de droite s’affiche comme suit.

   ![Recherche d’un code de site web](../../assets/configuration/website-code.png)

1. Le nom de la portée s’affiche dans la variable **[!UICONTROL Code]** champ .
1. Passez à la [Étape 2 : Définir des variables d’affichage globales, de site web ou de magasin](#step-2-set-global-website-or-store-view-variables).

### Recherche d’une portée d’affichage de site web ou de magasin dans la base de données

Pour obtenir ces valeurs de la base de données :

1. Connectez-vous à votre système de développement en tant que [propriétaire du système de fichiers](https://glossary.magento.com/magento-file-system-owner) si vous ne l&#39;avez pas déjà fait.
1. Saisissez la commande suivante :

   ```bash
   mysql -u <database-username> -p
   ```

1. Dans le `mysql>` saisissez les commandes suivantes dans l’ordre indiqué :

   ```shell
   use <database-name>;
   ```

1. Utilisez les requêtes SQL suivantes pour trouver les valeurs appropriées :

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   Voici un exemple :

   ```shell
   mysql> SELECT * FROM STORE_WEBSITE;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

1. Utilisez la valeur de la variable `code` n’est pas la colonne `name` .

   Par exemple, pour définir une variable de configuration pour le site Web de test, utilisez le format suivant :

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   where `<SYSTEM__VARIABLE__NAME>` provient de la section suivante.

## Étape 2 : Définir des variables d’affichage globales, de site web ou de magasin

Cette section explique comment définir des variables système.

- Pour définir des valeurs pour la portée globale (c’est-à-dire tous les sites web, magasins et vues de magasin), commencez le nom de variable par `CONFIG__DEFAULT__`.

- Pour définir une valeur pour une vue de magasin ou un site web spécifique, démarrez le nom de variable comme décrit dans la section [Étape 1 : Rechercher la valeur de portée](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- La dernière partie du nom de la variable est le chemin de configuration, qui est unique pour chaque paramètre de configuration.

[Voir quelques exemples](#examples).

Le tableau suivant présente quelques exemples de variables.

| Description | Chemin d’accès dans l’administration (omission **Magasins** > **Paramètres** > **Configuration**) | Nom de variable |
|--------------|--------------|----------------------|
| Nom d’hôte du serveur Elasticsearch | Catalogue > **Catalogue**, **Nom d’hôte du serveur Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Port du serveur Elasticsearch | Catalogue > **Catalogue**, **Port du serveur Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Origine du pays d&#39;expédition | Ventes > **Paramètres d’expédition** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| URL d’administration personnalisée | Avancé > **Administration** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Chemin d’accès d’administration personnalisé | Avancé > **Administration** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Exemples

Cette section explique comment rechercher des valeurs de certains exemples de variables.

### Nom d’hôte du serveur Elasticsearch

Pour rechercher le nom de variable pour la minification de HTML globale :

1. Déterminez la portée.

   Il s’agit de la portée globale, de sorte que le nom de variable commence par `CONFIG__DEFAULT__`

1. Le reste du nom de la variable est `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Résultat**: Le nom de la variable est `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Origine du pays d&#39;expédition

Pour rechercher le nom de variable pour l’origine du pays d’expédition :

1. Déterminez la portée.

   Recherchez l’étendue dans le [base](#find-a-website-or-store-view-scope-in-the-database) comme indiqué à l’étape 1 : Recherchez la valeur de portée du site web ou de la vue de magasin. (Vous pouvez également trouver la valeur dans l’Admin comme indiqué dans la section [tableau de l’étape 2 : Définir des variables d’affichage globales, de site web ou de magasin](#step-2-set-global-website-or-store-view-variables.

   Par exemple, la portée peut être `CONFIG__WEBSITES__DEFAULT`.

1. Le reste du nom de la variable est `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Résultat**: Le nom de la variable est `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Utilisation des variables d’environnement

Définir des valeurs de configuration comme variables à l’aide de PHP [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) table d’associée. Vous pouvez définir les valeurs de tout script PHP qui s’exécute lors de l’exécution de Commerce.

>[!TIP]
>
>Définition des valeurs de variable dans `index.php` ou `pub/index.php` ne fonctionne pas toujours comme prévu, car différents points d’entrée d’application peuvent être utilisés en fonction de la configuration du serveur web. En plaçant `$_ENV` dans les `app/bootstrap.php` , quels que soient les différents points d’entrée de l’application, la variable `$_ENV` les directives s’exécutent toujours, car `app/bootstrap.php` charge le fichier dans le cadre de l’architecture Commerce.

Exemple de définition de deux `$_ENV` est la suivante :

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Un exemple détaillé est présenté dans la section [Définition de valeurs de configuration à l’aide de variables d’environnement](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- Pour utiliser les valeurs définies dans la variable `$_ENV` tableau, vous devez définir `variables_order = "EGPCS"`(Environnement, Obtenir, Publier, Cookie et Serveur) dans votre `php.ini` fichier . Pour plus d’informations, voir [documentation PHP](https://www.php.net/manual/en/ini.core.php).
>
>- Pour Adobe Commerce sur l’infrastructure cloud, si vous tentez de remplacer les paramètres de configuration à l’aide de la variable [Interface Web du projet](https://devdocs.magento.com/cloud/project/project-webint-basic.html#project-conf-env-var), vous devez ajouter en préfixe le nom de la variable `env:`. Par exemple :
>
>![Exemple de variable d’environnement](https://devdocs.magento.com/common/images/cloud/cloud_env_var_example.png)
