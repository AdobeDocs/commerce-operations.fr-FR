---
title: Remplacer les paramètres de configuration
description: Découvrez comment utiliser les variables d’environnement pour remplacer les paramètres de configuration.
exl-id: 788fd3cd-f8c1-4514-8141-547fed36e9ce
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---

# Remplacer les paramètres de configuration

Cette rubrique explique comment dériver un nom de variable d’environnement en connaissant un chemin de configuration. Vous pouvez remplacer les paramètres de configuration d’Adobe Commerce à l’aide de variables d’environnement. Par exemple, vous pouvez remplacer la valeur de l’URL dynamique d’un processeur de paiements sur votre système de production.

Vous pouvez remplacer la valeur du paramètre de configuration _any_ à l’aide de variables d’environnement. Toutefois, Adobe vous recommande de conserver des paramètres cohérents à l’aide du fichier de configuration partagé, `config.php`, et du fichier de configuration spécifique au système, `env.php`, comme indiqué dans la section [Présentation générale du déploiement](../deployment/overview.md).

>[!TIP]
>
>Consultez la rubrique [ Configurer les environnements ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html?lang=fr) dans le guide _Commerce sur les infrastructures cloud_.

## Variables d’environnement

Un nom de variable d’environnement est constitué de sa portée suivie de son chemin de configuration dans un format particulier. Les sections suivantes expliquent en détail comment déterminer un nom de variable.

Vous pouvez utiliser des variables pour l’un des éléments suivants :

- [Valeurs sensibles](config-reference-sens.md) doivent être définies à l’aide de variables d’environnement ou de la commande [`magento config:sensitive:set`](../cli/set-configuration-values.md).
- Les valeurs spécifiques au système doivent être définies à l’aide des éléments suivants :

   - Variables d’environnement
   - La commande [`magento config:set`](../cli/set-configuration-values.md)
   - Admin suivi de la commande [`magento app:config:dump`](../cli/export-configuration.md)

Les chemins de configuration se trouvent dans :

- [Référence des chemins de configuration sensibles et spécifiques au système](config-reference-sens.md)
- [Référence des chemins de configuration des paiements](config-reference-payment.md)
- [Référence des chemins de configuration de l’extension B2B de Commerce](config-reference-b2b.md)
- [Référence des autres chemins de configuration](config-reference-general.md)

### Noms de variables

