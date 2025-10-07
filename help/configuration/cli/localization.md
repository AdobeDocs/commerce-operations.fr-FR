---
title: Dictionnaires de traduction et packages de langue
description: Découvrez comment générer des dictionnaires de traduction et créer des packages de langue pour Adobe Commerce. Découvrez la localisation et la configuration de la boutique multilingue.
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1441'
ht-degree: 0%

---

# Localisation

{{file-system-owner}}

Les traductions Commerce vous permettent de personnaliser et de localiser votre boutique pour plusieurs régions et marchés en générant :

- **Dictionnaires de traduction**, qui sont un moyen pratique de personnaliser ou de traduire _certains_ mots et expressions, tels que ceux d’un module ou d’un thème personnalisé.
- **Packages de langues** qui permettent de traduire _tout ou partie_ des mots et expressions dans l’application Commerce.

Voir [ Présentation des traductions ].

## Génération d’un dictionnaire de traduction

Vous pouvez générer un [dictionnaire de traduction] pour personnaliser les chaînes existantes, traduire des mots et des expressions dans un module personnalisé, localiser un thème ou créer des packages de langue.

Pour commencer la traduction, utilisez une commande pour générer un fichier CSV de dictionnaire avec une liste de tous les mots et expressions existants.

Pour générer le dictionnaire et commencer la traduction :

1. Extrayez les mots et expressions traduisibles des composants activés à l’aide de la commande de collection de traduction . Le contenu est extrait dans un fichier CSV.
1. Traduisez les mots et expressions existants. Vous pouvez ajouter d’autres termes personnalisés selon vos besoins.

   Vous disposez d’options pour utiliser le dictionnaire traduit :

1. Vous pouvez regrouper les dictionnaires de traduction dans un package de langue et fournir le package à l’administrateur du magasin Commerce.

1. Dans Admin, l’administrateur de magasin [configure les traductions].

Options de commande :

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

Le tableau suivant explique les paramètres et valeurs :

| Paramètre | Valeur | Obligatoire ? |
|--- |--- |--- |
| `<path to directory to translate>` | Chemin d’accès à un répertoire contenant du code traduisible ; en d’autres termes, des fichiers PHP, PHTML ou XML contenant des expressions à traduire.<br><br>L’outil commence à rechercher le chemin d’accès que vous avez saisi et recherche tous les fichiers et sous-répertoires qu’il contient.<br><br>N’utilisez pas ce paramètre si vous utilisez `-m --magento`. | Oui (dictionnaires), non (packages). |
| `-m --magento` | Obligatoire pour créer un package de langue à partir de ce dictionnaire de traduction. S’il est utilisé, recherche les répertoires contenant bin/magento. Cette option ajoute des thèmes ou des modules à chaque ligne du dictionnaire.<br><br>Voici un exemple :<br><br>« Aucun élément trouvé »,« Aucun élément trouvé »,module,Magento_Wishlist | Non |
| `-o --output="<path>"` | Indique le chemin d’accès absolu au système de fichiers et le nom de fichier du fichier CSV du dictionnaire de traduction à créer. La valeur saisie est sensible à la casse. Le nom du fichier CSV doit correspondre exactement au nom du paramètre régional, y compris la casse des caractères.<br><br>Si vous omettez ce paramètre, la sortie est redirigée vers stdout. | Non |

>[!INFO]
>
>Pour créer un module linguistique à partir d&#39;un dictionnaire de traduction, vous _devez_ utiliser l&#39;option `-m|--magento`.

### Instructions de traduction

Appliquez les règles suivantes lors de la traduction de mots et d’expressions :

- Modifiez uniquement le contenu de la deuxième colonne. Traduisez les phrases de l’anglais (`US`) dans la langue souhaitée.
- Lors de la création de dictionnaires pour les paramètres régionaux, utilisez les chaînes Commerce par défaut.
- Lors de la traduction, faites attention aux espaces réservés : `%1`, `%2`

Commerce utilise des espaces réservés pour insérer des valeurs contextuelles ; elles ne sont _pas_ utilisées pour les traductions. Par exemple :

```text
Product '%1' has been added to shopping cart.
```

Remplit avec une valeur :

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

