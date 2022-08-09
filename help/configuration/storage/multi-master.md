---
title: Solution de performance de la base de données de partage
description: Découvrez la solution de base de données partagée pour Adobe Commerce et Magento Open Source.
source-git-commit: 52f92ef79586d618fd4ac51c00eaa1446a2dc98f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Présentation de la solution de base de données partagée

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerce offre plusieurs avantages en termes d’évolutivité, notamment la possibilité d’utiliser trois bases de données principales distinctes pour différents domaines fonctionnels de l’application Commerce.

L’extraction, les commandes et les données de produit peuvent utiliser une base de données principale distincte que vous pouvez éventuellement répliquer. Cette séparation met à l’échelle la charge par rapport aux passages en caisse d’un site web, aux activités de gestion des commandes, à la navigation sur le site web et aux activités de marchandisage, selon vos besoins. Ces modifications offrent une flexibilité considérable dans la façon dont le niveau de la base de données peut être mis à l’échelle.

>[!INFO]
>
>Adobe Commerce sur l’infrastructure cloud _not_ prennent en charge cette fonctionnalité.

Le `ResourceConnections` fournit la connexion de base de données MySQL unifiée à l’application Commerce. Pour les requêtes envoyées aux bases de données principales, nous implémentons le modèle de base de données CQRS (Command Query Responsabilité Segregation). Ce modèle gère la logique de routage des requêtes de lecture et d’écriture vers les bases de données appropriées. Les développeurs n’ont pas besoin de savoir quelle configuration est utilisée et il n’existe aucune connexion de base de données en lecture et en écriture distincte.

Si vous configurez une réplication de base de données facultative, vous bénéficiez des avantages suivants :

- Sauvegarde des données
- Analyse des données sans affecter la base de données principale
- Évolutivité

Les bases de données MySQL se répliquent de manière asynchrone, ce qui signifie que les Secondaires n’ont pas besoin d’être connectés de manière permanente pour recevoir les mises à jour du maître.

La figure suivante illustre le fonctionnement de cette fonctionnalité.

![Adobe Commerce utilise différentes bases de données pour stocker des tables.](../../assets/configuration/split-db-diagram-ee.png)

Dans Magento Open Source, une seule base de données principale est utilisée.

Adobe Commerce utilise trois bases de données maîtres et un nombre configurable de bases de Secondaires pour la réplication. Adobe Commerce dispose d’une interface unique pour les connexions à la base de données, ce qui se traduit par des performances plus rapides et une meilleure évolutivité.

## Options de configuration

En raison de la conception de la solution de performances de la base de données partagée, votre code personnalisé et les composants installés _cannot_ effectuez l’une des opérations suivantes :

- Ecrire directement dans la base de données (vous devez utiliser l&#39;interface de la base de données Adobe Commerce)
- Utiliser des JOINS qui affectent les ventes ou [guillemet](https://glossary.magento.com/quote) bases de données
- Utiliser des clés étrangères pour les tables dans les bases de données principales, de ventes ou de passage en caisse

>[!WARNING]
>
>Contactez les développeurs de composants pour vérifier si leurs composants effectuent l’une des opérations précédentes. Si tel est le cas, vous ne devez choisir qu’une seule des options suivantes :
>
>- Demandez aux développeurs de composants de mettre à jour leurs composants.
>- Utiliser les composants tels quels _without_ la solution de base de données partagée.
>- Supprimez les composants pour pouvoir utiliser la solution de base de données partagée.


Cela signifie également que vous pouvez effectuer l’une des opérations suivantes :

- Configuration de la solution de base de données partagée _before_ Mise en production du commerce.

   Adobe recommande de configurer des bases de données partagées dès que possible après l’installation du logiciel Commerce.

- [Configuration manuelle](multi-master-manual.md) la solution de base de données partagée.

   Vous devez effectuer cette tâche si vous avez déjà installé des composants ou si Commerce est déjà en production. (_Ne pas_ mettre à jour un système de production ; effectuez les mises à jour dans un système de développement et synchronisez les modifications après les avoir testées.)

   >[!WARNING]
   >
   >Vous devez sauvegarder manuellement les deux instances de base de données supplémentaires. Commerce sauvegarde uniquement l’instance de base de données principale. Le [`magento setup:backup --db`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html) Les options Commande et Admin ne sauvegardent pas les tables additionnelles.

## Conditions préalables

La base de données partagée requiert que vous configuriez trois bases de données principales MySQL sur n’importe quel hôte (les trois sur le serveur Commerce, chaque base de données sur un serveur distinct, etc.). Voici les _master_ et elles sont utilisées comme suit :

- Une base de données principale pour [passage en caisse](https://glossary.magento.com/checkout) tables
- Une base de données principale pour les tables de ventes (également appelées _Système de gestion des commandes_ ou _OMS_, tableaux)
- Une base de données principale pour le reste des tables de l’application Commerce 2

En outre, vous pouvez éventuellement configurer un nombre illimité de _Secondaire_ bases de données qui servent d’équilibreurs de charge et de sauvegardes.

Ce guide explique uniquement comment configurer les bases de données principales. Nous vous proposons des exemples de paramétrages et de références afin que vous puissiez, si vous le souhaitez, configurer des bases de données de Secondaire.

Dans ce guide, les trois bases de données principales sont nommées :

- `magento_quote`
- `magento_sales`
- `magento`

(Vous pouvez nommer vos bases de données comme bon vous semble.)