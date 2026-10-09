---
title: Vue d’ensemble du moteur de recherche
description: Découvrez Elasticsearch et OpenSearch pour la recherche de catalogue Adobe Commerce, les conditions préalables, la configuration de serveur web et les tâches de maintenance après installation.
feature: Configuration, Search
exl-id: 0ea78ca2-0bca-4d61-980a-02fb7da04553
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
source-wordcount: '117'
ht-degree: 0%
---
# Vue d’ensemble du moteur de recherche

Depuis la version 2.4.4, Adobe Commerce nécessite [Elasticsearch](https://www.elastic.co) ou [OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) pour être le moteur de recherche de catalogue. Les versions précédentes de 2.4.x nécessitaient Elasticsearch. Pour plus d’informations sur l’installation d’un moteur de recherche et la configuration initiale, consultez les rubriques suivantes :

- [Conditions préalables relatives aux moteurs de recherche](../../installation/prerequisites/search-engine/overview.md)
- [Configuration de Nginx pour votre moteur de recherche](../../installation/prerequisites/search-engine/configure-nginx.md)
- [Configuration d’Apache pour votre moteur de recherche](../../installation/prerequisites/search-engine/configure-apache.md)
- [Installation du logiciel Commerce](../../installation/composer.md) (interface de ligne de commande)

Après avoir installé et intégré votre moteur de recherche à Adobe Commerce, vous devez effectuer une maintenance supplémentaire :

- [Configuration des mots vides de recherche](search-stopwords.md)
- [Configuration du moteur de recherche](configure-search-engine.md)

