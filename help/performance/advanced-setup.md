---
title: Configuration avancée
description: Examinez les bonnes pratiques et les recommandations relatives aux systèmes d’entreprise de grande taille conçus pour traiter de grands volumes de données.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 0%

---


# Configuration avancée

[!DNL Commerce] est un produit hautement flexible et évolutif contenant des solutions pour les commerçants de toutes tailles. Cette section décrit les bonnes pratiques et les recommandations relatives à la configuration [!DNL Commerce] pour travailler avec de grandes quantités de données, une charge extrême et d’autres cas d’entreprise.

## Calibrer les performances d’index

Lorsque vous traitez de grandes quantités de données, la réindexation peut devenir une préoccupation. Le [!DNL Commerce] L’équipe a sélectionné les index les plus chargés et activé l’indexation par lots, ce qui vous permet de définir une partie des données à traiter à chaque itération. Ainsi, l’utilisateur peut ajuster la taille des lots en fonction du type et de la taille des données de la base de données.

Pour gérer ce paramètre, modifiez la variable `batchRowsCount` du paramètre `di.xml` du module correspondant. Les index suivants prennent en charge cette fonctionnalité :

* Index de produit de catégorie (module catalogue)
* Index de prix (module catalogue)
* Index EAV (module catalogue)
* Index de stock (module CatalogInventory)

Vous pouvez optimiser les performances de l’indexeur en ajustant les variables de taille de lot d’index. Cela contrôle le nombre d’entités qui sont traitées à la fois par l’indexeur. Dans certains cas, nous avons constaté des baisses importantes du temps d’indexation.

Par exemple, si vous exécutez un profil similaire à B2B Medium, vous pouvez remplacer la valeur de configuration `batchRowsCount` in `app/code/Magento/catalog/etc/di.xml` et remplacer la valeur par défaut de `5000` to `1000`. Cela réduit le temps d’indexation complet de 4 heures à 2 heures avec une valeur par défaut. [!DNL MySQL] configuration.

>[!NOTE]
>
>Nous n’avons pas activé le traitement par lot pour l’indexeur de règles de catalogue. Les vendeurs avec un grand nombre de règles de catalogue doivent ajuster leurs [!DNL MySQL] pour optimiser le temps d’indexation. Dans ce cas, modifiez votre [!DNL MySQL] Le fichier de configuration et l’allocation de davantage de mémoire à TMP_TABLE_SIZE et MAX_HEAP_TABLE_SIZE (la valeur par défaut est 16M pour les deux) amélioreront les performances de cet indexeur, mais se traduiront par des [!DNL MySQL] consomme plus de RAM.

### Limitation des groupes de clients et des catalogues partagés par les sites web

Un grand nombre de SKU de produit, de sites web, de groupes de clients ou de catalogues partagés aura un impact sur le temps d’exécution des indexeurs de règles de catalogue et de prix des produits. En effet, par défaut, tous les sites web sont affectés à tous les groupes de clients (catalogues partagés).

Pour diminuer le temps d’indexation, vous pouvez : [exclure certains sites web des groupes de clients (catalogues partagés)](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites).

## Configuration de Redis

Il arrive qu’une instance Redis ne soit pas suffisante pour répondre aux requêtes entrantes. Il existe plusieurs solutions que nous pouvons recommander pour remédier à cette situation.

Tout d’abord, [!DNL Commerce] vous permet de configurer un stockage du cache distinct pour chaque type de cache. Cela vous permet d’installer autant d’instances Redis distinctes que le nombre de types de cache enregistrés dans Magento. En réalité, vous pouvez souhaiter des instances Redis pour les caches les plus utilisés, tels que la configuration, la mise en page et les blocs.

Une autre solution consiste à placer le cache de configuration sur le système de fichiers et à déplacer les autres caches sur le serveur Redis. Avec cette solution, vous avez besoin d’un outil distinct pour l’invalidation centralisée du cache de configuration sur tous vos noeuds web.

Vous pouvez également utiliser une grappe Redis qui effectue des opérations de lecture/écriture parallèles avec un nombre croissant de noeuds. [!DNL Commerce] ne fournit pas de configuration dans ce cas, mais il peut être lancé avec des personnalisations mineures.

## Configuration [!DNL RabbitMQ]

Magento Open Source et Adobe [!DNL Commerce] prendre en charge les files de messages implémentées via [!DNL RabbitMQ]. [!DNL Commerce] utilise ce service pour exécuter de nombreuses opérations asynchrones, y compris les opérations de catalogue B2B et les mises à jour de stock asynchrones. Toutes les interfaces permettant d’ajouter d’autres tâches au serveur de tâches sont distribuées avec le produit et sont disponibles pour l’implémentation de logique asynchrone personnalisée dans le cadre d’extensions tierces. Comme pour toute autre intégration, [!DNL Commerce] fournit un exemple de fichier de configuration pour [!DNL RabbitMQ] qui contient tous les paramètres recommandés et est entièrement prêt pour l’utilisation en production.

