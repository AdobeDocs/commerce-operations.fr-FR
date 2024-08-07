---
title: Migration de l’Elasticsearch vers OpenSearch
description: Découvrez comment remplacer le moteur de recherche utilisé pour les installations sur site d’Adobe Commerce.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Migration vers OpenSearch

OpenSearch est un double open source de 7.10.2 Elasticsearch qui a été créé après la modification de la licence de l’Elasticsearch.

Depuis les versions 2.4.4, 2.4.3-p2 et 2.3.7-p3, Adobe Commerce prend en charge OpenSearch. Les installations sur site continuent de prendre en charge les Elasticsearch, bien qu’elles ne soient plus prises en charge pour Adobe Commerce sur l’infrastructure cloud. Depuis la version 2.4.6, OpenSearch dispose de son propre module et de ses propres champs dans les paramètres de configuration de l’administrateur.

## Chemin de migration

Les étapes de migration vers OpenSearch sont simples et suivent largement les étapes de la configuration Elasticsearch. Ces étapes supposent qu’Adobe Commerce est la seule application utilisant le moteur de recherche. Dans les cas où plusieurs applications utilisent le moteur de recherche, suivez le guide officiel de migration [Passant de l’Elasticsearch open source à OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Assurez-vous que votre installation respecte les [conditions préalables du moteur de recherche](../../installation/prerequisites/search-engine/overview.md).

1. Placez le site en [mode de maintenance](../../installation/tutorials/maintenance-mode.md).

1. Désinstallez éventuellement l’Elasticsearch.

1. [Installer OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Configurez le moteur de recherche ](../../configuration/search/configure-search-engine.md) et effectuez les tâches associées, comme vider le cache et réindexer l’index de recherche du catalogue.

Aucune autre modification des valeurs de configuration n’est nécessaire.
