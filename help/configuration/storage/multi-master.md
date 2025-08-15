---
title: Solution de performances de base de données partagée
description: Découvrez la solution de base de données partagée pour Adobe Commerce.
recommendations: noCatalog
exl-id: 922a9af7-2c46-4bf3-b1ad-d966f5564ec0
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# Présentation de la solution de base de données fractionnée

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerce offre plusieurs avantages en termes d’évolutivité, notamment la possibilité d’utiliser trois bases de données principales distinctes pour différents domaines fonctionnels de l’application Commerce.

Les données de passage en caisse, de commandes et de produits peuvent chacune utiliser une base de données principale distincte que vous pouvez éventuellement répliquer. Cette séparation met à l’échelle de manière indépendante la charge des passages en caisse des sites web, des activités de gestion des commandes, de navigation sur les sites web et des activités de marchandisage, en fonction de vos besoins. Ces modifications offrent une flexibilité considérable quant à la manière dont le niveau de base de données peut être dimensionné.

>[!INFO]
>
>Adobe Commerce sur les infrastructures cloud ne prend _pas_ en charge cette fonctionnalité.

La classe `ResourceConnections` fournit la connexion de base de données MySQL unifiée à l’application Commerce. Pour les requêtes aux bases de données principales, nous implémentons le modèle de base de données CQRS (Command Query Responsibility Segregation). Ce modèle gère la logique de routage des requêtes de lecture et d’écriture vers les bases de données appropriées. Les développeurs n’ont pas besoin de savoir quelle configuration est utilisée et il n’existe aucune connexion de base de données distincte en lecture et écriture.

Si vous configurez la réplication de base de données facultative, vous obtenez les avantages suivants :

- Sauvegarde des données
- Analyse des données sans affecter la base de données principale
- Évolutivité

Les bases de données MySQL se répliquent de manière asynchrone, ce qui signifie que les esclaves n’ont pas besoin d’être connectés en permanence pour recevoir les mises à jour du maître.

La figure suivante montre le fonctionnement de cette fonctionnalité.

![Adobe Commerce utilise différentes bases de données pour stocker les tables](../../assets/configuration/split-db-diagram-ee.png)

Dans Magento Open Source, une seule base de données principale est utilisée.

Adobe Commerce utilise trois bases de données principales et un nombre configurable de bases de données esclaves pour la réplication. Adobe Commerce dispose d’une interface unique pour les connexions à la base de données, ce qui se traduit par des performances plus rapides et une meilleure évolutivité.

## Options de configuration

En raison de la conception de la solution de performances de la base de données partagée, votre code personnalisé et les composants installés _ne peuvent pas_ effectuer les opérations suivantes :

- Écrire directement dans la base de données (au lieu de cela, vous devez utiliser l’interface de base de données Adobe Commerce)
- Utiliser des jointures qui affectent les bases de données de ventes ou de devis
- Utilisez des clés étrangères pour créer des tables dans les bases de données de paiement, de ventes ou principales

>[!WARNING]
>
>Contactez les développeurs de composants pour vérifier si leurs composants effectuent l’une des opérations précédentes. Si tel est le cas, vous devez choisir uniquement l’une des options suivantes :
>
>- Demandez aux développeurs de composants de mettre à jour leurs composants.
>- Utilisez les composants en l’état _sans_ la solution de base de données fractionnée.
>- Supprimez les composants afin de pouvoir utiliser la solution de base de données partagée.

Cela signifie également que vous pouvez effectuer l’une des opérations suivantes :

- Configurez la solution de base de données partagée _avant_ mise en production de Commerce.

  Adobe recommande de configurer les bases de données fractionnées dès que possible après l’installation du logiciel Commerce.

- [Configuration manuelle](multi-master-manual.md) la solution de base de données partagée.

  Vous devez effectuer cette tâche si vous avez déjà installé des composants ou si Commerce est déjà en production. (_Ne mettez pas_ jour un système de production ; effectuez les mises à jour dans un système de développement et synchronisez les modifications après les avoir testées.)

  >[!WARNING]
  >
  >Vous devez sauvegarder manuellement les deux instances de base de données supplémentaires. Commerce ne sauvegarde que l’instance de base de données principale. La commande [`magento setup:backup --db`](../../installation/tutorials/backup.md) et les options d’administration ne sauvegardent pas les tableaux supplémentaires.

## Conditions préalables

La base de données fractionnée nécessite que vous configuriez trois bases de données principales MySQL sur n’importe quel hôte (les trois sur le serveur Commerce, chaque base de données sur un serveur distinct, etc.). Il s&#39;agit des bases de données _maître_ qui sont utilisées comme suit :

- Une base de données principale pour les tables de passage en caisse
- Une base de données principale pour les tables de ventes (également appelées tables _Order Management System_ ou _OMS_)
- Une base de données principale pour le reste des tables d’application Commerce 2

En outre, vous pouvez éventuellement configurer un nombre illimité de bases de données _esclaves_ qui servent de répartition de charge et de sauvegardes.

Ce guide explique comment configurer les bases de données principales uniquement. Nous fournissons des exemples de configurations et de références pour vous permettre de configurer des bases de données esclaves si vous le souhaitez.

Dans ce guide, les trois bases de données principales sont nommées :

- `magento_quote`
- `magento_sales`
- `magento`

(Vous pouvez nommer vos bases de données comme vous le souhaitez.)
