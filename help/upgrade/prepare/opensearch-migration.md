---
title: Migration d’Elasticsearch vers OpenSearch
description: Découvrez comment remplacer le moteur de recherche utilisé pour les installations sur site d’Adobe Commerce.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 54aef3d7db7b8333721fb56db0ba8f098aea030b
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Migration vers OpenSearch

OpenSearch est un branchement open source d’Elasticsearch 7.10.2 créé après le changement de licence d’Elasticsearch.

Depuis la version 2.4.4, 2.4.3-p2 et 2.3.7-p3, Adobe Commerce prend en charge OpenSearch. Les installations sur site continuent à prendre en charge Elasticsearch, bien qu’elles ne soient plus prises en charge pour Adobe Commerce sur les infrastructures cloud. À partir de la version 2.4.6, OpenSearch dispose de son propre module et de ses propres champs dans les paramètres de configuration d’administration.

## Chemin de migration

Les étapes de migration vers OpenSearch sont simples et suivent largement les étapes de configuration d’Elasticsearch. Ces étapes supposent qu’Adobe Commerce est la seule application utilisant le moteur de recherche. Si plusieurs applications utilisent le moteur de recherche, suivez le guide de migration officiel [Passer d’Open Source Elasticsearch à OpenSearch](https://opensearch.org/blog/moving-from-opensource-elasticsearch-to-opensearch/).

1. Assurez-vous que votre installation respecte les [conditions préalables relatives au moteur de recherche](../../installation/prerequisites/search-engine/overview.md).

1. Placez le site en [mode de maintenance](../../installation/tutorials/maintenance-mode.md).

1. Vous pouvez éventuellement désinstaller Elasticsearch.

1. [Installer OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Configurez le moteur de recherche](../../configuration/search/configure-search-engine.md) et effectuez les tâches associées, comme vider le cache et réindexer l’index de recherche du catalogue.

Aucune autre modification de la valeur de configuration n’est nécessaire.
