---
title: Dictionnaires de traduction et modules linguistiques
description: Apprenez à générer des dictionnaires de traduction et à créer des packages linguistiques.
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 0%

---

# Localisation

{{file-system-owner}}

Les traductions commerciales vous permettent de personnaliser et de localiser votre boutique pour plusieurs régions et marchés en générant :

- **Les dictionnaires** de traduction, qui sont un moyen pratique de personnaliser ou de traduire _certains_ mots et phrases, tels que ceux d’un module personnalisé ou d’un thème.
- **Packages de langues** qui vous permettent de traduire _tous les_ mots et expressions dans l’application Commerce.

Voir [Présentation des traductions].

## Génération d’un dictionnaire de traduction

Vous pouvez générer un [dictionnaire de traduction] pour personnaliser des chaînes existantes, traduire des mots et des expressions dans un module personnalisé, localiser un thème ou créer des modules de langue.

Pour commencer la traduction, utilisez une commande pour générer un fichier CSV de dictionnaire avec une liste collectée de toutes les phrases et mots existants.

Pour générer le dictionnaire et commencer la traduction :

1. Extract des mots et des expressions traduisibles à partir de composants activés à l’aide de la commande Translation Collection. Le contenu est extrait dans un fichier CSV.
1. Traduisez les mots et expressions existants. Vous pouvez ajouter d’autres termes personnalisés, si nécessaire.

   Vous disposez d’options pour utiliser le dictionnaire traduit :

1. Vous pouvez regrouper les dictionnaires de traduction dans un module de langue et fournir le module à l’administrateur de magasin Commerce.

1. Dans l’administrateur, l’administrateur [du magasin configure les traductions].

Options de commande :

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

Le tableau suivant décrit les paramètres et les valeurs :

| Paramètre | Valeur | Obligatoire? |
|--- |--- |--- |
| `<path to directory to translate>` | Chemin d’accès à un répertoire comportant du code traduisible, c’est-à-dire des fichiers PHP, PHTML ou XML ayant des expressions à traduire.<br><br>L’outil commence à rechercher le chemin que vous entrez et recherche tous les fichiers et sous-répertoires qu’il contient.<br><br>N’utilisez pas ce paramètre si vous utilisez `-m --magento`. | Oui (dictionnaires), non (packages). |
| `-m --magento` | Requis pour créer un module de langue à partir de ce dictionnaire de traduction. En cas d’utilisation, recherche les répertoires contenant bin/magento. Cette option ajoute des thèmes ou des modules à chaque ligne du dictionnaire.<br><br>Voici un exemple :<br><br>&quot;Aucun élément trouvé »,&quot;Aucun élément trouvé »,module,Magento_Liste de souhaits | Non |
| `-o --output="<path>"` | Spécifie le chemin d’accès absolu au système de fichiers et le nom de fichier du fichier CSV du dictionnaire de traduction à créer. La valeur que vous entrez est sensible à la casse. Le nom du fichier CSV doit correspondre exactement au nom du paramètre régional, y compris la casse des caractères.<br><br>Si vous omettez ce paramètre, la sortie est dirigée vers stdout. | Non |

>[!INFO]
>
>Pour créer un module de langue à partir d’un dictionnaire de traduction, vous _devez_ utiliser l’option `-m|--magento` .

### Instructions de traduction

Suivez les instructions ci-dessous pour traduire des mots et des expressions :

- Modifiez uniquement le contenu de la seconde colonne. Traduisez les expressions de l’anglais (`US`) dans la langue souhaitée.
- Lors de la création de dictionnaires pour les paramètres régionaux, utilisez les chaînes Commerce par défaut.
- Lors de la traduction, prêtez attention aux espaces réservés : `%1`, `%2`

Commerce utilise des espaces réservés pour insérer des valeurs contextuelles. Elles sont _et non_ utilisées pour les traductions. Par exemple :

```text
Product '%1' has been added to shopping cart.
```

Remplit avec une valeur :

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

