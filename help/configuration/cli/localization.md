---
title: Dictionnaires de traduction et packages de langue
description: Découvrez comment générer des dictionnaires de traduction et créer des packages de langue.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 0%

---


# Localisation

{{file-system-owner}}

Les traductions de commerce vous permettent de personnaliser et de localiser votre boutique pour plusieurs régions et marchés en générant :

- **Dictionnaires de traduction**, qui sont un moyen pratique de personnaliser ou de traduire _some_ mots et expressions, comme ceux d’un module ou d’un thème personnalisé.
- **Packages de langues** qui vous permettent de traduire _tout ou tout_ mots et expressions dans l’application Commerce.

Voir [Présentation des traductions].

## Générer un dictionnaire de traduction

Vous pouvez générer une [dictionnaire de traduction] pour personnaliser des chaînes existantes, traduire des mots et des expressions dans un module personnalisé, localiser un thème ou créer [packages de langue](https://glossary.magento.com/language-package).

Pour commencer la traduction, utilisez une commande pour générer un fichier CSV de dictionnaire avec une liste collectée de tous les mots et expressions existants.

Pour générer le dictionnaire et commencer la traduction :

1. Extrayez les mots et expressions traduisibles des composants activés à l’aide de la commande de collection de traduction. Le contenu est extrait dans un fichier CSV.
1. Traduisez les mots et expressions existants. Vous pouvez ajouter d’autres termes personnalisés, si nécessaire.

   Vous disposez d’options pour utiliser le dictionnaire traduit :

1. Vous pouvez regrouper les dictionnaires de traduction dans un module de langue et fournir le module à l’administrateur de la boutique de commerce.

1. Dans l’administrateur, l’administrateur de magasin [configure les traductions].

Options de commande :

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

Le tableau suivant explique les paramètres et les valeurs :

| Paramètre | Valeur | Obligatoire ? |
|--- |--- |--- |
| `<path to directory to translate>` | Chemin d’accès à un répertoire comportant du code traduisible ; en d’autres termes, des fichiers PHP, PHTML ou XML contenant des expressions à traduire.<br><br>L’outil commence la recherche à partir du chemin d’accès que vous saisissez et recherche tous les fichiers et sous-répertoires qu’il contient.<br><br>N’utilisez pas ce paramètre si vous utilisez `-m --magento`. | Oui (dictionnaires), non (packages). |
| `-m --magento` | Requis pour créer un module de langue à partir de ce dictionnaire de traduction. En cas d’utilisation, recherche les répertoires contenant bin/magento. Cette option ajoute des thèmes ou des modules à chaque ligne du dictionnaire.<br><br>Voici un exemple :<br><br>&quot;Aucun élément trouvé&quot;, &quot;Aucun élément trouvé&quot;, module, Magento_Wishlist | Non |
| `-o --output="<path>"` | Indique le chemin d’accès absolu au système de fichiers et le nom de fichier du fichier CSV du dictionnaire de traduction à créer. La valeur saisie est sensible à la casse. Le nom du fichier CSV doit correspondre exactement au nom du paramètre régional, y compris la casse des caractères.<br><br>Si vous omettez ce paramètre, la sortie est redirigée vers stdout. | Non |

>[!INFO]
>
>Pour créer un module de langue à partir d’un dictionnaire de traduction, vous devez : _must_ utilisez la méthode `-m|--magento` .

### Instructions de traduction

Suivez les instructions ci-dessous pour traduire des mots et des expressions :

- Modifiez uniquement le contenu de la seconde colonne. Traduisez les expressions en anglais (`US`) dans la langue souhaitée.
- Lors de la création de dictionnaires pour les paramètres régionaux, utilisez les chaînes Commerce par défaut.
- Lors de la traduction, prêtez attention aux espaces réservés : `%1`, `%2`

Commerce utilise des espaces réservés pour insérer des valeurs contextuelles ; they are _not_ utilisé pour les traductions. Par exemple :

```text
Product '%1' has been added to shopping cart.
```

Remplit avec une valeur :

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

L’expression résultante doit contenir au moins un espace réservé. Supposons, par exemple, qu’il existe des espaces réservés issus de `%1` to `%3` dans l’expression d’origine. La traduction peut avoir autant d’espaces réservés dans n’importe quel ordre, mais il doit y avoir au moins une occurrence de `%1`, `%2`, et `%3`. La traduction ne peut pas contenir d’espaces réservés qui ne sont pas présents dans la valeur d’origine (par exemple, `%4`, `%5`, etc.).

Exemple de traduction d’une expression :

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Créer un package de langue

Contrairement à un dictionnaire de traduction, vous pouvez traduire n’importe quel ou tous les mots et expressions de l’application Commerce à l’aide d’un module de langue. Vous pouvez traduire un composant particulier, tel qu’un module ou un thème, à l’aide d’un dictionnaire de traduction. [En savoir plus sur les packages de langue].

Cette section explique comment créer un module de langue, qui écrit des fichiers CSV dans des modules et des thèmes. Pour créer un package de langue, vous devez effectuer les tâches décrites dans les sections suivantes :

1. [Collecte et traduction de mots et d’expressions](#generate-a-translation-dictionary). (La variable `--magento` est obligatoire.)
1. [Exécution de la commande du module de langue](#run-the-language-package-command).
1. [Création de répertoires et de fichiers](#create-directories-and-files).
1. (Facultatif.) [Configuration de plusieurs packages pour une langue](#configure-multiple-packages-for-a-language).

### Exécution de la commande du module de langue

Utilisation des commandes :

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

Le tableau suivant explique les paramètres et valeurs de la commande du module de langue :

| Paramètre | Valeur | Obligatoire ? |
|--- |--- |--- |
| `<source>` | Chemin d’accès absolu au système de fichiers et nom de fichier d’un fichier CSV contenant le dictionnaire de traduction combiné et les méta-informations nécessaires à la ventilation dans un module de langue.<br><br>Utilisation [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) pour créer le fichier CSV, puis créez le module de langue comme décrit dans [Création de répertoires et de fichiers](#m2devgde-xlate-files). | Oui |
| `<locale>` | [ISO 639-1] (langue) et [ISO 3166] (pays) identifiant de la langue utilisée comme nom de fichier pour tous les fichiers CSV obtenus. Exemples : `de_DE`, `pt_PT`, `pt_BR`. | Oui |
| `-m --mode` | Si un fichier cible existe, indique s’il faut remplacer le module de langue existant ou le fusionner avec le nouveau module de langue. La fusion remplace toutes les expressions qui existaient et en ajoute de nouvelles.<br><br>Valeurs : fusionner ou remplacer (par défaut). | Non |
| `-d --allow-duplicates` | Incluez cette option pour autoriser les doublons dans le module de langue. Sinon, la commande échoue avec une erreur si elle rencontre la même expression dans plusieurs entrées avec des traductions différentes. | Non |

### Création de répertoires et de fichiers

Les modules de langue se trouvent dans un répertoire sous `app/i18n/<VendorName>` dans le système de fichiers Commerce avec les contenus suivants :

- Fichiers de licence requis
- `composer.json`
- `registration.php` that [registres] le package de langue
- [`language.xml`](#language-package-languagexml) fichier de méta-information

>[!INFO]
>
>Vous devez mettre le chemin en minuscules. Par exemple, reportez-vous à la section [`de_de`].

Pour créer ces fichiers :

1. Créez un répertoire sous `app/i18n`.

   Par exemple, les modules de langue Commerce se trouvent dans `app/i18n/magento`

1. Ajoutez les fichiers de licence requis.
1. Ajouter [`composer.json`] qui spécifie les dépendances pour votre module de langue.
1. Enregistrez le package de langue avec [`registration.php`]
1. Ajouter `language.xml` fichier de méta-information, comme décrit dans la section suivante.

#### Language Package language.xml

Lors de la déclaration d’un module de langue dans la variable `language.xml` fichier de configuration, vous devez spécifier la séquence d’héritage de langue pour ce module.

L’héritage de langue vous permet de créer une traduction appelée _child_ sur la base d’une traduction existante appelée _parent_. Les traductions enfants remplacent le parent. Cependant, si la traduction enfant ne parvient pas à charger ou à afficher ou si une expression ou un mot manque, Commerce utilise le parent [locale](https://glossary.magento.com/locale). [Exemples d’héritage de package de langue](#example-of-language-inheritance).

Pour déclarer un package, indiquez les informations suivantes :

```xml
<?xml version="1.0"?>
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>en_gb</package>
    <sort_order>100</sort_order>
    <use vendor="oxford-university" package="en_us"/>
</language>
```

Où :

- `code`—Paramètre régional du package de langue (obligatoire)
- `vendor`—Nom du fournisseur du module (obligatoire)
- `package`—Nom du package de langue (obligatoire)
- `sort_order`: priorité de chargement d’un module lorsqu’il existe plusieurs modules de langue disponibles pour un magasin.
- `use`: paramètre régional du package de langue parente à partir duquel hériter des dictionnaires

Si nécessaire, vous pouvez spécifier plusieurs packages parents. Les packages parents sont appliqués sur la première base répertoriée, la première utilisée.

#### Exemple d’héritage de langue

Supposons qu’un module de langue hérite de deux autres modules et que ces derniers possèdent également des modules parents et &quot;grand-parents&quot;.

Si un module de langue hérite de deux modules, son `language.xml` peut se présenter comme suit :

```xml
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>language_pack</package>
    <sort_order>100</sort_order>
    <use vendor="parent-package-one" package="language_package_one"/>
    <use vendor= "parent-package-two" package="language_package_two"/>
</language>
```

Dans l’exemple précédent :

- `language_package_one` hérite de `en_au_package` et `en_au_package` hérite de `en_ie_package`
- `language_package_two` hérite de `en_ca_package` et `en_ca_package` hérite de `en_us_package`

Si l’application Commerce ne trouve pas de mot ou d’expression dans la variable `en_GB` module, il recherche dans d’autres modules dans l’ordre suivant :

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

La spécification de tous les héritages entre les packages de langue peut entraîner la création de chaînes d’héritage circulaires. Utilisation [Magento\Test\Integrity\App\Language\CircularDependencyTest] tester pour localiser et corriger de telles chaînes.

### Configuration de plusieurs packages pour une langue

Pour vous aider à rendre votre boutique plus flexible, vous pouvez charger plusieurs modules de langue pour la même langue dans votre boutique. Ainsi, vous pouvez utiliser différents packages personnalisés pour différentes parties de votre magasin, car le système compile un seul package à partir de tous les packages disponibles pour une langue.

Pour activer un module supplémentaire pour une langue existante, nommez le nouveau module sous un nom quelconque, à l’exception d’un nom de code de langue existant (afin d’éviter toute confusion). Spécifier les configurations d’un module dans le `language.xml` fichier de méta-information, comme décrit dans la section suivante.

## Exemples d’utilisation des commandes de traduction

Les sections suivantes fournissent des exemples de bout en bout d’utilisation des commandes abordées dans cette rubrique pour créer des dictionnaires de traduction et des packages de traduction :

### Exemple : Création d’un dictionnaire de traduction pour un module ou un thème

Pour ajouter une traduction allemande à un module ou à un thème que vous souhaitez distribuer à d’autres commerçants :

1. Collectez des expressions à partir de votre module :

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >Le nom du fichier CSV doit _correspond exactement_ le paramètre régional, y compris la casse des caractères.

1. Traduisez les mots et expressions à l’aide de [ces instructions](#translation-guidelines).
1. Si nécessaire, copiez `xx_YY.csv` to `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` ou au répertoire de thèmes du module (selon que le dictionnaire de traduction est pour un module ou un thème).

### Exemple : Créer un package de langue

Comme dans l’exemple précédent, générez un fichier CSV, mais au lieu de spécifier un répertoire de module ou de thème, spécifiez le répertoire racine de l’application Commerce entier. Le fichier CSV obtenu contient toutes les expressions que la commande peut trouver dans le code.

1. Collectez des expressions à partir de votre module :

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >Le nom du fichier CSV doit _correspond exactement_ le paramètre régional, y compris la casse des caractères.

1. Traduisez les mots et expressions à l’aide de [ces instructions](#translation-guidelines).
1. Créez le package de langue.

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. Créez un répertoire pour le module de langue.

   Par exemple, `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. Dans ce répertoire, ajoutez tous les éléments suivants :

   - Une licence, le cas échéant
   - `composer.json` (exemple de suivi)
   - `registration.php` (exemple de suivi)
   - `language.xml` (exemple de suivi)

   **Exemple`composer.json`**:

   ```json
   {
       "name": "examplecorp/language-xx_yy",
       "description": "Sample language",
       "version": "100.0.2",
       "license": [
           "OSL-3.0",
           "AFL-3.0"
       ],
       "require": {
           "magento/framework": "100.0.*"
       },
       "type": "magento2-language",
       "autoload": {
           "files": [
               "registration.php"
           ]
       }
   }
   ```

   **Exemple`registration.php`**:

   ```php
   <?php
   /**
    * Copyright © Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **Exemple`language.xml`**:

   ```xml
   <?xml version="1.0"?>
   /**
   * Copyright © Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
   
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[Translate theme strings]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/translate_theory.html
[Présentation des traductions]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html
[Community Engineering contributions]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#translations-project
[dictionnaire de traduction]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#m2devgde-xlate-dictionaries
[configure les traductions]: https://docs.magento.com/user-guide/stores/store-language-add.html?Highlight=translation
[En savoir plus sur les packages de langue]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#m2devgde-xlate-languagepack
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[registres]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/component-registration.html
[`de_de`]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[`composer.json`]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/composer-integration.html
[`registration.php`]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/component-registration.html
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
