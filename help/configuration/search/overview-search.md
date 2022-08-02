---
title: Présentation du moteur de recherche
description: Présentation des options du moteur de recherche pour Adobe Commerce et Magento Open Source.
source-git-commit: 52c472bf80942339b511292243b5da9babf829d9
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Présentation du moteur de recherche

À compter de la version 2.4.4, Adobe Commerce et Magento Open Source requièrent soit [Elasticsearch] ou [OpenSearch] pour être le moteur de recherche catalogue. Les versions précédentes de la version 2.4.x nécessitaient un Elasticsearch. Pour plus d&#39;informations sur l&#39;installation d&#39;un moteur de recherche et la configuration initiale, reportez-vous aux rubriques suivantes :

- [Prérequis du moteur de recherche]
- [Configuration de nginx pour votre moteur de recherche]
- [Configuration d’Apache pour votre moteur de recherche]
- [Installation du logiciel Commerce] (interface de ligne de commande)

Après avoir installé et intégré votre moteur de recherche avec Adobe Commerce, vous devez effectuer une maintenance supplémentaire :

- [Configuration des mots-clés de recherche](search-stopwords.md)
- [Configuration du moteur de recherche](configure-search-engine.md)

<!-- Link Definitions -->

[Prérequis du moteur de recherche]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html
[Configuration de nginx pour votre moteur de recherche]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html
[Configuration d’Apache pour votre moteur de recherche]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html
[Elasticsearch]: https://www.elastic.co
[Elasticsearch documentation]: https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html
[Installation du logiciel Commerce]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-install.html
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
