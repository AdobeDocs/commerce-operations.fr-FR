---
title: Configuration automatique des bases de données principales
description: Consultez les conseils sur la configuration automatique de la solution de base de données partagée.
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# Configuration automatique des bases de données principales

{{ee-only}}

{{deprecate-split-db}}

Cette rubrique explique comment commencer à utiliser la solution de base de données partagée en :

1. Installation d’Adobe Commerce avec une seule base de données principale (nommée `magento`)
1. Création de deux bases de données principales supplémentaires pour l&#39;extraction et OMS (nommées `magento_quote` et `magento_sales`)
1. Configuration d’Adobe Commerce pour utiliser les bases de données de paiement et de vente

>[!INFO]
>
>Ce guide suppose que les trois bases de données se trouvent sur le même hôte que l’application Commerce et qu’elles sont nommées `magento`, `magento_quote` et `magento_sales`. Cependant, le choix de l&#39;emplacement des bases de données et de leur nom dépend de vous. Nous espérons que nos exemples rendront les instructions plus faciles à suivre.

## Installation du logiciel Adobe Commerce

Vous pouvez activer les bases de données partagées à tout moment après l&#39;installation du logiciel Adobe Commerce ; en d&#39;autres termes, vous pouvez ajouter des bases de données partagées à un système Adobe Commerce qui dispose déjà de données de commande et de passage en caisse. Suivez les instructions du fichier README d’Adobe Commerce ou du [guide d’installation](../../installation/overview.md) pour installer le logiciel Adobe Commerce à l’aide d’une seule base de données principale.

## Configurer des bases de données principales supplémentaires

Créez des bases de données principales de passage en caisse et OMS comme suit :

1. Connectez-vous à votre serveur de base de données en tant qu&#39;utilisateur.
1. Saisissez la commande suivante pour accéder à une invite de commande MySQL :

   ```bash
   mysql -u root -p
   ```

1. Entrez le mot de passe de l&#39;utilisateur MySQL `root` lorsque vous y êtes invité.
1. Saisissez les commandes suivantes dans l’ordre indiqué pour créer des instances de base de données appelées `magento_quote` et `magento_sales` avec les mêmes noms d’utilisateur et mots de passe :

   ```shell
   create database magento_quote;
   ```

   ```shell
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   ```

   ```shell
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Saisissez `exit` pour quitter l’invite de commande.

1. Vérifiez les bases de données une par une :

   Base de données de passage en caisse :

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   Base de données du système de gestion des commandes :

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Si le moniteur MySQL s’affiche, vous avez créé la base de données correctement. Si une erreur s’affiche, répétez les commandes précédentes.

## Configuration de Commerce pour utiliser les bases de données principales

Après avoir configuré un total de trois bases de données principales, utilisez la ligne de commande pour configurer Commerce afin de les utiliser. (La commande permet de configurer des connexions à la base de données et de répartir les tables entre les bases de données principales.)

### Premières étapes

Voir [Exécution des commandes](../cli/config-cli.md#running-commands) pour vous connecter et exécuter des commandes d’interface de ligne de commande.

### Configuration de la base de données de passage en caisse

Syntaxe de la commande :

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Par exemple,

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

Le message suivant s’affiche pour confirmer la réussite de la configuration :

```
Migration has been finished successfully!
```

### Configuration de la base de données OMS

Syntaxe de la commande :

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Par exemple,

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

```bash
bin/magento setup:upgrade
```

Le message suivant s’affiche pour confirmer la réussite de la configuration :

```
Migration has been finished successfully!
```
