---
title: Bonnes pratiques de configuration de MySQL
description: Découvrez comment les déclencheurs MySQL et les connexions esclaves affectent les performances du site Commerce et comment les utiliser efficacement.
role: Developer
feature: Best Practices
exl-id: 7c2f51fd-9333-4954-bd35-79c2de3cb2ff
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Bonnes pratiques de configuration de MySQL

>[!NOTE]
>
>Cette rubrique contient des termes logiciels standard que certains peuvent trouver racistes, sexistes ou oppressants et qui peuvent faire ressentir au lecteur de la douleur, un traumatisme ou un malaise. Adobe s’efforce de supprimer ces termes du code, de la documentation et des expériences utilisateur.

## Déclencheurs

Cet article explique comment éviter des problèmes de performances lors de l’utilisation de déclencheurs MySQL. Des déclencheurs sont utilisés pour consigner les modifications dans les tables d&#39;audit.

### Produits et versions concernés

- Adobe Commerce On-Premise
- Adobe Commerce sur les infrastructures cloud

>[!WARNING]
>
>Pour Adobe Commerce sur les projets cloud, testez toujours les modifications de configuration dans l’environnement d’évaluation avant de modifier la configuration de l’environnement de production.

### Incidences sur les performances

Les Triggers sont interprétés comme du code, ce qui signifie que MySQL ne les précompile pas.

En se connectant à l’espace de transaction de la requête, les déclencheurs ajoutent une surcharge à un analyseur et à un interpréteur pour chaque requête effectuée avec la table. Les déclencheurs partagent le même espace de transaction que les requêtes d&#39;origine. Alors que ces requêtes sont en concurrence pour les verrous sur la table, les déclencheurs sont en concurrence indépendamment pour les verrous sur une autre table.

Cette surcharge supplémentaire peut avoir un impact négatif sur les performances du site si de nombreux déclencheurs sont utilisés.

>[!WARNING]
>
>Adobe Commerce ne prend en charge aucun déclencheur personnalisé dans la base de données Adobe Commerce, car les déclencheurs personnalisés peuvent introduire des incompatibilités avec les versions ultérieures d’Adobe Commerce. Pour connaître les bonnes pratiques, voir [Directives générales de MySQL](../../../installation/prerequisites/database/mysql.md) dans la documentation d’Adobe Commerce.

### Utilisation efficace

Pour éviter des problèmes de performances lors de l’utilisation de déclencheurs, suivez ces instructions :

- Si des déclencheurs personnalisés écrivent des données lors de l’exécution du déclencheur, déplacez cette logique pour écrire directement dans les tables d’audit à la place. Par exemple, en ajoutant une requête supplémentaire dans le code de l’application, après la requête pour laquelle vous souhaitiez créer le déclencheur.
- Passez en revue les déclencheurs personnalisés existants et envisagez de les supprimer et d’écrire directement dans les tableaux du côté de l’application. Recherchez les déclencheurs existants dans votre base de données à l’aide de l’instruction SQL [`SHOW TRIGGERS`](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Pour toute assistance supplémentaire, toute question ou préoccupation, [envoyez un ticket d’assistance Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=fr&#submit-ticket).

## Connexions esclaves

Adobe Commerce peut lire plusieurs bases de données de manière asynchrone. Si vous prévoyez une charge élevée pour la base de données MySQL d’un site Commerce déployé sur l’architecture Pro de l’infrastructure cloud, Adobe recommande d’activer la connexion esclave MYSQL.

Lorsque vous activez la connexion esclave MYSQL, Adobe Commerce utilise une connexion en lecture seule à la base de données pour recevoir le trafic en lecture seule sur un nœud non maître. Les performances sont améliorées par l’équilibrage de charge lorsqu’un seul nœud gère le trafic en lecture-écriture.

### Versions affectées

Adobe Commerce sur les infrastructures cloud, architecture Pro uniquement

### Configuration

Dans Adobe Commerce sur l’infrastructure cloud, vous pouvez remplacer la configuration par défaut de la connexion esclave MYSQL en définissant la variable [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=fr#mysql_use_slave_connection). Définissez cette variable sur `true` pour utiliser automatiquement une connexion en lecture seule à la base de données.

**Pour activer la connexion esclave MySQL** :

1. Sur votre station de travail locale, accédez au répertoire du projet.

1. Dans le fichier `.magento.env.yaml`, définissez la `MYSQL_USE_SLAVE_CONNECTION` sur true.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Validez les modifications apportées au fichier `.magento.env.yaml` et envoyez-le à l’environnement distant.

   Une fois le déploiement terminé, la connexion esclave MySQL est activée pour l’environnement cloud.
