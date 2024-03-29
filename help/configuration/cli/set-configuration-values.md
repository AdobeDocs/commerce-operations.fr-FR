---
title: Définition des valeurs de configuration
description: Découvrez comment définir des valeurs de configuration et modifier des valeurs verrouillées dans Admin.
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 473ab09f83a4cfc1809adff854d52a11ad49d3af
workflow-type: tm+mt
source-wordcount: '1038'
ht-degree: 0%

---

# Définition des valeurs de configuration

{{file-system-owner}}

Cette rubrique décrit les commandes de configuration avancées que vous pouvez utiliser pour :

- Définissez toute option de configuration à partir de la ligne de commande.
- Vous pouvez éventuellement verrouiller toute option de configuration de sorte que sa valeur ne puisse pas être modifiée dans l’administrateur.
- Modification d’une option de configuration verrouillée dans l’Admin

Vous pouvez utiliser ces commandes pour définir la configuration de Commerce manuellement ou à l’aide de scripts. Vous pouvez définir des options de configuration à l’aide d’une _chemin de configuration_, qui est un `/`Chaîne délimitée par des caractères qui identifie de manière unique cette option de configuration. Vous trouverez des chemins de configuration dans les références suivantes :

- [Référence des chemins de configuration sensibles et spécifiques au système](../reference/config-reference-sens.md)
- [Référence des chemins de configuration des paiements](../reference/config-reference-payment.md)
- [Référence générale sur les chemins de configuration](../reference/config-reference-general.md)
- [Référence sur les chemins de configuration de l’extension B2B de Commerce Enterprise](../reference/config-reference-b2b.md)

Vous pouvez définir des valeurs aux moments suivants :

- Avant d’installer Commerce, vous pouvez définir des valeurs de configuration pour la portée par défaut uniquement, car il s’agit de la seule portée valide.

- Après avoir installé Commerce, vous pouvez définir des valeurs de configuration pour n’importe quel site web ou stocker la portée de la vue.

Utilisez les commandes suivantes :

- `bin/magento config:set` définit toute valeur de configuration non sensible en fonction de son chemin de configuration ;
- `bin/magento config:sensitive:set` définit toute valeur de configuration sensible en fonction de son chemin de configuration ;
- `bin/magento config:show` affiche les valeurs de configuration enregistrées ; les valeurs des paramètres chiffrés sont affichées sous la forme d’astérisques.

## Conditions préalables

Pour définir une valeur de configuration, vous devez connaître au moins l’un des éléments suivants :

- Chemin de configuration
- Pour définir une valeur de configuration pour une portée particulière, vous devez connaître le code de portée.

  Pour définir une valeur de configuration pour la portée par défaut, il n’est pas nécessaire de faire quoi que ce soit.

### Recherche du chemin de configuration

Voir les références suivantes :

- [Référence des chemins de configuration sensibles et spécifiques au système](../reference/config-reference-sens.md)
- [Référence des chemins de configuration des paiements](../reference/config-reference-payment.md)
- [Autres références de chemins de configuration](../reference/config-reference-general.md)
- [Référence sur les chemins de configuration de l’extension B2B de Commerce Enterprise](../reference/config-reference-b2b.md)

### Recherche du code d’étendue

Vous pouvez trouver le code de portée dans la base de données Commerce ou dans l’administrateur Commerce.

**Pour trouver le code de portée dans l’Admin**:

1. Connectez-vous à l’administrateur en tant qu’utilisateur capable d’afficher des sites web et de stocker les vues.
1. Cliquez sur **[!UICONTROL Stores]** > Paramètres > **[!UICONTROL All Stores]**.
1. Dans le volet de droite, cliquez sur le nom du site web ou de la vue de magasin pour afficher son code.

   La figure suivante illustre un exemple de code de site web.

   ![Obtention d’un site web ou d’un code d’affichage de magasin auprès de l’administrateur](../../assets/configuration/website-code.png)

