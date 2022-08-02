---
title: Configuration du moteur de recherche
description: Configurez un moteur de recherche avec Adobe Commerce et Magento Open Source.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---


# Configuration du moteur de recherche

Cette section décrit les paramètres minimaux que vous devez choisir pour tester Elasticsearch ou OpenSearch avec Adobe Commerce et Magento Open Source. Depuis les versions 2.4.4 et 2.4.3-p2, tous les champs sont libellés **Elasticsearch** s’applique également à OpenSearch.

Pour plus d’informations sur la configuration de votre moteur de recherche, voir [Guide de l’utilisateur](https://docs.magento.com/user-guide/catalog/search-elasticsearch.html).

## Configuration de votre moteur de recherche à partir de l’administrateur

Pour configurer votre système afin d’utiliser Elasticsearch ou OpenSearch :

1. Connectez-vous à l’administrateur en tant qu’administrateur.
1. Cliquez sur **Magasins** > Paramètres > **Configuration** > **Catalogue** > **Catalogue** > **Recherche catalogue**.
1. Dans la **Moteur de recherche** Sélectionnez la version correspondante de votre moteur de recherche Si vous utilisez OpenSearch, vous devez sélectionner Elasticsearch7.

   Le tableau suivant répertorie les options de configuration requises pour configurer et tester la connexion à Commerce.
Les valeurs par défaut doivent fonctionner, sauf si vous avez modifié les paramètres du serveur de votre moteur de recherche. Passez à l’étape suivante.

   | Option | Description |
   |--- |--- |
   | **Nom d’hôte du serveur Elasticsearch** | Saisissez le nom d’hôte complet ou l’adresse IP de l’ordinateur exécutant l’Elasticsearch ou OpenSearch.<br>Adobe Commerce sur l’infrastructure cloud : Obtenez cette valeur à partir de votre système d’intégration. |
   | **Port du serveur Elasticsearch** | Saisissez le port proxy du serveur web. La valeur par défaut est 9200<br>Adobe Commerce sur l’infrastructure cloud : Obtenez cette valeur à partir de votre système d’intégration. |
   | **Préfixe d’index Elasticsearch** | Saisissez le préfixe d’index du moteur de recherche. Si vous utilisez une instance unique pour plusieurs installations Commerce (environnements d’évaluation et de production), vous devez spécifier un préfixe unique pour chaque installation. Sinon, vous pouvez utiliser le préfixe magento2 par défaut. |
   | **Activation de l’authentification HTTP Elasticsearch** | Cliquez sur **Oui** uniquement si vous avez activé l’authentification pour votre serveur de moteur de recherche. Si tel est le cas, indiquez un nom d’utilisateur et un mot de passe dans les champs fournis. |

1. Cliquez sur **Tester la connexion**.

   Exemple de réponse :

   ![success](../../assets/configuration/elastic_test-success.png)

   Poursuivez par :

   - [Configuration d’Apache pour votre moteur de recherche](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html)
   - [Configuration de nginx pour votre moteur de recherche](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html)

   ou vous voyez :

   ![failed](../../assets/configuration/elastic_test-fail.png)

Si tel est le cas, essayez les méthodes suivantes :

- Assurez-vous que le serveur du moteur de recherche est en cours d’exécution.
- Si le serveur se trouve sur un autre hôte que Commerce, connectez-vous au serveur Commerce et envoyez un ping à l’hôte du moteur de recherche. Résolvez les problèmes de connectivité réseau et testez à nouveau la connexion.
- Examinez la fenêtre de commande dans laquelle vous avez démarré Elasticsearch ou OpenSearch pour rechercher des arborescences et des arborescences de pile. Vous devez résoudre ceux-là avant de continuer. En particulier, assurez-vous que vous avez démarré votre moteur de recherche en tant qu’utilisateur avec `root` des privilèges.
- Assurez-vous que [pare-feu UNIX et SELinux](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#firewall-selinux) sont désactivés ou configurez des règles pour permettre à votre moteur de recherche et à Commerce de communiquer entre eux.
- Vérifiez la valeur de la variable **Nom d’hôte du serveur Elasticsearch** champ . Assurez-vous que le serveur est disponible. Vous pouvez essayer plutôt l’adresse IP du serveur.
- Utilisez la variable `netstat -an | grep <listen-port>` pour vérifier que le port spécifié dans la variable **Port du serveur Elasticsearch** n’est pas utilisé par un autre processus.

   Par exemple, pour voir si votre moteur de recherche s’exécute sur son port par défaut, utilisez la commande suivante :

   ```bash
   netstat -an | grep 9200
   ```

   S’il s’exécute sur le port 9200, il s’affiche comme suit :

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## Réindexation de la recherche de catalogue et actualisation du cache de la page entière

Après avoir modifié la configuration du moteur de recherche, vous devez réindexer l’index de recherche du catalogue et actualiser le cache de page complet à l’aide de la ligne de commande ou de l’administrateur.

Pour actualiser le cache à l’aide de l’administrateur :

1. Dans l’administrateur, cliquez sur **Système** > **Gestion du cache**.
1. Cochez la case en regard de **Cache de page**.
1. Dans la **Actions** dans la liste supérieure droite, cliquez sur **Actualiser**.

   ![gestion du cache](../../assets/configuration/refresh-cache.png)

Pour nettoyer le cache à l’aide de la ligne de commande : [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

Pour réindexer à l’aide de la ligne de commande :

1. Connectez-vous à votre serveur Commerce en tant que [propriétaire du système de fichiers](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Saisissez l’une des commandes suivantes :

   Saisissez la commande suivante pour réindexer uniquement l’index de recherche de catalogue :

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   Saisissez la commande suivante pour réindexer tous les indexeurs :

   ```bash
   bin/magento indexer:reindex
   ```

1. Attendez que la réindexation soit terminée.

   >[!INFO]
   >
   >Contrairement au cache, les indexeurs sont mis à jour par une tâche cron. Assurez-vous de [cron est activé](../cli/configure-cron-jobs.md) avant de commencer à utiliser votre moteur de recherche.

