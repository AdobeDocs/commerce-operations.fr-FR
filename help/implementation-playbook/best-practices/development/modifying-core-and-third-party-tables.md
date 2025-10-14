---
title: Bonnes pratiques relatives à la modification des tables de base de données
description: Découvrez comment et à quel moment modifier Adobe Commerce et les tables de bases de données tierces.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 0%

---

# Bonnes pratiques relatives à la modification des tables de base de données

Cet article présente les bonnes pratiques pour modifier les tables de base de données créées par des modules [!DNL Adobe Commerce] ou tiers. Comprendre quand et comment modifier efficacement les tableaux permet d’assurer la viabilité et la stabilité à long terme de votre plateforme commerciale.

La migration à partir de [!DNL Magento 1] et d’autres plateformes d’e-commerce, ou l’utilisation de modules du Marketplace [!DNL Adobe Commerce], peut nécessiter l’ajout et l’enregistrement de données supplémentaires. Votre premier instinct peut être d&#39;ajouter une colonne à une table de base de données ou d&#39;en ajuster une existante. Cependant, vous ne devez modifier une table de [!DNL Adobe Commerce] principale (ou une table de fournisseurs tiers) que dans des situations limitées.

## Pourquoi Adobe recommande d’éviter les modifications

La principale raison pour laquelle vous devez éviter de modifier les tables principales est qu’Adobe Commerce inclut une logique sous-jacente qui contient des requêtes SQL brutes. Les modifications apportées à la structure du tableau peuvent provoquer des effets indésirables inattendus difficiles à résoudre. La modification peut également affecter les opérations DDL (Data Definition Language), ce qui a des répercussions inattendues et imprévisibles sur les performances.

Si vous évitez de modifier la structure des tables de la base de données, c&#39;est également parce que vos modifications peuvent entraîner des problèmes si l&#39;équipe de développement principale ou des développeurs tiers modifient la structure de leurs tables de base de données. Par exemple, quelques tables de base de données principales comportent une colonne appelée `additional_data`. Il s’agit toujours d’un type de colonne `text`. Toutefois, pour des raisons de performances, l’équipe principale peut modifier la colonne en `longtext`. Ce type de colonne est un alias pour JSON. En effectuant la conversion en ce type de colonne, vous augmenterez les performances et la capacité de recherche de cette colonne, qui n’existe pas en tant que type de `text`. Vous pouvez en savoir plus à ce sujet dans [Type de données JSON](https://mariadb.com/kb/en/json-data-type/){target="_blank"}.

## Savoir quand enregistrer ou supprimer des données

Adobe vous recommande de déterminer d’abord si vous devez enregistrer ces données. Si vous déplacez des données à partir d’un système hérité, toute suppression de données vous permet de gagner du temps et vous évite des tâches inutiles lors de la migration. (Il existe des moyens d’archiver les données si elles doivent être consultées ultérieurement.) Pour être un bon gestionnaire de l’application et de la performance, il est acceptable de mettre en doute une demande d’enregistrement de données supplémentaires. Votre objectif est de vous assurer que l’enregistrement des données est une exigence pour répondre à un besoin commercial qui ne peut pas être satisfait d’une autre manière.

### Données héritées

Si votre projet contient des données héritées, telles que d’anciennes commandes ou des enregistrements de client, envisagez une autre méthode de recherche. Par exemple, si l’entreprise a besoin d’accéder aux données uniquement à titre de référence occasionnelle, envisagez d’implémenter une recherche externe de l’ancienne base de données hébergée en dehors de la plateforme commerciale au lieu de migrer les anciennes données vers [!DNL Adobe Commerce].

Dans ce cas, la base de données doit être migrée vers un serveur, offrant soit une interface web pour lire les données, soit une formation à l’utilisation de MySQL Workbench ou d’autres outils similaires. L’exclusion de ces données de la nouvelle base de données accélère la migration en permettant à l’équipe de développement de se concentrer sur le nouveau site plutôt que de résoudre les problèmes de migration des données.

Une autre option permettant de conserver les données externes à Commerce, mais de les utiliser en temps réel, consisterait à utiliser d’autres outils, tels que le maillage GraphQL. Cette option combine différentes sources de données et les renvoie sous la forme d’une réponse unique.

Par exemple, vous pouvez `stitch` d’anciennes commandes à partir d’une base de données externe, par exemple l’ancien site Magento 1 qui est mis hors service. Ensuite, à l’aide du maillage GraphQL, affichez-les dans l’historique des commandes des clients. Ces anciennes commandes peuvent être combinées avec les commandes de votre environnement de [!DNL Adobe Commerce] actuel.

