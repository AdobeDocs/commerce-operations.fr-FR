---
title: Configuration avancée
description: Découvrez comment effectuer une configuration avancée pour Adobe Commerce. Découvrez les instructions détaillées et les exigences de configuration.
exl-id: eb9ca9fa-b099-4e77-ab33-16cd0f382ffe
source-git-commit: da9ce645d4d32c1368da442d9bd260f5fb3cdb98
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 0%

---

# Configuration avancée

[!DNL Commerce] est un produit très flexible et évolutif contenant des solutions pour les commerçants de toutes tailles. Cette section présente les bonnes pratiques et les recommandations relatives à la configuration des [!DNL Commerce] pour qu’ils fonctionnent avec de grands volumes de données, une charge extrême et d’autres cas d’entreprise.

## Étalonner les performances de l’index

Lorsque vous traitez de grandes quantités de données, la réindexation peut devenir problématique. L’équipe [!DNL Commerce] a sélectionné les index les plus chargés et activé l’indexation par lots, ce qui vous permet de définir une partie des données à traiter à chaque itération. Ainsi, l’utilisateur peut ajuster les tailles des lots en fonction du type et de la taille des données dans la base de données.

Pour gérer ce paramètre, modifiez le paramètre `batchRowsCount` dans le fichier `di.xml` du module correspondant. Les index suivants prennent en charge cette fonctionnalité :

* Index des produits de catégorie (module de catalogue)
* Indice Des Prix (Module Catalogue)
* Index EAV (module de catalogue)
* Index de stock (module CatalogInventory)

Vous pouvez ajuster les performances de l’indexeur en ajustant les variables de taille de lot d’index. Cela contrôle le nombre d’entités traitées à la fois par l’indexeur. Dans certains cas, nous avons constaté des baisses importantes du temps d’indexation.

Par exemple, si vous exécutez un profil similaire à B2B Medium, vous pouvez remplacer la valeur de configuration `batchRowsCount` dans `app/code/Magento/catalog/etc/di.xml` et remplacer la valeur par défaut de `5000` par `1000`. Cela réduit la durée d’indexation complète de 4 heures à 2 heures avec une configuration de [!DNL MySQL] par défaut.

>[!NOTE]
>
>Nous n’avons pas activé le traitement par lots pour l’indexeur de règles de catalogue. Les commerçants avec un grand nombre de règles de catalogue doivent ajuster leur configuration de [!DNL MySQL] pour optimiser le temps d’indexation. Dans ce cas, la modification de votre fichier de configuration [!DNL MySQL] et l’allocation d’une plus grande quantité de mémoire aux valeurs de configuration TMP_TABLE_SIZE et MAX_HEAP_TABLE_SIZE (la valeur par défaut est de 16 millions pour les deux) amélioreront les performances de cet indexeur, mais entraîneront une plus grande consommation de RAM par les [!DNL MySQL].

### Limiter les groupes de clients et les catalogues partagés par sites Web

Un grand nombre de SKU de produit, de sites web, de groupes de clients ou de catalogues partagés aura un impact sur le temps d’exécution des indexeurs de prix de produit et de règles de catalogue. En effet, par défaut, tous les sites web sont affectés à tous les groupes de clients (catalogues partagés).

Pour réduire le temps d’indexation, vous pouvez [exclure certains sites web des groupes de clients (catalogues partagés)](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites).

## Configuration de Redis

Parfois, une seule instance Redis ne suffit pas à répondre aux requêtes entrantes. Il existe plusieurs solutions que nous pouvons recommander pour remédier à cette situation.

Tout d’abord, [!DNL Commerce] vous permet de configurer un espace de stockage de cache distinct pour chaque type de cache. Cela vous permet d’installer autant d’instances Redis distinctes que le nombre de types de cache enregistrés dans Magento. En réalité, vous pouvez souhaiter des instances Redis pour les caches les plus utilisés, tels que la configuration, la disposition et les blocs.

Une autre solution peut être de placer le cache de configuration sur le système de fichiers et de déplacer les autres caches vers le serveur Redis. Avec cette solution, vous avez besoin d’un outil distinct pour centraliser l’invalidation du cache de configuration sur tous vos nœuds web.

Vous pouvez également utiliser un cluster Redis qui effectue des opérations de lecture/écriture parallèles avec un nombre automatiquement croissant de nœuds. [!DNL Commerce] ne fournit pas de configuration pour ce cas, mais il peut être lancé avec des personnalisations mineures.

## Configurer les [!DNL RabbitMQ]

Adobe Commerce prend en charge les files d’attente de messages implémentées via [!DNL RabbitMQ]. [!DNL Commerce] utilise ce service pour exécuter de nombreuses opérations asynchrones, y compris les opérations de catalogue B2B et les mises à jour de stock asynchrones. Toutes les interfaces permettant d’ajouter d’autres tâches au serveur de tâches sont distribuées avec le produit et sont disponibles pour une implémentation logique asynchrone personnalisée dans la portée des extensions tierces. Comme pour toute autre intégration, [!DNL Commerce] fournit un exemple de fichier de configuration pour [!DNL RabbitMQ] qui contient tous les paramètres recommandés et est entièrement prêt pour une utilisation en production.

