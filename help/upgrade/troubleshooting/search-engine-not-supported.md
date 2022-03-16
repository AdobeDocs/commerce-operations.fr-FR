---
title: Moteur de recherche actuel non pris en charge
description: Dépannez votre mise à niveau Adobe Commerce ou Magento Open Source après avoir rencontré une erreur au sujet d’un moteur de recherche non pris en charge.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---


# Moteur de recherche actuel non pris en charge

Le message d’erreur suivant indique que la version de Magento à partir de laquelle vous effectuez une mise à niveau est configurée pour utiliser un moteur de recherche de catalogue qui n’est pas pris en charge dans la version de Magento vers laquelle vous effectuez la mise à niveau :

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Cette erreur signifie que l’une des conditions suivantes est vraie sur la version de bas niveau d’Adobe Commerce ou de Magento Open Source :

- Le moteur de recherche est défini sur MySQL.
- Le moteur de recherche est défini sur une version d’Elasticsearch qui n’est plus prise en charge.

Utilisez la commande suivante pour vérifier le moteur de recherche actuel :

```bash
bin/magento config:show catalog/search/engine
```

L’erreur se produit si la valeur renvoyée est `mysql` ou `elasticsearch`.

>[!WARNING]
>
>Si vous avez reçu cette erreur, l’état du Magento est incohérent et vous ne pouvez pas accéder à l’administrateur. Nous vous recommandons de revenir à votre version précédente pendant que vous résolvez cette erreur. Pour cela, exécutez l’une des commandes suivantes :
>
>
```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>
```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>Où `<version>` est la version du Magento que vous utilisiez. **before** la mise à niveau. Par exemple, `2.3.5`.

Suivez les instructions décrites dans les sections suivantes pour récupérer à partir d’un état incohérent.

## Si votre moteur de recherche est `mysql`

Avant la version 2.4, MySQL était le moteur de recherche catalogue par défaut, mais MySQL n’est plus pris en charge dans cette capacité. Maintenant, vous devez installer et configurer Elasticsearch en tant que moteur de recherche avant la mise à niveau vers la version 2.4.

Utilisez les ressources suivantes pour vous aider à accomplir ce processus :

- [Installation et configuration de l’Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html)
- [Installation de l’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- Configuration d’un Elasticsearch avec lequel travailler [nginx](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-nginx.html) ou [Apache](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-apache.html)
- [Configuration d’un Magento pour l’utilisation de l’Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html)

Après avoir configuré Elasticsearch et réindexé, vous êtes prêt à effectuer la mise à niveau vers la version 2.4.

## Si votre moteur de recherche est `elasticsearch`

Une valeur de `elasticsearch` indique que votre version de bas niveau d’Adobe Commerce ou de Magento Open Source est configurée pour utiliser Elasticsearch 2.x. Cette version d’Elasticsearch n’est plus prise en charge.

Vous devez effectuer les tâches suivantes avant la mise à niveau vers la version 2.4 :

1. Mettre à jour l’Elasticsearch. Nous vous recommandons de mettre à jour vers Elasticsearch 7.x. Voir [Mise à niveau d’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) pour obtenir des instructions complètes sur la sauvegarde de vos données, la détection des problèmes de migration potentiels et le test des mises à niveau avant le déploiement en production. Selon votre version actuelle d’Elasticsearch, un redémarrage complet de la grappe peut être nécessaire ou non.

   >[!NOTE]
   >
   >Elasticsearch requiert JDK 1.8 ou version ultérieure. Voir [Installation de Java Software Development Kit (JDK)](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) pour vérifier quelle version de JDK est installée.

1. [Configuration d’un Magento pour l’utilisation de l’Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html) et réindexez.

Après avoir configuré Elasticsearch et réindexé, vous êtes prêt à effectuer la mise à niveau vers la version 2.4.
