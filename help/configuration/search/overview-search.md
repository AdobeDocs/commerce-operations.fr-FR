---
title: Vue d’ensemble du moteur de recherche
description: Présentation des options du moteur de recherche pour Adobe Commerce.
feature: Configuration, Search
exl-id: 0ea78ca2-0bca-4d61-980a-02fb7da04553
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# Vue d’ensemble du moteur de recherche

Depuis la version 2.4.4, Adobe Commerce nécessite [Elasticsearch] ou [OpenSearch] pour être le moteur de recherche de catalogue. Les versions précédentes de 2.4.x nécessitaient Elasticsearch. Pour plus d’informations sur l’installation d’un moteur de recherche et la configuration initiale, consultez les rubriques suivantes :

- [Conditions préalables relatives aux moteurs de recherche](../../installation/prerequisites/search-engine/overview.md)
- [Configuration de Nginx pour votre moteur de recherche](../../installation/prerequisites/search-engine/configure-nginx.md)
- [Configuration d’Apache pour votre moteur de recherche](../../installation/prerequisites/search-engine/configure-apache.md)
- [Installation du logiciel Commerce](../../installation/composer.md) (interface de ligne de commande)

Après avoir installé et intégré votre moteur de recherche à Adobe Commerce, vous devez effectuer une maintenance supplémentaire :

- [Configuration des mots vides de recherche](search-stopwords.md)
- [Configuration du moteur de recherche](configure-search-engine.md)

<!-- Link Definitions -->

[Elasticsearch]: https://www.elastic.co
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