## Partage de la base

>[!WARNING]
>
>La fonctionnalité de base de données partagée était [obsolète](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) dans la version 2.4.2 d’Adobe Commerce. Voir [Rétablissement d’une base de données partagée en une seule base de données](../configuration/storage/revert-split-database.md).

Adobe Commerce vous permet de configurer un stockage de base de données évolutif pour répondre aux besoins d’une entreprise en pleine croissance. Vous pouvez configurer trois bases de données maîtres distinctes qui diffusent des domaines spécifiques :

* Base de données principale (catalogue)
* Extraction de base de données
* Base de données du système de gestion des commandes (OMS)

Pour paramétrer des bases de données additionnelles, vous devez créer une base vide et exécuter l&#39;une des commandes suivantes :

Pour la base de données du Principal de passage en caisse

```bash
bin/magento setup:db-schema:split-quote
```

Pour OMS Principal DB

```bash
bin/magento setup:db-schema:split-sales
```

Ces commandes migrent des tables de domaines spécifiques de la base principale vers une base de données de domaines. Ils modifient également la variable [!DNL Commerce] pour permettre le traitement de la connectivité et des contraintes correspondantes.

En disposant de bases de données distinctes pour les opérations de passage en caisse et de gestion des commandes, vous pouvez répartir la charge entre les serveurs de base de données. Vous pouvez effectuer plus de passages en caisse et traiter plus de commandes par seconde sans affecter la disponibilité de votre catalogue et d’autres opérations. Nous vous recommandons de fractionner les bases de données pour les périodes de vente flash ou principale, ou de les utiliser de manière permanente pour des projets à charge naturellement élevée. La migration des données présentes entre les bases de données doit être exécutée sous la supervision de votre administrateur système.  Ne séparez pas les bases de données en mode Production.

En plus des bases de données principales, [!DNL Commerce] permet de configurer plusieurs bases de données de Secondaire (une pour chaque ressource de données déclarée dans le système). Une base de données de Secondaire sert de réplique complète de votre base de données principale ou de l’une de vos bases de données maître de domaine. Il est émis pour les opérations de lecture sur une ressource spécifique.

Vous pouvez ajouter une base de données de Secondaire en exécutant la commande suivante :

```bash
bin/magento setup:db-schema:add-slave
```

Cette commande effectue des modifications de configuration, mais ne configure pas la réplication elle-même. Cela devrait être fait manuellement.

Après avoir divisé votre base de données principale et défini les bases de Secondaires, [!DNL Commerce] régule automatiquement les connexions à une base de données spécifique, prenant des décisions en fonction du type de demande (POST, PUT, GET, etc.) et de la ressource de données. If [!DNL Commerce] Pour que ses extensions effectuent des opérations d’écriture sur une demande de GET, le système change automatiquement la connexion de Secondaire à la base de données principale. Il fonctionne de la même manière avec les bases de données maîtres : dès que vous utilisez une table liée au passage en caisse, le système redirige toutes les requêtes vers une base de données spécifique. Pendant ce temps, toutes les requêtes liées au catalogue seront envoyées à la base de données principale.

Pour plus d’informations sur la configuration et les avantages de la configuration de plusieurs gabarits/Secondaires, voir
[Solution de performance de la base de données de partage](../configuration/storage/multi-master.md).

## Diffusion de contenu multimédia

Magento ne fournit aucune intégration spécifique pour diffuser et diffuser du contenu multimédia. Toutes les approches courantes peuvent être utilisées ensemble en Magento.

Le moyen le plus simple de diffuser du contenu multimédia est de le diffuser et de le mettre en cache sur une [!DNL Varnish] serveur. Cette approche suppose un système de fichiers partagé pour le stockage de contenu multimédia ou un serveur dédié pointant vers [!DNL Varnish].

Pour les environnements à charge moyenne et élevée, il est recommandé d’utiliser les services CDN (Content Delivery Network) tels que Fastly, Akamai, etc. Lorsque vous utilisez ces services, [!DNL Commerce] utilise la méthode d’extraction classique pour les mises à jour de contenu. Vous devez configurer [!DNL Commerce] URL à utiliser avec le service CDN correspondant. En déplaçant le contenu multimédia vers un CDN, vous réduirez considérablement la charge sur vos instances.

## Configuration du stockage des journaux

Le stockage des logs et leur influence sur d’autres opérations sur le disque affectent la disponibilité de vos noeuds web, en particulier dans les situations de charge élevée. Nous vous recommandons de minimiser la journalisation si vous n’en avez pas besoin. Vous pouvez également configurer la journalisation de sorte qu’elle s’écrive sur un système de stockage distinct doté de vitesses d’accès élevées. Notez que tout goulet d’étranglement lors de l’accès au stockage des journaux peut affecter directement le traitement des requêtes entrantes qui consignent des opérations d’écriture ou de lecture dans le cadre de leur flux.
