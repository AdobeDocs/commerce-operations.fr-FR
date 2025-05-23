---
title: Remplacement des paramètres de configuration
description: Découvrez comment utiliser les variables d’environnement pour remplacer les paramètres de configuration.
exl-id: 788fd3cd-f8c1-4514-8141-547fed36e9ce
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---

# Remplacement des paramètres de configuration

Cette rubrique explique comment dériver un nom de variable d’environnement connaissant un chemin de configuration. Vous pouvez remplacer les paramètres de configuration Adobe Commerce à l’aide de variables d’environnement. Par exemple, vous pouvez remplacer la valeur de l’URL active d’un processeur de paiement sur votre système de production.

Vous pouvez remplacer la valeur de _tout_ paramètre de configuration à l’aide de variables d’environnement ; cependant, Adobe vous recommande de conserver des paramètres cohérents à l’aide du fichier de configuration partagé, `config.php`, et du fichier de configuration spécifique au système, `env.php`, comme décrit dans la [présentation générale du déploiement](../deployment/overview.md).

>[!TIP]
>
>Consultez la rubrique [Configuration des environnements](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html?lang=fr) dans le _guide Commerce on Cloud Infrastructure_.

## Variables d’environnement

Un nom de variable d’environnement se compose de son étendue suivie de son chemin de configuration dans un format particulier. Les sections suivantes expliquent comment déterminer plus en détail un nom de variable.

Vous pouvez utiliser des variables pour l’une des opérations suivantes :

- [Les valeurs sensibles](config-reference-sens.md) doivent être définies à l’aide de variables d’environnement ou de la commande [`magento config:sensitive:set`](../cli/set-configuration-values.md).
- Les valeurs propres au système doivent être définies à l’aide des éléments suivants :

   - Variables d’environnement
   - La commande [`magento config:set`](../cli/set-configuration-values.md)
   - L’administrateur suivi de la commande [`magento app:config:dump`](../cli/export-configuration.md)

Les chemins de configuration se trouvent dans :

- [Référence des chemins de configuration sensibles et spécifiques au système](config-reference-sens.md)
- [Référence des chemins de configuration des paiements](config-reference-payment.md)
- [Référence sur les chemins de configuration de l’extension Commerce B2B](config-reference-b2b.md)
- [Autres références de chemins de configuration](config-reference-general.md)

### Noms de variables