1. Passez à la [Définir des valeurs](#set-values).

**Pour trouver le code de portée dans la base de données**:

Les codes d’étendue pour les sites web et les vues de magasin sont stockés dans la base de données Commerce de la variable `store_website` et `store` , respectivement.

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

   ```terminal
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   Utilisez la valeur de la variable `code` colonne .

1. Passez à la section suivante.

## Définir des valeurs

**Pour définir des valeurs de configuration spécifiques au système**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**Pour définir des valeurs de configuration sensibles**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

Le tableau suivant décrit la variable `set` paramètres de commande :

| Paramètre | Description |
| --- | --- |
| `--scope` | Portée de la configuration. Les valeurs possibles sont : `default`, `website`, ou `store`. La valeur par défaut est `default`. |
| `--scope-code` | Le code d’étendue de la configuration (code du site web ou code d’affichage de magasin) |
| `-e or --lock-env` | Verrouille la valeur afin qu’elle ne puisse pas être modifiée dans l’administrateur ou modifie un paramètre déjà verrouillé dans l’administrateur. La commande écrit la valeur dans la variable `<Commerce base dir>/app/etc/env.php` fichier . |
| `-c or --lock-config` | Verrouille la valeur afin qu’elle ne puisse pas être modifiée dans l’administrateur ou modifie un paramètre déjà verrouillé dans l’administrateur. La commande écrit la valeur dans la variable `<Commerce base dir>/app/etc/config.php` fichier . La variable `--lock-config` option remplace `--lock-env` si vous spécifiez les deux options. |
| `path` | _Obligatoire_. Chemin de configuration |
| `value` | _Obligatoire_. La valeur de la configuration |

>[!INFO]
>
>À compter de Commerce 2.2.4, la variable `--lock-env` et `--lock-config` les options remplacent la variable `--lock` .
>
>Si vous utilisez la variable `--lock-env` ou `--lock-config` pour définir ou modifier une valeur, vous devez utiliser la variable [`bin/magento app:config:import` command](../cli/import-configuration.md) pour importer le paramètre avant d’accéder à l’administrateur ou au storefront.

Si vous saisissez un chemin de configuration incorrect, cette commande renvoie une erreur.

```text
The "wrong/config/path" does not exist
```

Pour plus d’informations, reportez-vous à l’une des sections suivantes :

- [Définition de valeurs de configuration pouvant être modifiées dans l’élément Admin](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Définition des valeurs de configuration qui ne peuvent pas être modifiées dans l’élément Admin](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Définition de valeurs de configuration pouvant être modifiées dans l’élément Admin

Utilisation `bin/magento config:set` _without_ `--lock-env` ou `--lock-config` pour écrire la valeur dans la base de données. Les valeurs définies de cette manière peuvent être modifiées dans l’Admin.

Voici quelques exemples de définition d’une URL de base de magasin :

Définissez l’URL de base de la portée par défaut :

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Définissez l’URL de base de la variable `base` site web :

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Définissez l’URL de base de la variable `test` vue de magasin :

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Définition des valeurs de configuration qui ne peuvent pas être modifiées dans l’élément Admin

Si vous utilisez la variable `--lock-env`  , la commande enregistre la valeur de configuration dans `<Commerce base dir>/app/etc/env.php` et désactive le champ permettant de modifier cette valeur dans l’Admin.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Vous pouvez utiliser la variable `--lock-env` pour définir les valeurs de configuration si Commerce n’est pas installé. Cependant, vous ne pouvez définir des valeurs que pour la portée par défaut.

>[!INFO]
>
>La variable `env.php` est spécifique au système. Vous ne devez pas le transférer vers un autre système. Vous pouvez l’utiliser pour remplacer les valeurs de configuration de la base de données. Par exemple, vous pouvez extraire un vidage de base de données d’un autre système et remplacer le `base_url` et d’autres valeurs afin que vous n’ayez pas à modifier la base de données.

Si vous utilisez la variable `--lock-config` comme suit, la valeur de configuration est enregistrée dans `<Commerce base dir>/app/etc/config.php`. Le champ permettant de modifier cette valeur dans Admin est désactivé.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Vous pouvez utiliser `--lock-config` pour définir les valeurs de configuration si Commerce n’est pas installé. Cependant, vous ne pouvez définir des valeurs que pour la portée par défaut.

>[!INFO]
>
>Vous pouvez transférer `config.php` à un autre système pour utiliser les mêmes valeurs de configuration. Par exemple, si vous disposez d’un système de test, utilisez le même `config.php` signifie que vous n’avez pas à définir à nouveau les mêmes valeurs de configuration.

## Afficher la valeur des paramètres de configuration

Options de commande :

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

where

- `--scope` est la portée de la configuration (par défaut, site web, magasin). La valeur par défaut est `default`
- `--scope-code` est le code d’étendue de la configuration (code du site web ou code d’affichage de magasin).
- `path` est le chemin de configuration au format first_part/second_part/third_part/etc (_required_)

>[!INFO]
>
>La variable `bin/magento config:show` affiche les valeurs des [valeurs cryptées](../reference/config-reference-sens.md) sous la forme d’une série d’astérisques : `******`.

### Exemples

**Pour afficher toutes les configurations enregistrées**:

```bash
bin/magento config:show
```

Résultat :

```terminal
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**Pour afficher toutes les configurations enregistrées pour la variable `base` site web**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Résultat :

```terminal
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**Pour afficher l’URL de base de la portée par défaut**:

```bash
bin/magento config:show web/unsecure/base_url
```

Résultat :

```terminal
web/unsecure/base_url - http://example.com/
```

**Pour afficher l’URL de base de la variable `base` site web**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Résultat :

```terminal
web/unsecure/base_url - http://example-for-website.com/
```

**Pour afficher l’URL de base de la variable `default` store**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Résultat :

```terminal
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>Le code de portée peut inclure uniquement des lettres (a-z ou A-Z), des chiffres (0-9) et des traits de soulignement (_). En outre, le premier caractère doit être une lettre. Si des majuscules ou des majuscules sont utilisées lors de la création d’un site web ou d’une vue de magasin, la correspondance n’est pas sensible à la casse en interne afin de permettre le remplacement des paramètres de configuration par le biais de variables d’environnement. Voir [Utilisation des variables d’environnement pour remplacer les paramètres de configuration](../reference/override-config-settings.md#environment-variables).

