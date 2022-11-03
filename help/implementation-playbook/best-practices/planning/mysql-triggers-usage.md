---
title: Utilisation des déclencheurs MySQL
description: Découvrez comment utiliser efficacement les déclencheurs MySQL avec Adobe Commerce.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 79a825a094a80892cf1a30aa7f5c61bd351c69f5
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---


# Bonnes pratiques relatives à l’utilisation des déclencheurs MySQL

Cet article explique comment éviter des problèmes de performances lors de l’utilisation de déclencheurs MySQL. Les déclencheurs sont utilisés pour consigner les modifications dans les tables de contrôle.

## Produits et versions concernés

- Adobe Commerce sur site
- Adobe Commerce sur l’infrastructure cloud

>[!WARNING]
>
>Pour Adobe Commerce sur les projets cloud, testez toujours les modifications de configuration dans l’environnement d’évaluation avant de modifier la configuration de l’environnement de production.

## Comprendre les impacts sur les performances

Les déclencheurs sont interprétés comme du code, ce qui signifie que MySQL ne les précompile pas.

En se connectant à l’espace de transaction de la requête, les déclencheurs ajoutent de la surcharge à un analyseur et à un interprète pour chaque requête effectuée avec la table. Les déclencheurs partagent le même espace de transaction que les requêtes d’origine, et tandis que ces requêtes se disputent les verrous sur la table, les déclencheurs se disputent indépendamment les verrous sur une autre table.

Ces frais supplémentaires peuvent avoir un impact négatif sur les performances du site si de nombreux déclencheurs sont utilisés.

>[!WARNING]
>
>Adobe Commerce ne prend pas en charge les déclencheurs personnalisés dans la base de données Adobe Commerce, car les déclencheurs personnalisés peuvent introduire des incompatibilités avec les futures versions d’Adobe Commerce. Pour consulter les bonnes pratiques, voir [Directives générales pour MySQL](../../../installation/prerequisites/database/mysql.md) dans la documentation Adobe Commerce.

## Utilisation efficace des déclencheurs

Pour éviter des problèmes de performances lors de l’utilisation de déclencheurs, suivez ces instructions :

- Si des déclencheurs personnalisés écrivent des données au moment de l’exécution du déclencheur, déplacez cette logique pour écrire directement dans les tables d’audit à la place. Par exemple, en ajoutant une requête supplémentaire dans le code de l’application, après la requête pour laquelle vous avez voulu créer le déclencheur.
- Examinez les déclencheurs personnalisés existants et envisagez de les supprimer et d’écrire directement dans les tableaux du côté de l’application. Recherchez les déclencheurs existants dans votre base de données à l’aide de la fonction [`SHOW TRIGGERS` Instruction SQL](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Pour obtenir de l’aide, des questions ou des préoccupations supplémentaires, [envoyer un ticket d’assistance Adobe Commerce ;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Informations supplémentaires

- [Conditions préalables MySQL](../../../installation/prerequisites/database/mysql.md)
- [Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur l’infrastructure cloud](database-on-cloud.md)
