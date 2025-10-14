---
title: Configuration du moteur de recherche
description: Configurez un moteur de recherche pour les déploiements sur site d’Adobe Commerce.
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# Configuration du moteur de recherche

Cette section décrit les paramètres minimaux que vous devez choisir pour tester Elasticsearch ou OpenSearch avec des déploiements sur site d’Adobe Commerce.

>[!TIP]
>
>Dans les versions 2.4.4 et 2.4.3-p2, tous les champs libellés **Elasticsearch** s’appliquent également à OpenSearch.
>&#x200B;>Lorsque la prise en charge d’Elasticsearch 8.x a été introduite dans la version 2.4.6, de nouveaux libellés ont été créés pour faire la distinction entre les configurations Elasticsearch et OpenSearch.

Pour plus d’informations sur la configuration de votre moteur de recherche, consultez le [Guide de l’utilisateur](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html?lang=fr).

## Configuration de votre moteur de recherche à partir de l’Administration

>[!TIP]
>
>Pour obtenir des instructions sur la mise à niveau vers une nouvelle version du moteur de recherche, voir [&#x200B; Conditions préalables à la mise à niveau &#x200B;](../../upgrade/prepare/prerequisites.md).

Pour configurer votre système afin d’utiliser Elasticsearch ou OpenSearch :

1. Connectez-vous à l’administrateur en tant qu’administrateur.
1. Cliquez sur **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Dans la liste **[!UICONTROL Search Engine]**, sélectionnez la version correspondante de votre moteur de recherche.

   Le tableau suivant répertorie les options requises pour configurer et tester la connexion à Commerce. À moins que vous n’ayez modifié les paramètres du serveur de votre moteur de recherche, les valeurs par défaut doivent fonctionner. Passez à l’étape suivante.

   | Option | Description |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | Saisissez le nom d’hôte complet ou l’adresse IP de la machine exécutant Elasticsearch ou OpenSearch.<br>Adobe Commerce sur les infrastructures cloud : obtenez cette valeur de votre système d’intégration. |
   | **[!UICONTROL Server Port]** | Entrez le port proxy du serveur web. La valeur par défaut est de 9200<br>Adobe Commerce sur l’infrastructure cloud : obtenez cette valeur à partir de votre système d’intégration. |
   | **[!UICONTROL Index Prefix]** | Saisissez le préfixe d’index du moteur de recherche. Si vous utilisez une seule instance pour plusieurs installations de Commerce (environnements d’évaluation et de production), vous devez spécifier un préfixe unique pour chaque installation. Sinon, vous pouvez utiliser le préfixe par défaut magento2. |
   | **[!UICONTROL Enable HTTP Auth]** | Cliquez sur **[!UICONTROL Yes]** uniquement si vous avez activé l’authentification pour le serveur de votre moteur de recherche. Si tel est le cas, indiquez un nom d’utilisateur et un mot de passe dans les champs fournis. |
   | **[!UICONTROL Server Timeout]** | Saisissez la durée d’attente (en secondes) lors de la tentative de connexion au serveur Elasticsearch ou OpenSearch. |

1. Cliquez sur **[!UICONTROL Test Connection]**.

   Exemple de réponse :

   ![succès](../../assets/configuration/elastic_test-success.png)

   Continuer avec :

   - [Configuration d’Apache pour votre moteur de recherche](../../installation/prerequisites/search-engine/configure-apache.md)
   - [Configuration de Nginx pour votre moteur de recherche](../../installation/prerequisites/search-engine/configure-nginx.md)

   ou vous voyez :

   ![échec](../../assets/configuration/elastic_test-fail.png)

Si tel est le cas, essayez les méthodes suivantes :

- Vérifiez que le serveur du moteur de recherche est en cours d’exécution.
- Si le serveur se trouve sur un hôte différent de Commerce, connectez-vous au serveur Commerce et envoyez une requête ping à l’hôte du moteur de recherche. Résolvez les problèmes de connectivité réseau et testez à nouveau la connexion.
- Examinez la fenêtre de commande dans laquelle vous avez démarré Elasticsearch ou OpenSearch à la recherche de traces de pile et d’exceptions. Vous devez résoudre ces problèmes avant de continuer. Veillez en particulier à démarrer votre moteur de recherche en tant qu’utilisateur disposant des privilèges `root`.
- Assurez-vous que le [pare-feu UNIX et SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) sont tous deux désactivés, ou configurez des règles pour permettre à votre moteur de recherche et à Commerce de communiquer entre eux.
- Vérifiez la valeur du champ **[!UICONTROL Server Hostname]** . Vérifiez que le serveur est disponible. Vous pouvez essayer l’adresse IP du serveur à la place.
- Utilisez la commande `netstat -an | grep <listen-port>` pour vérifier que le port spécifié dans le champ **[!UICONTROL Server Port]** n’est pas utilisé par un autre processus.

  Par exemple, pour voir si votre moteur de recherche s’exécute sur son port par défaut, utilisez la commande suivante :

  ```bash
  netstat -an | grep 9200
  ```

  S’il s’exécute sur le port 9200, il se présente comme suit :

  ```
  `tcp        0      0 :::9200            :::-         LISTEN`
  ```

## Réindexez la recherche catalogue et actualisez le cache de page complet.

Après avoir modifié la configuration du moteur de recherche, vous devez réindexer l’index de recherche du catalogue et actualiser le cache de page complet à l’aide de l’Administration ou de la ligne de commande.

Pour actualiser le cache à l’aide de l’Administration :

1. Dans Admin, cliquez sur **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Cochez la case en regard de **[!UICONTROL Page Cache]**.
1. Dans la liste **[!UICONTROL Actions]** en haut à droite, cliquez sur **Actualiser**.

   ![gestion du cache](../../assets/configuration/refresh-cache.png)

Pour nettoyer le cache à l’aide de la ligne de commande : [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

Pour effectuer la réindexation à l’aide de la ligne de commande :

1. Connectez-vous à votre serveur Commerce en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) ou passez à ce dernier.
1. Saisissez l’une des commandes suivantes :

   Saisissez la commande suivante pour réindexer uniquement l’index de recherche de catalogue :

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   Saisissez la commande suivante pour réindexer tous les indexeurs :

   ```bash
   bin/magento indexer:reindex
   ```

1. Patientez jusqu’à la fin de la réindexation.

   >[!INFO]
   >
   >Contrairement au cache, les indexeurs sont mis à jour par une tâche cron. Assurez-vous que [cron est activé](../cli/configure-cron-jobs.md) avant de commencer à utiliser votre moteur de recherche.