L’expression résultante doit contenir au moins un espace réservé. Par exemple, supposons qu’il existe des espaces réservés entre `%1` et `%3` dans l’expression d’origine. La traduction peut avoir autant d’espaces réservés dans n’importe quel ordre, mais il doit y avoir au moins une occurrence de `%1`, `%2` et `%3`. La traduction ne peut pas contenir de valeurs d’espace réservé non présentes dans la valeur d’origine (par exemple, `%4`, `%5`, etc.).

Exemple de traduction d’une phrase :

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Créer un module linguistique

Contrairement à un dictionnaire de traduction, vous pouvez traduire tout ou partie des mots et expressions de l’application Commerce à l’aide d’un package de langue. Vous pouvez traduire un composant particulier, tel qu’un module ou un thème, à l’aide d’un dictionnaire de traduction. [En savoir plus sur les packages linguistiques].

Cette section explique comment créer un package de langage, qui écrit des fichiers CSV dans des modules et des thèmes. Pour créer un package linguistique, vous devez exécuter les tâches décrites dans les sections suivantes :

1. [Collecter et traduire des mots et des expressions](#generate-a-translation-dictionary). (Le paramètre `--magento` est requis.)
1. [Exécutez la commande de module de langue](#run-the-language-package-command).
1. [ Créez des répertoires et des fichiers ](#create-directories-and-files).
1. (Facultatif) [Configurez plusieurs packages pour une langue](#configure-multiple-packages-for-a-language).

### Exécution de la commande du module de langue

Utilisation des commandes :

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

Le tableau suivant explique les paramètres et valeurs de la commande du module de langue :

| Paramètre | Valeur | Obligatoire ? |
|--- |--- |--- |
| `<source>` | Chemin d’accès absolu au système de fichiers et nom de fichier d’un fichier CSV contenant le dictionnaire de traduction combiné et les méta-informations nécessaires à la ventilation dans un package de langue.<br><br>Utilisez [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) pour créer le fichier CSV, puis créez le package linguistique comme indiqué dans [Créer des répertoires et des fichiers](#m2devgde-xlate-files). | Oui |
| `<locale>` | [Identifiant ISO 639-1] (langue) et [ISO 3166] (pays) de la langue utilisée comme nom de fichier pour tous les fichiers CSV résultants. Exemples : `de_DE`, `pt_PT`, `pt_BR`. | Oui |
| `-m --mode` | Si un fichier cible existe, indique s’il faut remplacer le module de langue existant ou le fusionner avec le nouveau module de langue. La fusion remplace toutes les expressions qui existaient et en ajoute de nouvelles.<br><br>Valeurs : fusionner ou remplacer (par défaut). | Non |
| `-d --allow-duplicates` | Incluez cette option pour autoriser les doublons dans le module de langue. Dans le cas contraire, la commande échoue avec une erreur si elle rencontre la même expression dans plusieurs entrées avec des traductions différentes. | Non |

### Création de répertoires et de fichiers

Les modules linguistiques se trouvent dans un répertoire sous `app/i18n/<VendorName>` dans le système de fichiers Commerce avec le contenu suivant :

- Fichiers de licence requis
- `composer.json`
- `registration.php` que [enregistre] le package de langue
- [`language.xml`](#language-package-languagexml) fichier de méta-information

>[!INFO]
>
>Vous devez mettre le chemin en minuscules. Par exemple, reportez-vous à la section [`de_de`].

Pour créer ces fichiers :

1. Créez un répertoire sous `app/i18n`.

   Par exemple, les packages de langues Commerce se trouvent dans `app/i18n/magento`

1. Ajoutez les fichiers de licence requis.
1. Ajoutez [`composer.json`] qui spécifie les dépendances de votre module linguistique.
1. Enregistrez le module linguistique auprès de [`registration.php`]
1. Ajoutez le fichier de métadonnées `language.xml` comme décrit dans la section suivante.

#### Language Package language.xml

Lors de la déclaration d’un package de langue dans le fichier de configuration `language.xml`, vous devez spécifier la séquence d’héritage de langue pour ce package.

L’héritage de langue vous permet de créer une traduction appelée _child_ à partir d’une traduction existante appelée _parent_. Les traductions enfants remplacent le parent. Toutefois, si le téléchargement ou l’affichage de la traduction enfant échoue ou s’il manque une phrase ou un mot, Commerce utilise les paramètres régionaux parent. [Exemples d’héritage de modules linguistiques](#example-of-language-inheritance).

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

Où:

- `code`—Paramètre régional du module linguistique (obligatoire)
- `vendor`—nom du fournisseur du module (obligatoire)
- `package` : nom du package de langue (obligatoire)
- `sort_order` : priorité de chargement d’un module lorsqu’il existe plusieurs modules de langue disponibles pour un magasin.
- `use` : paramètre régional du package de langue parente à partir duquel hériter des dictionnaires

Si nécessaire, vous pouvez spécifier plusieurs packages parents. Les packages parents sont appliqués sur la première base répertoriée, la première utilisée.

#### Exemple d’héritage de langue

Supposons qu’un module de langue hérite de deux autres modules et que ces derniers possèdent également des modules parents et &quot;grand-parents&quot;.

Si un package de langue hérite de deux packages, son `language.xml` peut ressembler à ce qui suit :

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

Si l’application Commerce ne trouve pas de mot ou d’expression dans le package `en_GB`, elle recherche dans d’autres packages dans l’ordre suivant :

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

La spécification de tous les héritages entre les packages linguistiques peut entraîner la création de chaînes d’héritage circulaires. Utilisez [le test Magento\Test\Integrity\App\Language\CircularDependencyTest] pour localiser et corriger ces chaînes.

### Configuration de plusieurs packages pour une langue

Pour vous aider à rendre votre boutique plus flexible, vous pouvez télécharger plusieurs packages linguistiques pour la même langue dans votre boutique. Ainsi, vous pouvez utiliser différents packages personnalisés pour différentes parties de votre magasin, car le système compile un package unique à partir de tous les packages disponibles pour une langue.

Pour activer un package supplémentaire pour une langue existante, nommez le nouveau package n’importe quel nom à l’exception d’un nom de code de langue existant (pour éviter toute confusion). Spécifiez les configurations d’un package dans le fichier de méta-informations du `language.xml` module linguistique, comme indiqué dans la section suivante.

## Exemples d’utilisation des commandes de traduction

Les sections suivantes fournissent des exemples de bout en bout d’utilisation des commandes abordées dans cette rubrique pour créer des dictionnaires de traduction et des packages de traduction :

### Exemple : créer un dictionnaire de traduction pour un module ou un thème

Pour ajouter une traduction allemande à un module ou à un thème que vous souhaitez distribuer à d’autres commerçants :

1. Collectez des expressions à partir de votre module :

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >Le nom du fichier CSV doit _correspondre exactement à_ le paramètre régional, y compris la casse des caractères.

1. Traduisez les mots et expressions à l’aide de [ces instructions](#translation-guidelines).
1. Si nécessaire, copiez `xx_YY.csv` vers `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` ou dans le répertoire de thèmes du module (selon que le dictionnaire de traduction est pour un module ou un thème).

### Exemple : créer un package de langue

Comme dans l’exemple précédent, générez un fichier CSV, mais au lieu de spécifier un répertoire de module ou de thème, spécifiez le répertoire racine de l’application Commerce entier. Le fichier CSV obtenu contient toutes les expressions que la commande peut trouver dans le code.

1. Collectez les phrases de votre module :

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >Le nom du fichier CSV doit _correspondre_ exactement aux paramètres régionaux, y compris la casse des caractères.

1. Traduisez les mots et les expressions en suivant [ces directives](#translation-guidelines).
1. Créez le module linguistique.

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. Créez un répertoire pour le module linguistique.

   Par exemple, `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. Dans ce répertoire, ajoutez tous les éléments suivants :

   - Une licence, le cas échéant
   - `composer.json` (exemple de suivi)
   - `registration.php` (exemple de suivi)
   - `language.xml` (exemple suivant)

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
    * Copyright &copy; Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **Exemple`language.xml`** :

   ```xml
   <?xml version="1.0"?>
   /**
   * Copyright &copy; Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
   
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[Présentation des traductions]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[dictionnaire de traduction]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[configure les traductions ;]: https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/store-localize
[En savoir plus sur les packages linguistiques]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[registres]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[&#39;de_de&#39;]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&#39;composer.json&#39;]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[`registration.php`]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
