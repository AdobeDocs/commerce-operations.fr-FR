---
title: Bonnes pratiques relatives à la modification des tables de base de données
description: Découvrez comment et à quel moment modifier des tables de base de données tierces et Adobe Commerce.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1438'
ht-degree: 0%

---

# Bonnes pratiques relatives à la modification des tables de base de données

Cet article fournit les bonnes pratiques pour modifier les tables de base de données créées par [!DNL Adobe Commerce] ou des modules tiers. Comprendre quand et comment modifier efficacement les tables permet d’assurer la viabilité et la stabilité à long terme de votre plateforme commerciale.

Migration depuis [!DNL Magento 1] et d’autres plateformes de commerce électronique, ou l’utilisation de modules provenant de l’ [!DNL Adobe Commerce] Marketplace peut nécessiter l’ajout et l’enregistrement de données supplémentaires. Votre premier instinct peut être d&#39;ajouter une colonne à une table de base de données ou d&#39;en ajuster une existante. Cependant, vous ne devez modifier qu’un noeud [!DNL Adobe Commerce] (ou table de fournisseurs tiers) dans des situations limitées.

## Pourquoi Adobe recommande d’éviter les modifications

La Principale raison pour laquelle vous ne pouvez pas modifier les tables principales est qu’Adobe Commerce inclut une logique sous-jacente contenant des requêtes SQL brutes. Les modifications apportées à la structure du tableau peuvent entraîner des effets secondaires inattendus, difficiles à résoudre. La modification peut également affecter les opérations DDL (Data Definition Language), ce qui a un impact inattendu et imprévisible sur les performances.

