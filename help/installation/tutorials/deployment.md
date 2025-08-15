---
title: Créer ou mettre à jour la configuration de déploiement
description: Pour gérer la configuration de déploiement d’Adobe Commerce, procédez comme suit.
feature: Install, Deploy, Configuration
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---

# Créer ou mettre à jour la configuration de déploiement

Il n’existe aucune condition préalable à l’utilisation de cette commande.

## Créer ou mettre à jour la configuration de déploiement

[Configuration de déploiement](../../configuration/reference/deployment-files.md) fournit les informations dont l’application a besoin pour s’initialiser et s’amorcer.

Vous pouvez utiliser cette commande si :

* Vous avez précédemment installé l’application et vous souhaitez modifier la configuration de déploiement
* Vous souhaitez créer uniquement la configuration de déploiement et poursuivre l’installation d’une autre manière
* Pour mettre à jour la configuration de déploiement sans rien affecter d’autre

Options de commande :

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

Le tableau suivant explique la signification des paramètres et valeurs d&#39;installation.

| Paramètre | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--backend-frontname` | Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) pour accéder à l’administrateur.<br><br>Pour empêcher les exploits, nous vous recommandons de ne pas utiliser un mot courant tel que admin, backend. L’URI d’administration ne peut contenir que des valeurs alphanumériques et le caractère de soulignement (`_`). | Non |
| `--db-host` | Utilisez l’une des méthodes suivantes : <br><br>- Le nom d’hôte complet ou l’adresse IP complète du serveur de base de données.<br><br> : `localhost` (par défaut) ou `127.0.0.1` si le serveur de votre base de données se trouve sur le même hôte que votre serveur web. localhost signifie que la bibliothèque cliente MySQL utilise des sockets UNIX pour se connecter à la base de données. `127.0.0.1` entraîne l’utilisation du protocole TCP par la bibliothèque cliente. Pour plus d’informations sur les sockets, consultez la documentation [PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Remarque :** vous pouvez éventuellement spécifier le port du serveur de base de données dans son nom d&#39;hôte, comme `www.example.com:9000` | Non |
| `--db-name` | Nom de l’instance de base de données dans laquelle vous souhaitez installer les tables de base de données.<br><br>La valeur par défaut est `magento2`. | Non |
| `--db-user` | Nom d’utilisateur du propriétaire de l’instance de base de données.<br><br>La valeur par défaut est `root`. | Non |
| `--db-password` | Mot de passe du propriétaire de l&#39;instance de base de données. | Non |
| `--db-prefix` | À utiliser uniquement si vous installez les tables de la base de données dans une instance de base de données qui contient déjà des tables Adobe Commerce.<br><br>Dans ce cas, utilisez un préfixe pour identifier les tables de cette installation. Certains clients disposent de plusieurs instances Adobe Commerce s’exécutant sur un serveur avec toutes les tables dans la même base de données.<br><br>La longueur du préfixe ne peut pas excéder cinq caractères. Elle doit commencer par une lettre et ne peut contenir que des lettres, des chiffres et des traits de soulignement.<br><br>Cette option permet à ces clients de partager le serveur de base de données avec plusieurs installations Adobe Commerce. | Non |
| `--session-save` | Utilisez l’une des méthodes suivantes : <br><br>- `db` pour stocker les données de session dans la [base de données](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). Choisissez le stockage de la base de données si vous disposez d&#39;une base de données en cluster ; sinon, le stockage basé sur des fichiers ne sera pas très avantageux.<br><br> : `files` de stocker les données de session dans le système de fichiers. Le stockage des sessions basé sur des fichiers est approprié, sauf si l’accès au système de fichiers est lent, si vous disposez d’une base de données en cluster ou si vous souhaitez stocker les données de session dans Redis.<br><br>- `redis` de stocker les données de session dans [Utilisez Redis pour le stockage de session](../../configuration/cache/config-redis.md). Si vous utilisez Redis pour la mise en cache par défaut ou de pages, Redis doit être déjà installé. | Non |
| `--key` | Si vous en avez une, spécifiez une clé pour chiffrer les [données sensibles](#sensitive-data) dans la base de données. Si vous n’en avez pas, l’application en génère une pour vous. | Non |
| `--db-init-statements` | Paramètre de configuration MySQL avancé. Utilise les instructions d&#39;initialisation de base de données à exécuter lors de la connexion à la base de données MySQL.<br><br>La valeur par défaut est `SET NAMES utf8;`.<br><br>Consultez une référence similaire à [celle-ci](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) avant de définir des valeurs. | Non |
| `--http-cache-hosts` | Liste séparée par des virgules des hôtes de passerelle de cache HTTP auxquels envoyer les requêtes de purge. (Par exemple, les serveurs de vernis.) Utilisez ce paramètre pour spécifier l’hôte ou les hôtes à purger dans la même requête. (Peu importe que vous ayez un seul hôte ou plusieurs hôtes.)<br><br>Le format doit être `<hostname or ip>:<listen port>`, où vous pouvez omettre `<listen port>` s’il s’agit du port 80. Par exemple, `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. Ne séparez pas les hôtes avec un espace. | Non |

## Importer les données de configuration

Lors de la configuration d’un système d’exploitation, il est recommandé d’importer les paramètres de configuration de `config.php` et `env.php` dans la base de données.
Ces paramètres incluent les chemins et valeurs de configuration, les sites web, les magasins, les vues de magasin et les thèmes.

Après avoir importé des sites web, des boutiques, des vues de boutique et des thèmes, vous pouvez créer des attributs de produit et les appliquer aux sites web, aux boutiques et aux vues de boutique, sur le système d’exploitation.

Sur le système d’exploitation, exécutez la commande suivante pour importer les données des fichiers de configuration (`config.php` et `env.php`) dans la base de données :

```bash
bin/magento app:config:import [-n, --no-interaction]
```

L’indicateur `[-n, --no-interaction]` facultatif permet à la commande de s’exécuter sans confirmations supplémentaires.

Pour plus d’informations, consultez la [Importer des données à partir de fichiers de configuration](../../configuration/cli/import-configuration.md)

### Données sensibles

{{$include /help/_includes/sensitive-data.md}}