Le format général des noms de variables des paramètres système est le suivant :

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` peut être :

- Portée globale (c’est-à-dire le paramètre global pour _toutes_ portées)

  Les variables de portée globale ont le format suivant :

  `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Une portée spécifique (c’est-à-dire que le paramètre affecte uniquement une vue de magasin ou un site web spécifié)

  Par exemple, les variables d’étendue de vue de magasin ont le format suivant :

  `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

  Pour plus d’informations sur les portées, voir :

   - [Étape 1 : rechercher la valeur de la portée de l’affichage du site web ou du magasin](#step-1-find-the-website-or-store-view-scope-value)
   - [Rubrique du guide de l’utilisateur de Commerce sur la portée](https://experienceleague.adobe.com/fr/docs/commerce-admin/start/setup/websites-stores-views#scope-settings)
   - [Référence rapide de la portée](https://experienceleague.adobe.com/fr/docs/commerce-admin/config/scope-change#scope-quick-reference)

`<SYSTEM__VARIABLE__NAME>` est le chemin de configuration avec des caractères de soulignement doubles substitués à `/`. Pour plus d’informations, voir [Étape 2 : définition des variables système](#step-2-set-global-website-or-store-view-variables).

### Format de variable

`<SCOPE>` est séparé de `<SYSTEM__VARIABLE__NAME>` par deux caractères de soulignement.

`<SYSTEM__VARIABLE__NAME>` est dérivé du _chemin de configuration_ d’un paramètre de configuration, qui est une chaîne délimitée par des `/` qui identifie de manière unique un paramètre particulier. Remplacez chaque caractère `/` dans le chemin de configuration par deux caractères de soulignement pour créer la variable système.

Si un chemin de configuration contient un caractère de soulignement, ce dernier reste dans la variable .

La liste complète des chemins de configuration figure à l’adresse :

- [Référence des chemins de configuration sensibles et spécifiques au système](config-reference-sens.md)
- [Référence des chemins de configuration des paiements](config-reference-payment.md)
- [Référence des chemins de configuration de l’extension B2B d’entreprise Commerce](config-reference-b2b.md)
- [Référence des autres chemins de configuration](config-reference-general.md)

## Étape 1 : rechercher la valeur de la portée de l’affichage du site web ou du magasin

Cette section explique comment rechercher et définir des valeurs de configuration système par _portée_ (vue de magasin ou site web). Pour définir des variables de portée globale, consultez [Étape 2 : définir des variables d’affichage globales, de site web ou de magasin](#step-2-set-global-website-or-store-view-variables).

Les valeurs d’étendue proviennent des tableaux `store`, `store_group` et `store_website`.

- Le tableau `store` spécifie les noms et les codes des vues de magasin
- Le tableau `store_website` spécifie les noms et codes de site web

Vous pouvez également trouver les valeurs de code à l’aide de l’Administration.

Comment lire le tableau :

- `Path in Admin` la colonne

  Les valeurs avant la virgule sont des chemins d’accès dans la navigation d’administration. Les valeurs après la virgule sont des options dans le volet de droite.

- `Variable name` colonne correspond au nom de la variable d’environnement correspondante.

  Vous avez la possibilité de spécifier des valeurs système pour ces paramètres de configuration en tant que variables d’environnement si vous le souhaitez.

   - Le nom de variable entier est toujours en MAJUSCULES
   - Commencez un nom de variable par `CONFIG__` (notez deux caractères de soulignement)
   - La partie `<STORE_VIEW_CODE>` ou `<WEBSITE_CODE>` d’un nom de variable se trouve dans la base de données Admin ou Commerce, comme indiqué dans les sections suivantes.
   - Vous pouvez trouver des `<SYSTEM__VARIABLE__NAME>` comme indiqué à l’[Étape 2 : définir des variables d’affichage globales, de site web ou de magasin](#step-2-set-global-website-or-store-view-variables).

### Recherche d’un site web ou d’une étendue d’affichage de magasin dans l’Admin

Le tableau suivant résume la manière de trouver un site web ou de stocker la valeur d’affichage dans Admin.

| Description | Chemin dans Admin | Nom de la variable |
|--------------|--------------|----------------------|
| Créer, modifier et supprimer des vues de magasin | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Créer, modifier et supprimer des sites web | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

Par exemple, pour rechercher une valeur de portée d’affichage de site web ou de magasin dans l’administrateur :

1. Connectez-vous à l’administrateur en tant qu’utilisateur autorisé à afficher des sites web.
1. Cliquez sur **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Cliquez sur le nom d’une vue de site web ou de magasin.

   Le volet de droite s’affiche comme suit.

   ![Trouver un code de site web](../../assets/configuration/website-code.png)

1. Le nom de l’étendue s’affiche dans le champ **[!UICONTROL Code]** .
1. Passez à [Étape 2 : définir des variables d’affichage globales, de site web ou de magasin](#step-2-set-global-website-or-store-view-variables).

### Recherche d’un site web ou d’une étendue d’affichage de magasin dans la base de données

Pour obtenir ces valeurs à partir de la base de données :

1. Connectez-vous à votre système de développement en tant que propriétaire du système de fichiers si vous ne l’avez pas déjà fait.
1. Saisissez la commande suivante :

   ```bash
   mysql -u <database-username> -p
   ```

1. À l’invite de `mysql>`, saisissez les commandes suivantes dans l’ordre indiqué :

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

1. Utilisez la valeur de la colonne `code` comme nom de l’étendue, et non la valeur `name`.

   Par exemple, pour définir une variable de configuration pour le site web de test, utilisez le format suivant :

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   d’où `<SYSTEM__VARIABLE__NAME>` provient la section suivante.

## Étape 2 : définir des variables d’affichage globales, de site web ou de magasin

Cette section explique comment définir des variables système.

- Pour définir des valeurs pour la portée globale (c’est-à-dire tous les sites web, magasins et vues de magasin), commencez le nom de la variable par `CONFIG__DEFAULT__`.

- Pour définir une valeur pour une vue de magasin ou un site web spécifique, commencez par définir le nom de la variable comme décrit dans la section [Étape 1 : Rechercher la valeur de la portée ](#step-1-find-the-website-or-store-view-scope-value) :

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- La dernière partie du nom de la variable est le chemin de configuration, qui est unique pour chaque paramètre de configuration.

[Voir quelques exemples](#examples).

Le tableau suivant présente quelques exemples de variables.

| Description | Chemin d’accès dans Admin (sans **Magasins** > **Paramètres** > **Configuration**) | Nom de la variable |
|--------------|--------------|----------------------|
| nom d’hôte du serveur Elasticsearch | Catalogue > **Catalogue**, **Nom D’Hôte Du Serveur Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Port du serveur Elasticsearch | Catalogue > **Catalogue**, **Port du serveur Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Origine du pays d’expédition | Ventes > **Paramètres d’expédition** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| URL d’administration personnalisée | Avancé > **Admin** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Chemin d’accès d’administration personnalisé | Avancé > **Admin** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Exemples

Cette section explique comment trouver les valeurs de certaines variables d’exemple.

### nom d’hôte du serveur Elasticsearch

Pour rechercher le nom de variable pour la minimisation globale d’HTML :

1. Déterminez la portée.

   Comme il s’agit de la portée globale, le nom de la variable commence par `CONFIG__DEFAULT__`

1. Le reste du nom de variable est `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Result** : le nom de la variable est `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Origine du pays d’expédition

Pour rechercher le nom de variable du pays d’expédition d’origine :

1. Déterminez la portée.

   Recherchez la portée dans la [base de données](#find-a-website-or-store-view-scope-in-the-database) comme expliqué à l’étape 1 : rechercher la valeur de la portée de l’affichage du site web ou du magasin. (Vous pouvez également trouver la valeur dans Admin, comme indiqué dans le [tableau de l’étape 2 : définir des variables d’affichage globales, de site web ou de magasin]&#x200B;(#step-2-set-global-website-or-store-view-variables.

   Par exemple, la portée peut être `CONFIG__WEBSITES__DEFAULT`.

1. Le reste du nom de variable est `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Result** : le nom de la variable est `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Utilisation des variables d’environnement

Définissez les valeurs de configuration comme variables en utilisant le tableau associé [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) de PHP. Vous pouvez définir les valeurs dans n’importe quel script PHP qui s’exécute lorsque Commerce s’exécute.

>[!TIP]
>
>La définition de valeurs de variable dans `index.php` ou `pub/index.php` ne fonctionne pas toujours comme prévu, car différents points d’entrée de l’application peuvent être utilisés selon la configuration du serveur web. En plaçant des directives `$_ENV` dans le fichier `app/bootstrap.php`, quels que soient les points d’entrée de l’application, les directives `$_ENV` s’exécutent toujours, car le fichier `app/bootstrap.php` se charge dans le cadre de l’architecture Commerce.

Voici un exemple de définition de deux valeurs `$_ENV` :

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Un exemple détaillé est présenté dans [Définir des valeurs de configuration à l’aide de variables d’environnement](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- Pour utiliser les valeurs que vous définissez dans le tableau `$_ENV`, vous devez définir `variables_order = "EGPCS"`(Environnement, Get, Post, Cookie et Server) dans votre fichier `php.ini`. Pour plus de détails, voir [Documentation PHP](https://www.php.net/manual/en/ini.core.php).
>
>- Pour Adobe Commerce sur les infrastructures cloud, si vous tentez de remplacer les paramètres de configuration à l’aide de l’[interface web de projet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=fr#configure-the-project), vous devez ajouter le préfixe `env:` au nom de la variable. Par exemple :
>
>![ Exemple de variable d’environnement ](../../assets/configuration/cloud-console-envvariable.png)