## Partage de la base de données

>[!WARNING]
>
>La fonctionnalité de base de données partagée était [obsolète](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) dans la version 2.4.2 d’Adobe Commerce. Voir [Rétablir une base de données fractionnée en une seule base de données](../configuration/storage/revert-split-database.md).

Adobe Commerce vous permet de configurer un stockage de base de données évolutif pour répondre aux besoins d’une entreprise en croissance. Vous pouvez configurer trois bases de données principales distinctes qui servent des domaines spécifiques :

* Base de données principale (catalogue)
* Extraire la base de données
* Base de données du système Order Management (OMS)

Pour configurer des bases de données additionnelles, vous devez créer une base de données vide et exécuter l&#39;une des commandes suivantes :

Pour la base de données du Principal de paiement

```bash
bin/magento setup:db-schema:split-quote
```

Base de données du Principal OMS

```bash
bin/magento setup:db-schema:split-sales
```

Ces commandes migrent des tables de domaine spécifiques de la base de données principale vers une base de données de domaine. Ils modifient également la configuration du [!DNL Commerce] pour permettre le traitement des contraintes et de la connectivité correspondants.

Disposer de bases de données distinctes pour l’extraction et Order Management vous permet de répartir la charge entre vos serveurs de base de données. Vous pouvez effectuer plus de passages en caisse et traiter plus de commandes par seconde sans affecter la disponibilité de votre catalogue et d’autres opérations. Nous vous recommandons de fractionner les bases de données pour les périodes de ventes flash ou actives, ou de les utiliser en permanence pour les projets à forte charge naturelle. La migration des données actuelles entre les bases de données doit être effectuée sous la supervision de votre administrateur système.  Ne fractionnez pas les bases de données en mode Production.

Outre les bases de données principales, [!DNL Commerce] permet de configurer plusieurs bases de données esclaves (une pour chaque ressource de données déclarée dans le système). Une base de données esclave sert de réplica complet de votre base de données principale ou de l&#39;une de vos bases de données maîtres de domaine. Il est émis pour les opérations de lecture sur une ressource spécifique.

Vous pouvez ajouter une base esclave en exécutant la commande suivante :

```bash
bin/magento setup:db-schema:add-slave
```

Cette commande effectue des modifications de configuration, mais ne configure pas la réplication elle-même. Cela doit être fait manuellement.

Après avoir fractionné votre base de données principale et défini des bases de données esclaves, [!DNL Commerce] règle automatiquement les connexions à une base de données spécifique, en prenant des décisions en fonction du type de requête (POST, PUT, GET, etc.) et de la ressource de données. Si [!DNL Commerce] ou ses extensions effectuent des opérations d’écriture sur une requête GET, le système bascule automatiquement la connexion de la base de données esclave vers la base de données maître. Le fonctionnement est le même avec les bases de données principales : dès que vous utilisez une table liée au passage en caisse, le système redirige toutes les requêtes vers une base de données spécifique. Pendant ce temps, toutes les requêtes liées au catalogue sont dirigées vers la base de données principale.

Pour plus d’informations sur la configuration et les avantages d’une configuration maître/esclave multiple, voir
[Solution de performances de base de données partagée](../configuration/storage/multi-master.md).

## Diffuser du contenu multimédia

Magento ne fournit aucune intégration spécifique pour diffuser du contenu multimédia. Toutes les approches courantes peuvent être utilisées ensemble dans Magento.

Le moyen le plus simple de diffuser du contenu multimédia est de le diffuser et de le mettre en cache sur un serveur [!DNL Varnish]. Cette approche suppose soit un système de fichiers partagé pour stocker le contenu multimédia, soit un serveur dédié pointant vers [!DNL Varnish].

Pour les environnements à charge moyenne et élevée, nous vous recommandons d’utiliser les services de réseau de diffusion de contenu (CDN) tels que Fastly, Akamai, etc. Lorsque vous utilisez ces services, [!DNL Commerce] utilise l’approche classique d’extraction pour les mises à jour de contenu. Vous devez configurer [!DNL Commerce] URL pour qu’elles fonctionnent avec le service CDN correspondant. En déplaçant le contenu multimédia vers un réseau CDN, vous réduirez considérablement la charge sur vos instances.

## Configuration du stockage des journaux

Le stockage des journaux et leur influence sur les autres opérations du disque affectent la disponibilité de vos nœuds web, en particulier dans les situations de charge élevée. Nous vous recommandons de minimiser la journalisation si vous n’en avez pas besoin. Vous pouvez également configurer la journalisation afin qu’elle s’écrive sur un système de stockage distinct offrant des vitesses d’accès élevées. Notez que tout goulot d’étranglement lors de l’accès au stockage des journaux peut affecter directement le traitement des requêtes entrantes qui consignent les opérations d’écriture ou de lecture dans le cadre de leur flux.
