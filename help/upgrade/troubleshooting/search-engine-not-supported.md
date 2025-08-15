---
title: Moteur de recherche actuel non pris en charge
description: Résolvez les problèmes liés à la mise à niveau d’Adobe Commerce après avoir rencontré une erreur sur un moteur de recherche non pris en charge.
feature: Upgrade, Search
exl-id: 11479d23-53a5-4086-9f9a-c3420ccad073
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Moteur de recherche actuel non pris en charge

Le message d’erreur suivant indique que la version d’Adobe Commerce à partir de laquelle vous effectuez la mise à niveau est configurée pour utiliser un moteur de recherche catalogue qui n’est pas pris en charge dans la version vers laquelle vous effectuez la mise à niveau :

```
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Cette erreur signifie que l’une des conditions suivantes est remplie sur la version de bas niveau d’Adobe Commerce :

- Le moteur de recherche est défini sur MySQL.
- Le moteur de recherche est défini sur une version d’Elasticsearch qui n’est plus prise en charge.

Utilisez la commande suivante pour vérifier le moteur de recherche actif :

```bash
bin/magento config:show catalog/search/engine
```

L’erreur se produit si la valeur renvoyée est `mysql`, `elasticsearch` ou `elasticsearch6`.

>[!WARNING]
>
>Si vous avez reçu cette erreur, votre installation est dans un état incohérent et vous ne pouvez pas accéder à l’administrateur. Nous vous recommandons de revenir à votre version précédente pendant que vous résolvez cette erreur. Pour ce faire, exécutez l’une des commandes suivantes :
>
>```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>Où `<version>` est la version de Magento que vous utilisiez **avant** la mise à niveau. Par exemple, `2.3.5`.

Suivez les instructions décrites dans les sections suivantes pour récupérer après un état incohérent.

## Si votre moteur de recherche est `mysql`

Avant la version 2.4, MySQL était le moteur de recherche catalogue par défaut, mais il n’est plus pris en charge à ce titre. Désormais, vous devez installer et configurer Elasticsearch ou OpenSearch comme moteur de recherche avant de passer à la version 2.4.

Utilisez les ressources suivantes pour vous guider tout au long de ce processus :

- [Installation et configuration du moteur de recherche](../../configuration/search/overview-search.md)
- [Configuration du moteur de recherche](../../configuration/search/configure-search-engine.md)

Après avoir configuré le moteur de recherche et la réindexation, vous êtes prêt à effectuer la mise à niveau vers la version 2.4.

## Si votre moteur de recherche est `elasticsearch`

Elasticsearch 6 et les versions antérieures ne sont plus prises en charge.

Une valeur `elasticsearch` indique que votre version de bas niveau d’Adobe Commerce est configurée pour utiliser Elasticsearch 2.x. Cette version d’Elasticsearch n’est plus prise en charge.

Vous devez effectuer les tâches suivantes avant d’effectuer la mise à niveau vers la version 2.4 :

1. Effectuez une mise à jour vers une version d’Elasticsearch prise en charge par Commerce. Consultez la section [Mise à niveau d’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) pour obtenir des instructions complètes sur la sauvegarde de vos données, la détection de problèmes de migration potentiels et le test des mises à niveau avant le déploiement en production. Selon la version d’Elasticsearch que vous utilisez, un redémarrage complet du cluster peut être requis.

   >[!NOTE]
   >
   >Elasticsearch nécessite JDK 1.8 ou une version ultérieure. Consultez [Installation du kit de développement logiciel Java (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) pour vérifier quelle version du JDK est installée.

1. [Configurer Elasticsearch](../../configuration/search/configure-search-engine.md) et la réindexation.

Après avoir configuré le moteur de recherche et la réindexation, vous êtes prêt à effectuer la mise à niveau vers la version 2.4.