L’expression obtenue doit contenir au moins un de chaque espace réservé. Supposons, par exemple, qu’il existe des espaces réservés de `%1` à `%3` dans l’expression d’origine. La traduction peut comporter autant d’espaces réservés que nécessaire dans n’importe quel ordre, mais il doit y avoir au moins une occurrence de `%1`, `%2` et `%3`. La traduction ne peut pas contenir de valeurs d’espace réservé non présentes dans la valeur d’origine (par exemple, `%4`, `%5`, etc.).

Exemple de traduction d’une expression :

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Créer un package de langue

Contrairement à un dictionnaire de traduction, vous pouvez traduire n’importe lequel ou l’ensemble des mots et des expressions de l’application Commerce à l’aide d’un package de langue. Vous pouvez traduire un composant particulier (un module ou un thème, par exemple) à l’aide d’un dictionnaire de traduction. [En savoir plus sur les packages de langue].

Cette section explique comment créer un package de langue, qui écrit des fichiers CSV dans des modules et des thèmes. Pour créer un package de langue, vous devez effectuer les tâches décrites dans les sections suivantes :

1. [Collecter et traduire des mots et des phrases](#generate-a-translation-dictionary). (Le paramètre `--magento` est obligatoire.)
1. [Exécutez la commande du package de langue](#run-the-language-package-command).
1. [Créer des répertoires et des fichiers](#create-directories-and-files).
1. (Facultatif) [Configurez plusieurs packages pour une langue](#configure-multiple-packages-for-a-language).

### Exécutez la commande du package de langue

Utilisation des commandes :

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

Le tableau suivant explique les paramètres et valeurs de la commande du package de langue :

| Paramètre | Valeur | Obligatoire ? |
|--- |--- |--- |
| `<source>` | Chemin d’accès absolu au système de fichiers et nom de fichier d’un fichier CSV contenant le dictionnaire de traduction combiné aux méta-informations nécessaires pour la répartition dans un package de langue.<br><br>Utilisez [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) pour créer le fichier CSV, puis créez le package de langue comme décrit dans la section [Création de répertoires et de fichiers](#m2devgde-xlate-files). | Oui |
| `<locale>` | [Identifiant ISO 639-1] (langue) et [ISO 3166] (pays) de la langue utilisée comme nom de fichier pour tous les fichiers CSV obtenus. Exemples : `de_DE`, `pt_PT`, `pt_BR`. | Oui |
| `-m --mode` | S’il existe un fichier cible, indique s’il faut remplacer le package de langue existant ou le fusionner avec le nouveau package de langue. La fusion remplace toutes les expressions qui existaient et en ajoute de nouvelles.<br><br>Valeurs : fusionner ou remplacer (par défaut). | Non |
| `-d --allow-duplicates` | Incluez cette option pour autoriser les doublons dans le module linguistique. Dans le cas contraire, la commande échoue avec une erreur si elle rencontre la même expression dans plusieurs entrées avec des traductions différentes. | Non |

### Créer des répertoires et des fichiers

Les packages de langue se trouvent dans un répertoire sous `app/i18n/<VendorName>` dans le système de fichiers Commerce avec le contenu suivant :

- Fichiers de licence requis
- `composer.json`
- `registration.php` qui [enregistre] le package de langue
- [`language.xml`](#language-package-languagexml) le fichier de méta-informations

>[!INFO]
>
>Vous devez mettre l’ensemble du chemin en minuscules. Par exemple, consultez la section [`de_de`].

Pour créer ces fichiers :

1. Créez un répertoire sous `app/i18n`.

   Par exemple, les packages de langue Commerce se trouvent dans `app/i18n/magento`

1. Ajoutez les fichiers de licence requis.
1. Ajoutez des [`composer.json`] qui spécifient les dépendances de votre package de langue.
1. Enregistrez le package de langue avec [`registration.php`]
1. Ajoutez `language.xml` fichier de méta-informations comme décrit dans la section suivante.

#### Package de langue language.xml

Lors de la déclaration d’un package de langue dans le fichier de configuration `language.xml`, vous devez spécifier la séquence d’héritage de langue de ce package.

L’héritage de langue vous permet de créer une traduction appelée _enfant_ basée sur une traduction existante appelée _parent_. Les traductions enfants remplacent les traductions parents. Cependant, si le chargement ou l’affichage de la traduction enfant échoue ou si une expression ou un mot est manquant, Commerce utilise le paramètre régional parent. [ Exemples d’héritage de package de langue ](#example-of-language-inheritance).

Pour déclarer un package, spécifiez les informations suivantes :

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

- `code`—Paramètres régionaux du package de langue (obligatoire)
- `vendor` : nom du fournisseur du module (obligatoire)
- `package` : nom du package de langue (obligatoire)
- `sort_order` : priorité de chargement d&#39;un package lorsqu&#39;un magasin dispose de plusieurs packages de langue
- `use`—Parent language package locale à partir duquel hériter les dictionnaires

Si nécessaire, vous pouvez spécifier plusieurs packages parents. Les packages parents sont appliqués sur la base Première utilisation répertoriée.

#### Exemple d’héritage de langue

Supposons qu’un package de langue hérite de deux autres packages et que ces packages aient également des packages parents et « grands-parents ».

Si un package de langue hérite de deux packages, son `language.xml` peut se présenter comme suit :

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

Dans l&#39;exemple précédent:

- `language_package_one` hérite de `en_au_package` et `en_au_package` de `en_ie_package`
- `language_package_two` hérite de `en_ca_package` et `en_ca_package` de `en_us_package`

Si l’application Commerce ne trouve pas de mot ou d’expression dans le package `en_GB`, elle recherche dans d’autres packages dans l’ordre suivant :

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

La spécification de tous les héritages entre les packages de langue peut entraîner la création de chaînes d’héritage circulaires. Utilisez le test [Magento\Test\Integrity\App\Language\CircularDependencyTest] pour localiser et corriger ces chaînes.

### Configuration de plusieurs packages pour une langue

Pour rendre votre boutique plus flexible, vous pouvez charger plusieurs packages de langue pour la même langue dans votre boutique. Ainsi, vous pouvez utiliser différents packages personnalisés pour différentes parties de votre magasin, car le système compile un seul package à partir de tous les packages disponibles pour une langue.

Pour activer un package supplémentaire pour une langue existante, donnez au nouveau package tout nom à l’exception d’un nom de code de langue existant (pour éviter toute confusion). Spécifiez les configurations d’un package dans le fichier de méta-informations `language.xml` du package de langue, comme décrit dans la section suivante.

## Exemples d’utilisation des commandes de traduction

Les sections suivantes fournissent des exemples complets d’utilisation des commandes décrites dans cette rubrique pour créer des dictionnaires et des packages de traduction :

### Exemple : créez un dictionnaire de traduction pour un module ou un thème

Pour ajouter une traduction allemande à un module ou un thème que vous souhaitez distribuer à d&#39;autres commerçants :

1. Collecter des expressions de votre module :

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >Le nom du fichier CSV doit _correspondre exactement_ au paramètre régional, y compris la casse des caractères.

1. Traduisez les mots et les expressions à l’aide de [ces directives](#translation-guidelines).
1. Si nécessaire, copiez `xx_YY.csv` dans `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` ou dans le répertoire des thèmes du module (selon que le dictionnaire de traduction correspond à un module ou à un thème).

### Exemple : créer un package de langue

Comme dans l’exemple précédent, générez un fichier CSV, mais au lieu de spécifier un répertoire de module ou de thème, spécifiez l’ensemble du répertoire racine de l’application Commerce. Le fichier CSV obtenu contient toutes les expressions que la commande peut trouver dans le code.

1. Collecter des expressions de votre module :

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >Le nom du fichier CSV doit _correspondre exactement_ au paramètre régional, y compris la casse des caractères.

1. Traduisez les mots et les expressions à l’aide de [ces directives](#translation-guidelines).
1. Créez le package de langue.

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. Créez un répertoire pour le package de langue.

   Par exemple, `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. Dans ce répertoire, ajoutez tous les éléments suivants :

   - Une licence, si nécessaire
   - `composer.json` (exemple de code suivant)
   - `registration.php` (exemple de code suivant)
   - `language.xml` (exemple de code suivant)

   **Exemple de`composer.json`** :

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

   **Exemple de`registration.php`** :

   ```php
   <?php
   /**
    * Copyright [first year code created] Adobe
    * All Rights Reserved.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **Exemple de`language.xml`** :

   ```xml
   <?xml version="1.0"?>
   <!--
   Copyright [first year code created] Adobe
   All Rights Reserved.
   -->
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[Présentation des traductions]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[dictionnaire de traduction]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[configure les traductions]: https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/store-localize
[En savoir plus sur les packages de langue]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[registres]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[`de_de`]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[`compositeur.json`]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[`registration.php`]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
