---
title: Configuration des mots vides de recherche
description: Découvrez comment gérer les mots vides pour Adobe Commerce à l’aide de fichiers CSV.
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# Configuration des mots vides de recherche

En général, les _mots vides_ sont des mots courants que les moteurs de recherche filtrent après traitement du texte. À l&#39;origine, lorsque l&#39;espace disque et la mémoire étaient extrêmement limités, chaque kilo-octet économisé signifiait une amélioration significative des performances. Par conséquent, les moteurs de recherche ont réalisé des gains de performances en ignorant certains mots et en gardant l’index petit.

Bien que nous disposions aujourd’hui de davantage de stockage, les performances restent importantes. Elasticsearch et OpenSearch, comme d’autres moteurs de recherche, utilisent toujours des mots vides pour améliorer les performances.

Vous devez gérer vos mots vides à l’aide de fichiers CSV situés dans le répertoire `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ou le répertoire `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`, selon la manière dont vous avez installé le logiciel Commerce.

Pour plus d’informations sur l’utilisation des mots vides par Elasticsearch et OpenSearch, consultez les ressources suivantes :

- [Mots vides : performance et précision](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [Avantages et inconvénients des mots vides](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [Utilisation de mots vides](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Mots vides et performance](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Configurer les mots vides

Les mots vides se trouvent dans le répertoire `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`. Adobe Commerce est fourni avec un fichier CSV contenant des mots vides pour les paramètres régionaux par défaut et un fichier supplémentaire, `stopwords.csv`, qui contient des mots vides pour tous les paramètres régionaux qui ne sont pas représentés par un autre fichier CSV.

La durée de vie par défaut du cache de fichier de mots vides est de 15 minutes.

### Modifier les mots vides pour un paramètre régional existant

**Pour modifier des mots vides** :

1. Connectez-vous à votre serveur Commerce ou passez au [ propriétaire du système de fichiers ](../../installation/prerequisites/file-system/overview.md).
1. Utilisez un éditeur de texte pour ouvrir un fichier de mots vides dans le répertoire `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`.

   Les fichiers CSV utilisent la convention de nommage `stopwords_<locale_code>.csv`. Par exemple, le fichier de mots vides allemand est nommé `stopwords_de_DE.csv`.

1. Ajoutez des mots, supprimez des mots ou modifiez des mots dans le fichier .

   (Chaque mot-clé d’un fichier commence sur une nouvelle ligne.)

1. Enregistrez vos modifications et quittez l’éditeur de texte.
1. Nettoyez le cache de configuration.

   - Admin : **Système** > Outils > **Gestion du cache**. Cochez la case **Configuration** et, dans la liste située au-dessus, cliquez sur **Actualiser**. Cliquez sur **Envoyer** pour terminer l’action.

   - Ligne de commande : en tant que propriétaire du système de fichiers, saisissez la commande suivante :

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. Vérifiez les résultats en recherchant des termes sur votre storefront.

### Créer des mots vides pour un nouveau paramètre régional

**Pour ajouter des mots vides pour un paramètre régional** :

1. Connectez-vous à votre serveur Commerce ou passez au [ propriétaire du système de fichiers ](../../installation/prerequisites/file-system/overview.md).

1. Utilisez un éditeur de texte pour créer un fichier de mots vides nommé `stopwords_<locale_code>.csv` dans le répertoire `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`.

   Par exemple, pour créer des mots vides pour le paramètre régional italien, nommez le fichier `stopwords_it_IT.csv`.

1. Dans votre fichier de mots vides, assurez-vous que chaque mot vide est sur une ligne distincte.
1. Enregistrez vos modifications et quittez l’éditeur de texte.
1. Dans le même répertoire, ouvrez `esconfig.xml` dans un éditeur de texte.
1. Ajoutez une ligne à `esconfig.xml` comme suit :

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Par exemple, pour ajouter un fichier de mots vides italiens, ajoutez la ligne suivante :

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. Enregistrez les modifications dans `esconfig.xml` et quittez l’éditeur de texte.
1. Nettoyez le cache de configuration.

   - Admin : **Système** > Outils > **Gestion du cache**. Cochez la case **Configuration** et, dans la liste située au-dessus, cliquez sur **Actualiser**. Cliquez sur **Envoyer** pour terminer l’action.

   - Ligne de commande : en tant que propriétaire du système de fichiers, saisissez la commande suivante :

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. Vérifiez les résultats en recherchant des termes sur votre storefront.

## Modifier le répertoire des mots vides

Cette section explique comment, de manière facultative, modifier le répertoire de mots vides par défaut de l’un des répertoires suivants :

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

L’emplacement dépend de la manière dont vous avez installé le logiciel Commerce. Si vous avez cloné le référentiel GitHub Magento 2, le chemin d’accès se trouve sous `app/code`. Si vous avez installé une archive compressée ou un métapaquet, le chemin d’accès se trouve sous `vendor`.

**Pour modifier le répertoire** :

1. En tant que propriétaire du système de fichiers, ouvrez le `di.xml` Elasticsearch dans un éditeur de texte.

   Si vous avez cloné le référentiel, il se trouve à l’emplacement `app/code/Magento/Elasticsearch/etc/di.xml`

   Si vous disposez d’une archive ou du métapaquet, il se trouve à l’emplacement `vendor/magento/module-elasticsearch/etc/di.xml`

1. Remplacez la valeur de `stopwordsDirectory` par le répertoire souhaité :

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Enregistrez vos modifications dans `di.xml` et quittez l’éditeur de texte.

## Pour modifier le répertoire depuis votre module

1. [Créer un module](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. Dans votre module `etc/di.xml` ajoutez des instructions :

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. Dans votre module , créez le répertoire `etc/stopwords`, avec le fichier CSV correspondant.

1. Enregistrez vos modifications dans `di.xml` et quittez l’éditeur de texte.
