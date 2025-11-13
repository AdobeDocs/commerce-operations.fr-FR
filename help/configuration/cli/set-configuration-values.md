---
title: Définir les valeurs de configuration
description: Découvrez comment définir des valeurs de configuration et modifier les valeurs d’administration verrouillées dans Adobe Commerce. Découvrez les commandes et techniques de configuration avancées.
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 2672c696d672ad72bef7537570ed630bc33c41b4
workflow-type: tm+mt
source-wordcount: '1101'
ht-degree: 0%

---

# Définir les valeurs de configuration

{{file-system-owner}}

Cette rubrique présente les commandes de configuration avancées que vous pouvez utiliser pour :

- Définissez une option de configuration à partir de la ligne de commande
- Verrouillez éventuellement toute option de configuration afin que sa valeur ne puisse pas être modifiée dans l’administrateur
- Modifier une option de configuration verrouillée dans l’administrateur

Vous pouvez utiliser ces commandes pour définir la configuration Commerce manuellement ou à l’aide de scripts. Vous définissez les options de configuration à l’aide d’un _chemin de configuration_, qui est une chaîne délimitée par des `/` qui identifie de manière unique cette option de configuration. Les chemins de configuration sont répertoriés dans les références suivantes :

- [Référence des chemins de configuration sensibles et spécifiques au système](../reference/config-reference-sens.md)
- [Référence des chemins de configuration des paiements](../reference/config-reference-payment.md)
- [Référence des chemins de configuration généraux](../reference/config-reference-general.md)
- [Référence des chemins de configuration de l’extension B2B d’entreprise Commerce](../reference/config-reference-b2b.md)

Vous pouvez définir des valeurs aux heures suivantes :

- Avant d’installer Commerce, vous pouvez définir des valeurs de configuration pour l’étendue par défaut uniquement, car il s’agit de la seule étendue valide.

- Après avoir installé Commerce, vous pouvez définir des valeurs de configuration pour n’importe quel site web ou étendue d’affichage de magasin.

Utilisez les commandes suivantes :

- `bin/magento config:set` définit toute valeur de configuration non sensible en fonction de son chemin de configuration
- `bin/magento config:sensitive:set` définit toute valeur de configuration sensible en fonction de son chemin de configuration
- `bin/magento config:show` affiche les valeurs de configuration enregistrées ; les valeurs des paramètres chiffrés sont affichées sous forme d’astérisques

## Conditions préalables

Pour définir une valeur de configuration, vous devez connaître au moins l’un des éléments suivants :

- Chemin de configuration
- Pour définir une valeur de configuration pour une portée particulière, vous devez connaître le code de portée.

  Pour définir une valeur de configuration pour l’étendue par défaut, vous n’avez rien à faire.

### Rechercher le chemin de configuration

Voir les références suivantes :

- [Référence des chemins de configuration sensibles et spécifiques au système](../reference/config-reference-sens.md)
- [Référence des chemins de configuration des paiements](../reference/config-reference-payment.md)
- [Référence des autres chemins de configuration](../reference/config-reference-general.md)
- [Référence des chemins de configuration de l’extension B2B d’entreprise Commerce](../reference/config-reference-b2b.md)

### Rechercher le code de l’étendue

Le code de l’étendue se trouve dans la base de données Commerce ou dans Commerce Admin.

**Pour trouver le code d’étendue dans Admin** :

1. Connectez-vous à l’administrateur en tant qu’utilisateur autorisé à afficher des sites web et à stocker des vues.
1. Cliquez sur **[!UICONTROL Stores]** > Paramètres > **[!UICONTROL All Stores]**.
1. Dans le volet de droite, cliquez sur le nom du site web ou de l’affichage du magasin pour afficher son code.

   La figure suivante présente un exemple de code de site web.

   ![Obtenir un code d’affichage de site web ou de boutique auprès de l’administrateur](../../assets/configuration/website-code.png)

