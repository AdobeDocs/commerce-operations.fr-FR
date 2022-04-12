---
title: Migration de l’Elasticsearch vers OpenSearch
description: Découvrez comment remplacer le moteur de recherche utilisé pour les installations sur site d’Adobe Commerce et de Magento Open Source.
source-git-commit: 8007ff2e77689ec2058a326924dc34b8d91ee570
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# Migration vers OpenSearch

OpenSearch est un double open source de 7.10.2 Elasticsearch qui a été créé après la modification de la licence de l’Elasticsearch.

Depuis la version 2.4.4, 2.4.3-p2 et 2.3.7-p3, Adobe Commerce et Magento Open Source prennent en charge OpenSearch. Les installations sur site continuent de prendre en charge les Elasticsearch, bien qu’elles ne soient plus prises en charge pour Adobe Commerce sur l’infrastructure cloud.

## Chemin de migration

Les étapes de migration vers OpenSearch sont simples et suivent largement les étapes de la configuration Elasticsearch. Ces étapes supposent qu’Adobe Commerce est la seule application utilisant le moteur de recherche. Si plusieurs applications utilisent le moteur de recherche, suivez le guide de migration officiel. [Passage de l’Elasticsearch open source à OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Assurez-vous que votre installation respecte la variable [conditions préalables du moteur de recherche](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html).

1. Placez le site dans [Mode de maintenance](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. Désinstallez éventuellement l’Elasticsearch.

1. [Installer OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Configuration du moteur de recherche](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) et effectuer les tâches associées, comme vider le cache et réindexer l’index de recherche du catalogue.

Aucune autre modification des valeurs de configuration n’est nécessaire.
