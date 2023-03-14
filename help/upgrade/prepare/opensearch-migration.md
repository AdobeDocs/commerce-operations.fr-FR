---
title: Migration de l’Elasticsearch vers OpenSearch
description: Découvrez comment remplacer le moteur de recherche utilisé pour les installations sur site d’Adobe Commerce et de Magento Open Source.
source-git-commit: 682963fb66519097e54f14f2b84ed71528030054
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---


# Migration vers OpenSearch

OpenSearch est un double open source de 7.10.2 Elasticsearch qui a été créé après la modification de la licence de l’Elasticsearch.

Depuis la version 2.4.4, 2.4.3-p2 et 2.3.7-p3, Adobe Commerce et Magento Open Source prennent en charge OpenSearch. Les installations sur site continuent de prendre en charge les Elasticsearch, bien qu’elles ne soient plus prises en charge pour Adobe Commerce sur l’infrastructure cloud. Depuis la version 2.4.6, OpenSearch dispose de son propre module et de ses propres champs dans les paramètres de configuration de l’administrateur.

## Chemin de migration

Les étapes de migration vers OpenSearch sont simples et suivent largement les étapes de la configuration Elasticsearch. Ces étapes supposent qu’Adobe Commerce est la seule application utilisant le moteur de recherche. Si plusieurs applications utilisent le moteur de recherche, suivez le guide de migration officiel. [Passage de l’Elasticsearch open source à OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Assurez-vous que votre installation respecte la variable [conditions préalables du moteur de recherche](../../installation/prerequisites/search-engine/overview.md).

1. Placez le site dans [Mode de maintenance](../../installation/tutorials/maintenance-mode.md).

1. Désinstallez éventuellement l’Elasticsearch.

1. [Installer OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Configuration du moteur de recherche](../../configuration/search/configure-search-engine.md) et effectuer les tâches associées, comme vider le cache et réindexer l’index de recherche du catalogue.

Aucune autre modification des valeurs de configuration n’est nécessaire.