Une autre raison d’éviter de modifier la structure de la table de base de données est que vos modifications peuvent entraîner des problèmes si l’équipe de développement principale ou les développeurs tiers modifient la structure de leurs tables de base de données. Par exemple, il existe quelques tables de base de données de base de données de base de données de base qui ont une colonne appelée `additional_data`. Cela a toujours été une `text` type de colonne. Toutefois, pour des raisons de performances, l’équipe principale peut remplacer la colonne par `longtext`. Ce type de colonne est un alias pour JSON. La conversion de ce type de colonne permet d’ajouter à cette colonne des gains de performances et des recherches, qui n’existent pas en tant que `text` type. Pour en savoir plus sur ce sujet, voir [Type de données JSON](https://mariadb.com/kb/en/json-data-type/){target="_blank"}.

## Savoir quand enregistrer ou supprimer des données

Adobe recommande de déterminer d’abord si vous devez enregistrer ces données. Si vous déplacez des données d’un système hérité, toutes les données que vous pouvez supprimer vous font gagner du temps et vous font gagner du temps lors de la migration. (Il existe des moyens d’archiver des données si elles doivent être consultées ultérieurement.) Pour être un bon gestionnaire de l’application et des performances, il est acceptable de contester une demande d’enregistrement de données supplémentaires. Votre objectif est de vous assurer que l’enregistrement des données est nécessaire pour répondre à un besoin de l’entreprise qui ne peut pas être rempli d’une autre manière.

### Données héritées

Si votre projet contient des données héritées, telles que d’anciennes commandes ou des enregistrements de clients, envisagez une autre méthode de recherche. Par exemple, si l’entreprise ne doit accéder aux données qu’à titre de référence occasionnelle, pensez à mettre en oeuvre une recherche externe de l’ancienne base de données hébergée en dehors de la plateforme commerciale au lieu de migrer les anciennes données vers [!DNL Adobe Commerce].

Dans ce cas, la base de données doit être migrée vers un serveur, offrant soit une interface web pour lire les données, soit une formation à l’utilisation de MySQL Workbench ou d’outils similaires. L’exclusion de ces données de la nouvelle base de données accélère la migration en permettant à l’équipe de développement de se concentrer sur le nouveau site plutôt que de résoudre les problèmes de migration des données.

Une autre option connexe permettant de conserver les données à l’extérieur du commerce, mais vous permettant de les utiliser en temps réel, consiste à utiliser d’autres outils, tels que GraphQL mesh. Cette option combine différentes sources de données et les renvoie sous la forme d’une seule réponse.

Par exemple, vous pouvez `stitch` ensemble d’anciennes commandes provenant d’une base de données externe, par exemple l’ancien site Magento 1 qui est mis hors service. Ensuite, à l’aide de l’impression GraphQL, affichez-les dans l’historique des commandes des clients. Ces anciennes commandes peuvent être combinées avec les commandes de votre [!DNL Adobe Commerce] environnement.

Pour plus d’informations sur l’utilisation de l’intégration d’API à GraphQL, voir [Qu’est-ce que le maillage API ?](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) and [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}.

## Migration des données héritées avec des attributs d’extension

Si vous déterminez que les données héritées nécessitent une migration ou que de nouvelles données doivent être enregistrées dans [!DNL Adobe Commerce], Adobe recommande d’utiliser [attributs d’extension](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}. L’utilisation d’attributs d’extension pour enregistrer des données supplémentaires présente les avantages suivants :

- Vous pouvez contrôler les données conservées et la structure de la base de données, ce qui garantit que les données sont enregistrées avec le type de colonne correct et les index adéquats.
- La plupart des entités dans [!DNL Adobe Commerce] et [!DNL Magento Open Source] prennent en charge l’utilisation d’attributs d’extension.
- Les attributs d’extension sont un mécanisme indépendant du stockage qui offre la possibilité d’enregistrer les données à un emplacement optimal pour votre projet.

Deux exemples d’emplacements de stockage sont des tables de base de données et [!DNL Redis]. Les éléments essentiels à prendre en compte lors du choix d’un emplacement sont les suivants : l’emplacement introduit une complexité supplémentaire ou affecte les performances.

### Considérer d&#39;autres alternatives

En tant que développeur, il est essentiel de toujours envisager d’utiliser des outils en dehors de vos [!DNL Adobe Commerce] , comme GraphQL mesh et Adobe App Builder. Ces outils peuvent vous aider à conserver l’accès aux données, mais n’ont aucun impact sur l’application commerciale principale ou ses tables de base de données sous-jacentes. Grâce à cette approche, vous exposez vos données par le biais d’une API. Ensuite, vous ajoutez une source de données à votre configuration App Builder. Avec GraphQL Mesh, vous pouvez combiner ces sources de données et produire une seule réponse, comme indiqué dans la section [données héritées](#legacy-data).

Pour plus d’informations sur l’impression GraphQL, voir [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}. For information about the Adobe App Builder,  see [Introducing App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target="_blank"}.

## Modification d’un tableau principal ou d’un tableau tiers

Si vous décidez de stocker des données en modifiant un noyau [!DNL Adobe Commerce] Pour un tableau de base de données de module tiers, suivez les instructions ci-après afin de minimiser l’impact sur la stabilité et les performances.

- Ajouter de nouvelles colonnes uniquement.
- Ne jamais modifier la variable _type_ d’une colonne existante. Par exemple, ne modifiez pas une `integer` à `varchar` afin de répondre à votre cas d’utilisation unique.
- Évitez d’ajouter des colonnes aux tables d’attributs de la VEC. Ces tables sont déjà surchargées de logique et de responsabilité.
- Avant d’ajuster un tableau, déterminez sa taille. La modification de tables volumineuses a un impact sur le déploiement, ce qui peut entraîner des minutes ou des heures de retard lorsque des modifications sont appliquées.

## Bonnes pratiques relatives à la modification d&#39;une table de base de données externe

Adobe recommande de procéder comme suit lorsque vous ajoutez une colonne à un tableau de base de données principal ou à un tableau tiers :

1. Créez un module avec un nom dans votre espace de noms qui représente ce que vous mettez à jour.

   Par exemple : `app/code/YourCompany/Customer`

1. Créez les fichiers appropriés pour activer le module (voir [Création d’un module](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target="_blank"}.

1. Créez un fichier appelé `db_schema.xml` dans le `etc` et apportez les modifications appropriées.

   Le cas échéant, générez une `db_schema_whitelist.json` fichier . Voir [Schéma déclaratif](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"} pour plus d’informations.

### Effets potentiels

L’ajout d’une colonne à une base de données externe peut avoir un impact sur votre projet Adobe Commerce de la manière suivante :

- Les mises à niveau pourraient être plus complexes.
- Les déploiements sont impactés si la table en cours de modification est volumineuse.
- Les migrations vers une nouvelle plate-forme pourraient être plus complexes.

## Méthodes pour éviter de modifier les tableaux principaux

Vous pouvez éviter de modifier des tables de base de données Adobe Commerce en utilisant [attributs d’extension](#migrate-legacy-data-with-extension-attributes). Une autre alternative consiste à utiliser une colonne spéciale (`additional_data`) trouvées sur quelques tableaux principaux pour stocker des données et les enregistrer au format codé JSON.

### Enregistrement des données dans une colonne de données codée au format JSON

Certains tableaux principaux comportent une variable `additional_data` qui contient des données codées JSON. Cette colonne offre une méthode native de mappage des données additionnelles dans un champ. L’utilisation de cette méthode permet d’éviter l’ajout d’un tableau pour les petits éléments de données simples qui stockent des informations pour la récupération des données sans avoir à effectuer de recherche. Le `additional_data` est généralement disponible uniquement au niveau de l’élément, et non pour le guillemet ou l’ordre entier.

- Avantages de l’utilisation de la variable `additional_data` field

   - Aucun champ supplémentaire n’est nécessaire, ce qui réduit le nombre de colonnes au minimum. Cela s’avère utile dans le flux de ventes, où de nombreuses tables sont déjà impliquées. Il est préférable de ne pas ajouter plus de complexité à ce processus déjà compliqué. Cette méthode répond à de nombreux cas d’utilisation, mais pas à tous.

- Inconvénients

   - Cette méthode est idéale uniquement pour stocker des données en lecture seule. Ce problème se produit car notre code doit être désérialisé pour modifier et créer l’objet afin d’ajouter des dépendances ou des relations de base de données.

   - Il est difficile d’utiliser les opérations de base de données pour rechercher ces champs. La recherche avec cette méthode est lente.

   - Vous devez être plus prudent lorsque vous stockez des données dans la variable `additional_data` afin d’éviter de déclencher des opérations de sérialisation ou de déssérialisation qui peuvent interrompre le code en créant un code JSON non valide ou en provoquant des erreurs de lecture au moment de l’exécution.

   - Ces champs doivent être clairement déclarés dans le code afin qu’un développeur puisse facilement les trouver.

   - D&#39;autres problèmes qui peuvent se produire peuvent être très difficiles à diagnostiquer. Par exemple, avec certaines fonctions PHP natives si vous n’utilisez pas [!DNL Adobe Commerce] les méthodes wrapper fournies par l’application principale ; le résultat final des données transformées peut être différent du format attendu. Utilisez toujours les fonctions wrapper pour assurer la cohérence et la prévisibilité des données en cours d’enregistrement ou de récupération.

Voici des exemples de tableaux dont la colonne et la structure correspondent au `additional_data` colonne .

```mysql
MariaDB [main]> DESCRIBE quote_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)


MariaDB [main]> DESCRIBE sales_order_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)
```

Dans les versions 2.4.3, 2.4.4 et 2.4.5, dix tableaux comportent la colonne `additional_data`.

```mysql
MariaDB [magento]> SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('additional_data') AND TABLE_SCHEMA='main';
+------------------------+
| TABLE_NAME             |
+------------------------+
| sales_shipment_item    |
| sales_creditmemo_item  |
| sales_invoice_item     |
| catalog_eav_attribute  |
| sales_order_payment    |
| quote_address_item     |
| quote_payment          |
| quote_item             |
| magento_reward_history |
| sales_order_item       |
+------------------------+
10 rows in set (0.020 sec)
```
