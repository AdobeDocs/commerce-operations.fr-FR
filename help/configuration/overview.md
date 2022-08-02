---
title: Présentation du guide de configuration
description: Découvrez l’ensemble des fonctionnalités et services configurables pour votre application Adobe Commerce ou Magento Open Source.
source-git-commit: 573b407bf29fd4dea2c0e9a52593f65fa64ffa2d
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---


# Guide de configuration

Le _Configuration_ Ce guide fournit des documents de référence et des conseils limités pour gérer les fonctionnalités et services d’application Commerce configurables. Les utilisateurs techniques chargés de configurer l’application Commerce peuvent trouver des conseils dans les domaines suivants :

- [Installation](../configuration/bootstrap/initialization.md)
- [Méthodes de déploiement](../configuration/deployment/overview.md)
- [Options de mise en cache](../configuration/cache/caching-overview.md)
- [Gestion des tâches Cron](../configuration/cron/custom-cron.md)
- [Utilisation de la ligne de commande](../configuration/cli/config-cli.md)
- [Personnalisation des logs](../configuration/logs/custom-logging.md)
- [Options de sécurité](../configuration/security/overview.md)
- [Paramètres du moteur de recherche](../configuration/search/configure-search-engine.md)
- [Méthodes de stockage](../configuration/storage/memcached.md)

## Configuration des administrateurs de commerce

Il existe des rubriques correspondantes dans la section [Guide de l’utilisateur de Commerce](https://docs.magento.com/user-guide/stores/configuration.html) qui peuvent vous aider à comprendre la description des champs pour chaque paramètre de configuration dans l’administrateur Commerce.

## Configuration du cloud

[!DNL Commerce on cloud infrastructure] utilise une [ensemble de fichiers de configuration](https://devdocs.magento.com/cloud/env/environments.html) pour mettre à jour la variable [!DNL Commerce] fonctionnalités et services de l’application dans les environnements hébergés. En raison de la nature unique des environnements hébergés dans le cloud d’Adobe, vous devez toujours consulter la variable [Guide Cloud](https://devdocs.magento.com/cloud/bk-cloud.html) pour d’autres exigences de configuration.
