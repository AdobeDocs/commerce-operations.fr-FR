---
title: Bonnes pratiques de configuration MySQL
description: Découvrez comment les déclencheurs MySQL et les connexions esclaves affectent les performances du site Commerce et comment les utiliser efficacement.
role: Developer
feature: Best Practices
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---


# Bonnes pratiques de configuration MySQL

>[!NOTE]
>
>Cette rubrique contient des termes logiciels standard que certains peuvent trouver racistes, sexistes ou oppressifs et qui peuvent faire que le lecteur se sent blessé, traumatisé ou mal accueilli. Adobe s’efforce de supprimer ces termes du code, de la documentation et des expériences utilisateur.

## Triggers

Cet article explique comment éviter des problèmes de performances lors de l’utilisation de déclencheurs MySQL. Les déclencheurs sont utilisés pour consigner les modifications dans les tables de contrôle.

### Produits et versions concernés

- Adobe Commerce sur site
- Adobe Commerce sur l’infrastructure cloud

>[!WARNING]
>
>Pour Adobe Commerce sur les projets cloud, testez toujours les modifications de configuration dans l’environnement d’évaluation avant de modifier la configuration de l’environnement de production.

### Incidences sur les performances

Les déclencheurs sont interprétés comme du code, ce qui signifie que MySQL ne les précompile pas.

En se connectant à l’espace de transaction de la requête, les déclencheurs ajoutent de la surcharge à un analyseur et à un interprète pour chaque requête effectuée avec la table. Les déclencheurs partagent le même espace de transaction que les requêtes d’origine, et tandis que ces requêtes se disputent les verrous sur la table, les déclencheurs se disputent indépendamment les verrous sur une autre table.

Ces frais supplémentaires peuvent avoir un impact négatif sur les performances du site si de nombreux déclencheurs sont utilisés.

>[!WARNING]
>
>Adobe Commerce ne prend pas en charge les déclencheurs personnalisés dans la base de données Adobe Commerce, car les déclencheurs personnalisés peuvent introduire des incompatibilités avec les futures versions d’Adobe Commerce. Pour consulter les bonnes pratiques, voir [Directives générales pour MySQL](../../../installation/prerequisites/database/mysql.md) dans la documentation Adobe Commerce.

### Utilisation efficace

Pour éviter des problèmes de performances lors de l’utilisation de déclencheurs, suivez ces instructions :

- Si des déclencheurs personnalisés écrivent des données au moment de l’exécution du déclencheur, déplacez cette logique pour écrire directement dans les tables d’audit à la place. Par exemple, en ajoutant une requête supplémentaire dans le code de l’application, après la requête pour laquelle vous avez voulu créer le déclencheur.
- Examinez les déclencheurs personnalisés existants et envisagez de les supprimer et d’écrire directement dans les tableaux du côté de l’application. Recherchez les déclencheurs existants dans votre base de données à l’aide de la fonction [`SHOW TRIGGERS` Instruction SQL](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Pour obtenir de l’aide, des questions ou des préoccupations supplémentaires, [envoyer un ticket d’assistance Adobe Commerce ;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Connexions esclaves

Adobe Commerce peut lire plusieurs bases de données de manière asynchrone. Si vous attendez une charge élevée pour la base de données MySQL d’un site de commerce déployé sur l’architecture de l’infrastructure cloud Pro, Adobe recommande d’activer la connexion esclave MYSQL.

Lorsque vous activez la connexion esclave MYSQL, Adobe Commerce utilise une connexion en lecture seule à la base de données pour recevoir du trafic en lecture seule sur un noeud non maître. Les performances s’améliorent grâce à l’équilibrage de charge lorsqu’un seul noeud gère le trafic lecture-écriture.

### Versions affectées

Adobe Commerce sur l’infrastructure cloud, architecture Pro uniquement

### Configuration

Dans Adobe Commerce sur l’infrastructure cloud, vous pouvez remplacer la configuration par défaut de la connexion esclave MYSQL en définissant la variable [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) Variable . Définissez cette variable sur `true` pour utiliser automatiquement une connexion en lecture seule à la base.

**Pour activer la connexion esclave MySQL**:

1. Sur votre poste de travail local, modifiez le répertoire de votre projet.

1. Dans le `.magento.env.yaml` , définissez `MYSQL_USE_SLAVE_CONNECTION` sur true.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Validez la variable `.magento.env.yaml` change de fichier et envoie une notification push vers l’environnement distant.

   Une fois le déploiement terminé, la connexion esclave MySQL est activée pour l’environnement cloud.
