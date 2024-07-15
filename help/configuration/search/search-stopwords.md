---
title: Configuration des mots-clés de recherche
description: Découvrez comment gérer les mots-arrêts pour Adobe Commerce à l’aide de fichiers CSV.
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# Configuration des mots-clés de recherche

En général, les _mots-clés_ sont des mots courants que les moteurs de recherche filtrent après le traitement du texte. A l&#39;origine, lorsque l&#39;espace disque et la mémoire étaient extrêmement limités, chaque kilo-octet économisé représentait une amélioration significative des performances. Par conséquent, les moteurs de recherche ont obtenu des gains de performances en ignorant certains mots et en gardant un index faible.

Bien que nous ayons plus de stockage aujourd’hui, les performances sont encore importantes. Elasticsearch et OpenSearch, comme les autres moteurs de recherche, utilisent toujours des mots-clés pour améliorer les performances.

Vous devez gérer vos mots-clés à l’aide de fichiers CSV situés dans le répertoire `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` ou le répertoire `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`, selon la manière dont vous avez installé le logiciel Commerce.

Pour plus d’informations sur la façon dont Elasticsearch et OpenSearch utilisent les mots-clés, consultez les ressources suivantes :

- [Stopwords : Performance Contre Précision](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [Avantages et inconvénients des mots-clés](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [ Utilisation de mots-clés](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Stopwords and Performance](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Configuration des mots-clés

Les mots-clés se trouvent dans le répertoire `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` . Adobe Commerce est livré avec un fichier CSV contenant des mots-clés pour les paramètres régionaux par défaut et un fichier supplémentaire, `stopwords.csv`, contenant des mots-clés pour les paramètres régionaux qui ne sont pas représentés par un autre fichier CSV.

La durée de vie par défaut du cache de fichiers des mots-clés est de 15 minutes.

### Modification des mots-clés d’un paramètre régional existant

**Pour modifier les mots-arrêts** :

1. Connectez-vous à votre serveur Commerce ou basculez vers le [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
1. Utilisez un éditeur de texte pour ouvrir un fichier de mots-clés dans le répertoire `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`.

   Les fichiers CSV utilisent la convention d’affectation des noms `stopwords_<locale_code>.csv`. Par exemple, le fichier du mot-clé allemand est nommé `stopwords_de_DE.csv`.

1. Ajoutez des mots, supprimez des mots ou modifiez des mots dans le fichier.

   (Chaque mot-clé d’un fichier commence sur une nouvelle ligne.)

1. Enregistrez vos modifications et quittez l’éditeur de texte.
1. Nettoyez le cache de configuration.

   - Administration : **Système** > Outils > **Gestion du cache**. Cochez la case **Configuration** et, dans la liste ci-dessus, cliquez sur **Actualiser**. Cliquez sur **Submit** pour terminer l’action.

   - Ligne de commande : en tant que propriétaire du système de fichiers, saisissez la commande suivante :

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. Vérifiez les résultats en recherchant les termes sur votre storefront.

### Créer des mots-clés pour un nouveau paramètre régional

**Pour ajouter des mots de arrêt pour un paramètre régional** :

1. Connectez-vous à votre serveur Commerce ou basculez vers le [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).

1. Utilisez un éditeur de texte pour créer un fichier de mots-clés nommé `stopwords_<locale_code>.csv` dans le répertoire `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`.

   Par exemple, pour créer des mots de fin pour le paramètre régional Italien, nommez le fichier `stopwords_it_IT.csv`.

1. Dans votre fichier de mot d’arrêt, assurez-vous que chaque mot d’arrêt se trouve sur une ligne distincte.
1. Enregistrez vos modifications et quittez l’éditeur de texte.
1. Dans le même répertoire, ouvrez `esconfig.xml` dans un éditeur de texte.
1. Ajoutez une ligne à `esconfig.xml` comme suit :

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Par exemple, pour ajouter un fichier de mots-clés italiens, ajoutez la ligne suivante :

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. Enregistrez les modifications dans `esconfig.xml` et quittez l’éditeur de texte.
1. Nettoyez le cache de configuration.

   - Administration : **Système** > Outils > **Gestion du cache**. Cochez la case **Configuration** et, dans la liste ci-dessus, cliquez sur **Actualiser**. Cliquez sur **Submit** pour terminer l’action.

   - Ligne de commande : en tant que propriétaire du système de fichiers, saisissez la commande suivante :

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. Vérifiez les résultats en recherchant les termes sur votre storefront.

## Modification du répertoire des mots-clés

Cette section explique comment modifier le répertoire de mots-clés par défaut à partir de l’un des éléments suivants :

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

L’emplacement dépend de la manière dont vous avez installé le logiciel Commerce. Si vous avez cloné le référentiel GitHub de Magento 2, le chemin d’accès est sous `app/code`. Si vous avez installé une archive compressée ou un métappackage, le chemin d’accès est sous `vendor`.

**Pour modifier le répertoire** :

1. En tant que propriétaire du système de fichiers, ouvrez l’Elasticsearch `di.xml` dans un éditeur de texte.

   Si vous avez cloné le référentiel, il se trouve à l’emplacement `app/code/Magento/Elasticsearch/etc/di.xml`

   Si vous avez une archive ou le métappackage, elle se trouve à l’adresse `vendor/magento/module-elasticsearch/etc/di.xml`

1. Remplacez la valeur de `stopwordsDirectory` par le répertoire souhaité :

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Enregistrez vos modifications dans `di.xml` et quittez l’éditeur de texte.

## Pour modifier le répertoire à partir de votre module

1. [Créer un module](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. Dans votre module `etc/di.xml`, ajoutez des instructions :

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. Dans votre module, créez le répertoire `etc/stopwords` avec le fichier CSV correspondant.

1. Enregistrez vos modifications dans `di.xml` et quittez l’éditeur de texte.
