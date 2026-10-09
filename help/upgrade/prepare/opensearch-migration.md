---
title: Migration d’Elasticsearch vers OpenSearch
description: Découvrez comment remplacer le moteur de recherche utilisé pour les installations sur site d’Adobe Commerce.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '201'
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