Le format général des noms de variable des paramètres système suit :

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` peut être :

- Portée globale (c’est-à-dire le paramètre global pour _toutes_ portées)

  Les variables de portée globale ont le format suivant :

  `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Portée spécifique (c’est-à-dire que le paramètre affecte uniquement une vue de magasin ou un site web spécifique)

  Les variables de portée de vue de magasin, par exemple, ont le format suivant :

  `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

  Pour plus d’informations sur les portées, voir :

   - [Étape 1 : recherche de la valeur de portée du site web ou de la vue de magasin](#step-1-find-the-website-or-store-view-scope-value)
   - [Rubrique du guide de l’utilisateur de Commerce sur la portée](https://experienceleague.adobe.com/fr/docs/commerce-admin/start/setup/websites-stores-views#scope-settings)
   - [Référence rapide sur l’étendue](https://experienceleague.adobe.com/fr/docs/commerce-admin/config/scope-change#scope-quick-reference)

`<SYSTEM__VARIABLE__NAME>` est le chemin de configuration avec des caractères de soulignement doubles remplacés par `/`. Pour plus d’informations, voir [Étape 2 : définition des variables système](#step-2-set-global-website-or-store-view-variables).

### Format de variable

`<SCOPE>` est séparé de `<SYSTEM__VARIABLE__NAME>` par deux caractères de soulignement.

`<SYSTEM__VARIABLE__NAME>` est dérivé du _chemin de configuration_ d’un paramètre de configuration, qui est une chaîne délimitée `/` qui identifie de manière unique un paramètre particulier. Remplacez chaque caractère `/` du chemin de configuration par deux caractères de soulignement pour créer la variable système.

Si un chemin de configuration contient un caractère de soulignement, celui-ci reste dans la variable .

Vous trouverez une liste complète des chemins de configuration dans :

- [Référence des chemins de configuration sensibles et spécifiques au système](config-reference-sens.md)
- [Référence des chemins de configuration des paiements](config-reference-payment.md)
- [Référence sur les chemins de configuration de l’extension Commerce Enterprise B2B](config-reference-b2b.md)
- [Autres références de chemins de configuration](config-reference-general.md)

## Étape 1 : recherche de la valeur de portée du site web ou de la vue de magasin

Cette section explique comment trouver et définir des valeurs de configuration système par _portée_ (vue de magasin ou site web). Pour définir des variables de portée globale, voir [Étape 2 : définition de variables de vue globale, de site web ou de magasin](#step-2-set-global-website-or-store-view-variables).

Les valeurs de portée proviennent des tables `store`, `store_group` et `store_website`.

- La table `store` spécifie les noms et les codes des vues de magasin
- La table `store_website` spécifie les noms et les codes de site web

Vous pouvez également trouver les valeurs de code à l’aide de l’Admin.

Comment lire le tableau :

- colonne `Path in Admin`

  Les valeurs situées avant la virgule sont des chemins d’accès dans la navigation Admin. Les valeurs après la virgule sont des options dans le volet de droite.

- La colonne `Variable name` est le nom de la variable d&#39;environnement correspondante.

  Vous avez la possibilité de spécifier les valeurs système de ces paramètres de configuration en tant que variables d’environnement si vous le souhaitez.

   - Le nom complet de la variable est toujours ALL CAPS
   - Commencer un nom de variable avec `CONFIG__` (notez deux caractères de soulignement)
   - Vous trouverez la partie `<STORE_VIEW_CODE>` ou `<WEBSITE_CODE>` d’un nom de variable dans la base de données Admin ou Commerce, comme indiqué dans les sections suivantes.
   - Vous pouvez trouver `<SYSTEM__VARIABLE__NAME>` comme décrit dans [Étape 2 : définir des variables globales, de site web ou de vue de magasin](#step-2-set-global-website-or-store-view-variables).

### Recherche d’un site web ou stockage d’une portée d’affichage dans l’administrateur

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

   ![Trouver un code de site web](../../assets/configuration/website-code.png)

1. Le nom de la portée s’affiche dans le champ **[!UICONTROL Code]**.
1. Passez à l’ [Étape 2 : définition des variables d’affichage globales, de site web ou de magasin](#step-2-set-global-website-or-store-view-variables).

### Recherche d’une portée d’affichage de site web ou de magasin dans la base de données

Pour obtenir ces valeurs de la base de données :

1. Connectez-vous à votre système de développement en tant que propriétaire du système de fichiers si vous ne l’avez pas déjà fait.
1. Saisissez la commande suivante :

   ```bash
   mysql -u <database-username> -p
   ```

1. À l’invite `mysql>`, saisissez les commandes suivantes dans l’ordre indiqué :

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

1. Utilisez la valeur de la colonne `code` comme nom de la portée, et non la valeur `name`.

   Par exemple, pour définir une variable de configuration pour le site Web de test, utilisez le format suivant :

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   où `<SYSTEM__VARIABLE__NAME>` provient de la section suivante.

## Étape 2 : définition de variables d’affichage globales, de site web ou de magasin

Cette section explique comment définir des variables système.

- Pour définir des valeurs pour la portée globale (c’est-à-dire tous les sites web, magasins et vues de magasin), commencez le nom de variable par `CONFIG__DEFAULT__`.

- Pour définir une valeur pour une vue de magasin ou un site web spécifique, démarrez le nom de variable comme décrit dans [Étape 1 : Rechercher la valeur de portée](#step-1-find-the-website-or-store-view-scope-value) :

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- La dernière partie du nom de la variable est le chemin de configuration, qui est unique pour chaque paramètre de configuration.

[Voir quelques exemples](#examples).

Le tableau suivant présente quelques exemples de variables.

| Description | Chemin d’accès dans Admin (sans **Magasins** > **Paramètres** > **Configuration**) | Nom de variable |
|--------------|--------------|----------------------|
| Nom d’hôte du serveur Elasticsearch | Catalogue > **Catalog**, **Nom d’hôte du serveur Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Port du serveur Elasticsearch | Catalogue > **Catalog**, **Port du serveur Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Origine du pays d&#39;expédition | Ventes > **Paramètres d’expédition** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| URL d’administration personnalisée | Avancé > **Admin** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Chemin d’accès d’administration personnalisé | Avancé > **Admin** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Exemples

Cette section explique comment rechercher des valeurs de certains exemples de variables.

### Nom d’hôte du serveur Elasticsearch

Pour rechercher le nom de variable pour la minification globale de l’HTML :

1. Déterminez la portée.

   Il s’agit de la portée globale, de sorte que le nom de variable commence par `CONFIG__DEFAULT__`.

1. Le reste du nom de la variable est `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Result** : le nom de variable est `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Origine du pays d&#39;expédition

Pour rechercher le nom de variable pour l’origine du pays d’expédition :

1. Déterminez la portée.

   Recherchez la portée dans la [base de données](#find-a-website-or-store-view-scope-in-the-database) comme expliqué à l’étape 1 : recherchez la valeur de la portée de la vue de magasin ou de site web. (Vous pouvez également trouver la valeur dans l’Admin comme indiqué dans le tableau [ de l’étape 2 : définir des variables globales, de site web ou de vue de magasin](#step-2-set-global-website-or-store-view-variables).

   Par exemple, la portée peut être `CONFIG__WEBSITES__DEFAULT`.

1. Le reste du nom de la variable est `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Result** : le nom de variable est `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Utilisation des variables d’environnement

Définissez des valeurs de configuration en tant que variables à l’aide du tableau associé [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) de PHP. Vous pouvez définir les valeurs de tout script PHP qui s’exécute lors de l’exécution de Commerce.

>[!TIP]
>
>La définition de valeurs de variable dans `index.php` ou `pub/index.php` ne fonctionne pas toujours comme prévu, car différents points d’entrée d’application peuvent être utilisés en fonction de la configuration du serveur web. En plaçant des directives `$_ENV` dans le fichier `app/bootstrap.php`, quels que soient les différents points d’entrée de l’application, les directives `$_ENV` s’exécutent toujours puisque le fichier `app/bootstrap.php` est chargé dans le cadre de l’architecture Commerce.

Voici un exemple de définition de deux valeurs `$_ENV` :

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Un exemple détaillé est présenté dans la section [Définir des valeurs de configuration à l’aide de variables d’environnement](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- Pour utiliser les valeurs que vous définissez dans le tableau `$_ENV`, vous devez définir `variables_order = "EGPCS"`(Environnement, Get, Post, Cookie et Serveur) dans votre fichier `php.ini`. Pour plus d’informations, voir la [documentation PHP](https://www.php.net/manual/en/ini.core.php).
>
>- Pour Adobe Commerce sur l’infrastructure cloud, si vous tentez de remplacer les paramètres de configuration à l’aide de l’[ interface web du projet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=fr#configure-the-project), vous devez ajouter `env:` en préfixe au nom de la variable. Par exemple :
>
>![Exemple de variable d’environnement](../../assets/configuration/cloud-console-envvariable.png)