Pour plus d’informations sur l’utilisation du maillage API avec GraphQL, voir [En quoi consiste le maillage API &#x200B;](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) et [Passerelle du maillage GraphQL](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}.

## Migration des données héritées avec des attributs d’extension

Si vous déterminez que les données héritées nécessitent une migration ou que les nouvelles données doivent être enregistrées dans [!DNL Adobe Commerce], Adobe recommande d’utiliser des [attributs d’extension](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}. L’utilisation d’attributs d’extension pour enregistrer des données supplémentaires offre les avantages suivants :

- Vous pouvez contrôler les données conservées et la structure de la base de données, ce qui garantit que les données sont enregistrées avec le type de colonne approprié et les index appropriés.
- La plupart des entités dans [!DNL Adobe Commerce] prennent en charge l’utilisation d’attributs d’extension.
- Les attributs d’extension sont un mécanisme agnostique de stockage qui offre la possibilité d’enregistrer les données à l’emplacement optimal pour votre projet.

Deux exemples d’emplacements de stockage sont les tables de base de données et les [!DNL Redis]. Les éléments clés à prendre en compte lors du choix d’un emplacement sont les suivants : l’emplacement introduit une complexité supplémentaire ou affecte les performances.

### Envisager d’autres alternatives

En tant que développeur, il est essentiel de toujours envisager d’utiliser des outils en dehors de votre environnement de [!DNL Adobe Commerce], tels que le maillage GraphQL et Adobe App Builder. Ces outils peuvent vous aider à conserver l’accès aux données, mais n’ont aucun impact sur l’application commerciale principale ou ses tables de base de données sous-jacentes. Grâce à cette approche, vous exposez vos données par le biais d’une API. Ajoutez ensuite une source de données à votre configuration App Builder. À l’aide du maillage GraphQL, vous pouvez combiner ces sources de données et produire une seule réponse, comme indiqué dans [données héritées](#legacy-data).

Pour plus d’informations sur le maillage GraphQL, voir [Passerelle du maillage GraphQL](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}. Pour plus d’informations sur Adobe App Builder, voir [Présentation d’App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=fr){target="_blank"}.

## Modifier une table principale ou une table tierce

Si vous décidez de stocker des données en modifiant un [!DNL Adobe Commerce] principal ou une table de base de données de module tiers, suivez les instructions suivantes afin de minimiser l’impact sur la stabilité et les performances.

- Ajoutez uniquement de nouvelles colonnes.
- Ne modifiez jamais la valeur _type_ d’une colonne existante. Par exemple, ne modifiez pas un `integer` en `varchar` afin de répondre à votre cas d’utilisation unique.
- Évitez d’ajouter des colonnes aux tables d’attributs EAV. Ces tables sont déjà surchargées de logique et de responsabilité.
- Avant d’ajuster un tableau, déterminez sa taille. La modification de tables volumineuses a un impact sur le déploiement d’, ce qui peut entraîner des minutes ou des heures de retard lorsque des modifications sont appliquées.

## Bonnes pratiques pour modifier une table de base de données externe

Adobe recommande de suivre les étapes suivantes lorsque vous ajoutez une colonne à une table de base de données principale ou à une table tierce :

1. Créez un module dont le nom dans votre espace de noms représente ce que vous mettez à jour.

   Par exemple : `app/code/YourCompany/Customer`

1. Créez les fichiers appropriés pour activer le module (voir [Création d’un module](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html?lang=fr){target="_blank"}.

1. Créez un fichier appelé `db_schema.xml` dans le dossier `etc` et apportez les modifications appropriées.

   Le cas échéant, générez un fichier `db_schema_whitelist.json`. Voir [Schéma déclaratif](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"} pour plus d’informations.

### Impacts potentiels

L’ajout d’une colonne à une base de données externe peut avoir un impact sur votre projet Adobe Commerce des manières suivantes :

- Les mises à niveau peuvent être plus compliquées.
- Les déploiements sont affectés si la table en cours de modification est volumineuse.
- La migration vers une nouvelle plateforme pourrait être plus compliquée.

## Méthodes pour éviter de modifier des tables principales

Vous pouvez éviter de modifier les tables de la base de données Adobe Commerce à l’aide d’attributs [extension](#migrate-legacy-data-with-extension-attributes). Une autre alternative consiste à utiliser une colonne spéciale (`additional_data`) qui se trouve sur quelques tables principales pour stocker les données et les enregistrer au format codé JSON.

### Enregistrer des données dans une colonne de données codée en JSON

Certains tableaux principaux comportent une colonne `additional_data` qui contient des données codées JSON. Cette colonne offre un moyen natif de mapper des données supplémentaires dans un champ. L’utilisation de cette méthode évite d’ajouter un tableau pour les petits éléments de données simples qui stockent des informations pour la récupération des données sans avoir à effectuer de recherche. La colonne `additional_data` n&#39;est généralement disponible qu&#39;au niveau de l&#39;article, et non pour l&#39;ensemble du devis ou de la commande.

- Avantages de l’utilisation du champ `additional_data`

   - Aucun champ supplémentaire n’est nécessaire, ce qui réduit le nombre de colonnes au minimum. Cela s’avère utile dans le flux des ventes, où de nombreuses tables sont déjà impliquées. Il est préférable de ne pas ajouter plus de complexité à ce processus déjà compliqué. Cette méthode répond à de nombreux cas d’utilisation, mais pas à tous.

- Inconvénients

   - Cette méthode est idéale uniquement pour stocker des données en lecture seule. Ce problème se produit, car le code doit être désérialisé pour modifier et créer l’objet afin d’ajouter des dépendances ou des relations de base de données.

   - Il est difficile d’utiliser les opérations de base de données pour rechercher ces champs. La recherche avec cette méthode est lente.

   - Soyez très prudent lors du stockage des données dans la colonne `additional_data` pour éviter de déclencher des opérations de sérialisation ou d’annulation de sérialisation qui pourraient interrompre le code en créant un fichier JSON non valide ou en provoquant des erreurs de lecture lors de l’exécution.

   - Ces champs doivent être clairement déclarés dans le code afin qu’un développeur puisse facilement les trouver.

   - D’autres problèmes pouvant survenir et être très difficiles à diagnostiquer. Par exemple, avec certaines fonctions PHP natives, si vous n&#39;utilisez pas [!DNL Adobe Commerce] méthodes wrapper fournies par l&#39;application principale, le résultat final des données transformées peut être différent du format attendu. Utilisez toujours les fonctions wrapper pour garantir la cohérence et la prévisibilité des données enregistrées ou récupérées.

Voici des exemples de tableaux qui ont la colonne et la structure pour la colonne `additional_data`.

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