1. Continuez avec [Définir les valeurs](#set-values).

**Pour trouver le code d&#39;étendue dans la base de données** :

Les codes d’étendue pour les sites web et les vues de magasin sont stockés dans la base de données Commerce, dans les tableaux `store_website` et `store`, respectivement.

1. Connectez-vous à la base de données Commerce.

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. Saisissez les commandes suivantes :

   ```shell
   use <Commerce database name>;
   ```

   ```shell
   SELECT * FROM store;
   ```

   ```shell
   SELECT * FROM store_website;
   ```

   Voici un exemple de résultat :

   ```
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   Utilisez la valeur de la colonne `code` .

1. Passez à la section suivante.

## Définir les valeurs

**Pour définir des valeurs de configuration spécifiques au système** :

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**Pour définir des valeurs de configuration sensibles** :

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path
```

Le tableau suivant décrit les paramètres de la commande `set` :

| Paramètre | Description |
| --- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `--scope` | Portée de la configuration. Les valeurs possibles sont `default`, `website` ou `store`. La valeur par défaut est `default`. |
| `--scope-code` | Le code d’étendue de la configuration (code de site web ou code d’affichage du magasin) |
| `-e or --lock-env` | Verrouille la valeur afin qu’elle ne puisse pas être modifiée dans l’administration ou modifie un paramètre déjà verrouillé dans l’administration. La commande écrit la valeur dans le fichier `<Commerce base dir>/app/etc/env.php`. |
| `-c or --lock-config` | Verrouille la valeur afin qu’elle ne puisse pas être modifiée dans l’administration ou modifie un paramètre déjà verrouillé dans l’administration. La commande écrit la valeur dans le fichier `<Commerce base dir>/app/etc/config.php`. L’option `--lock-config` remplace `--lock-env` si vous spécifiez les deux options. |
| `path` | _Obligatoire_. Chemin de configuration |
| `value` | _Obligatoire_. Valeur de la configuration. Bien qu’il puisse être transmis en tant qu’argument distinct dans une commande d’interface de ligne de commande, Adobe vous recommande de ne pas le spécifier dans la commande d’origine. Exécutez plutôt la commande sans la valeur , puis saisissez la valeur lorsque vous y êtes invité. L’utilisation de cette méthode empêche l’écriture de valeurs d’accès sensibles dans bash_history, ce qui est le moyen le plus sûr de définir la configuration. |

>[!INFO]
>
>Depuis Commerce version 2.2.4, les options `--lock-env` et `--lock-config` remplacent l’option `--lock`.
>
>Si vous utilisez l’option `--lock-env` ou `--lock-config` pour définir ou modifier une valeur, vous devez utiliser la commande [`bin/magento app:config:import`](../cli/import-configuration.md) pour importer le paramètre avant d’accéder à Admin ou Storefront.

Si vous saisissez un chemin de configuration incorrect, cette commande renvoie une erreur

```text
The "wrong/config/path" does not exist
```

Pour plus d’informations, consultez l’une des sections suivantes :

- [Définir des valeurs de configuration qui peuvent être modifiées dans l’administration](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Définir des valeurs de configuration qui ne peuvent pas être modifiées dans l’administration](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Définir des valeurs de configuration qui peuvent être modifiées dans l’administration

Utilisez `bin/magento config:set` _without_ `--lock-env` ou `--lock-config` pour écrire la valeur dans la base de données. Les valeurs définies de cette manière peuvent être modifiées dans l’Administration.

Voici quelques exemples de définition d’une URL de base de magasin :

Définissez l’URL de base de la portée par défaut :

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Définissez l’URL de base du site web `base` :

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Définissez l’URL de base de la vue de magasin `test` :

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Définir des valeurs de configuration qui ne peuvent pas être modifiées dans l’administration

Si vous utilisez l’option `--lock-env` comme suit, la commande enregistre la valeur de configuration dans `<Commerce base dir>/app/etc/env.php` et désactive le champ permettant de modifier cette valeur dans Admin.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Vous pouvez utiliser l’option `--lock-env` pour définir des valeurs de configuration si Commerce n’est pas installé. Cependant, vous ne pouvez définir des valeurs que pour la portée par défaut.

>[!INFO]
>
>Le fichier `env.php` est spécifique au système. Vous ne devez pas le transférer vers un autre système. Vous pouvez l’utiliser pour remplacer les valeurs de configuration de la base de données. Par exemple, vous pouvez prendre une image mémoire de base de données d’un autre système et remplacer le `base_url` et d’autres valeurs afin de ne pas avoir à modifier la base de données.

Si vous utilisez l’option `--lock-config` comme suit, la valeur de configuration est enregistrée dans `<Commerce base dir>/app/etc/config.php`. Le champ permettant de modifier cette valeur dans l’Admin est désactivé.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Vous pouvez utiliser `--lock-config` pour définir des valeurs de configuration si Commerce n’est pas installé. Cependant, vous ne pouvez définir des valeurs que pour la portée par défaut.

>[!INFO]
>
>Vous pouvez transférer des `config.php` vers un autre système pour y utiliser les mêmes valeurs de configuration. Par exemple, si vous disposez d’un système de test, l’utilisation du même `config.php` signifie que vous n’avez pas à définir à nouveau les mêmes valeurs de configuration.

## Afficher la valeur des paramètres de configuration

Options de commande :

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

où

- `--scope` est la portée de la configuration (par défaut, site web, magasin). La valeur par défaut est `default`
- `--scope-code` est le code d’étendue de la configuration (code de site web ou code d’affichage du magasin)
- `path` est le chemin de configuration au format first_part/second_part/third_part/etc (_obligatoire_)

>[!INFO]
>
>La commande `bin/magento config:show` affiche les valeurs de toutes les [&#x200B; valeurs chiffrées &#x200B;](../reference/config-reference-sens.md) sous la forme d’une série d’astérisques : `**&#x200B;**&#x200B;**`.

### Exemples

**Pour afficher toutes les configurations enregistrées** :

```bash
bin/magento config:show
```

Résultat :

```
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**Pour afficher toutes les configurations enregistrées pour le site web `base`** :

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Résultat :

```
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**Pour afficher l’URL de base de la portée par défaut** :

```bash
bin/magento config:show web/unsecure/base_url
```

Résultat :

```
web/unsecure/base_url - http://example.com/
```

**Pour afficher l’URL de base du site web `base`** :

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Résultat :

```
web/unsecure/base_url - http://example-for-website.com/
```

**Pour afficher l’URL de base du magasin de `default`** :

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Résultat :

```
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>Le code d’étendue peut uniquement inclure des lettres (a-z ou A-Z), des chiffres (0-9) et des traits de soulignement (_). En outre, le premier caractère doit être une lettre. Si des majuscules ou des majuscules sont utilisées lors de la création d’une vue de site web ou de boutique, en interne, la correspondance est insensible à la casse pour s’adapter au remplacement des paramètres de configuration par le biais de variables d’environnement. Voir [&#x200B; Utilisation de variables d’environnement pour remplacer les paramètres de configuration](../reference/override-config-settings.md#environment-variables).

