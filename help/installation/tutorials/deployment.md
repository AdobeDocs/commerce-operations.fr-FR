---
title: Création ou mise à jour de la configuration du déploiement
description: Pour gérer votre configuration de déploiement Adobe Commerce, procédez comme suit.
feature: Install, Deploy, Configuration
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---

# Création ou mise à jour de la configuration du déploiement

L’utilisation de cette commande ne nécessite aucune condition préalable.

## Création ou mise à jour de la configuration du déploiement

[Configuration de déploiement](../../configuration/reference/deployment-files.md) fournit les informations que l’application doit initialiser et amorcer.

Vous pouvez utiliser cette commande si :

* Vous avez précédemment installé l’application et souhaitez modifier la configuration de déploiement.
* Vous souhaitez créer uniquement la configuration de déploiement et poursuivre l’installation d’une autre manière.
* Pour mettre à jour la configuration du déploiement sans affecter quoi que ce soit d’autre

Options de commande :

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

Le tableau suivant décrit la signification des paramètres et valeurs d’installation.

| Paramètre | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--backend-frontname` | Identifiant de ressource unique ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) pour accéder à l’administrateur.<br><br>Pour éviter les exploits, nous vous recommandons de ne pas utiliser un mot commun tel que admin, backend. L’URI d’administration ne peut contenir que des valeurs alphanumériques et le caractère de soulignement (`_`). | Non |
| `--db-host` | Utilisez l’une des méthodes suivantes :<br><br> - Nom d’hôte complet du serveur de base de données ou adresse IP.<br><br>- `localhost` (par défaut) ou `127.0.0.1` si votre serveur de base de données se trouve sur le même hôte que votre serveur web. localhost signifie que la bibliothèque cliente MySQL utilise des sockets UNIX pour se connecter à la base de données. `127.0.0.1` entraîne l’utilisation du protocole TCP par la bibliothèque cliente. Pour plus d’informations sur les sockets, consultez la [documentation PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Remarque :** Vous pouvez éventuellement spécifier le port du serveur de base de données dans son nom d’hôte, par exemple `www.example.com:9000` | Non |
| `--db-name` | Nom de l&#39;instance de base de données dans laquelle vous souhaitez installer les tables de base de données.<br><br>La valeur par défaut est `magento2`. | Non |
| `--db-user` | Nom d’utilisateur du propriétaire de l’instance de base de données.<br><br>La valeur par défaut est `root`. | Non |
| `--db-password` | Mot de passe du propriétaire de l’instance de base de données. | Non |
| `--db-prefix` | À utiliser uniquement si vous installez les tables de base de données dans une instance de base de données qui contient déjà des tables Adobe Commerce.<br><br>Dans ce cas, utilisez un préfixe pour identifier les tables pour cette installation. Certains clients disposent de plusieurs instances Adobe Commerce s’exécutant sur un serveur avec toutes les tables dans la même base de données.<br><br>Le préfixe peut contenir, au maximum, cinq caractères. Il doit commencer par une lettre et ne peut contenir que des lettres, des chiffres et des caractères de soulignement.<br><br>Cette option permet à ces clients de partager le serveur de base de données avec plusieurs installations Adobe Commerce. | Non |
| `--session-save` | Utilisez l’une des méthodes suivantes :<br><br>- `db` pour stocker les données de session dans la [base de données](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). Choisissez le stockage de la base de données si vous disposez d’une base de données en grappe ; dans le cas contraire, le stockage basé sur les fichiers n’offre pas beaucoup d’avantages.<br><br> - `files` pour stocker les données de session dans le système de fichiers. Le stockage des sessions basées sur des fichiers est approprié, sauf si l’accès au système de fichiers est lent, si vous disposez d’une base de données en grappe ou si vous souhaitez stocker des données de session dans Redis.<br><br> - `redis` pour stocker des données de session dans [Utiliser Redis pour le stockage de session](../../configuration/cache/config-redis.md). Si vous utilisez Redis pour la mise en cache des pages ou par défaut, Redis doit être déjà installé. | Non |
| `--key` | Si vous en avez un, spécifiez une clé pour chiffrer les [données sensibles](#sensitive-data) dans la base de données. Si vous n’en avez pas, l’application en génère une pour vous. | Non |
| `--db-init-statements` | Paramètre de configuration MySQL avancé. Utilise les instructions d’initialisation de base de données à exécuter lors de la connexion à la base de données MySQL.<br><br>La valeur par défaut est `SET NAMES utf8;`.<br><br>Consultez une référence similaire à [celle-ci](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) avant de définir des valeurs. | Non |
| `--http-cache-hosts` | Liste séparée par des virgules des hôtes de la passerelle de cache HTTP vers lesquels envoyer les demandes de purge. (Par exemple, les serveurs vernis.) Utilisez ce paramètre pour spécifier l’hôte ou les hôtes à purger dans la même requête. (Peu importe que vous n’ayez qu’un seul hôte ou plusieurs hôtes.)<br><br>Le format doit être `<hostname or ip>:<listen port>`, où vous pouvez omettre `<listen port>` s&#39;il s&#39;agit du port 80. Par exemple, `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. Ne séparez pas les hôtes avec un espace. | Non |

## Importation des données de configuration

Lors de la configuration d’un système de production, il est recommandé d’importer les paramètres de configuration de `config.php` et `env.php` dans la base de données.
Ces paramètres comprennent les chemins et valeurs de configuration, les sites web, les magasins, les vues de magasin et les thèmes.

Après avoir importé des sites web, des magasins, des vues de magasin et des thèmes, vous pouvez créer des attributs de produit et les appliquer à des sites web, des magasins et des vues de magasin sur le système de production.

Sur le système de production, exécutez la commande suivante pour importer les données des fichiers de configuration (`config.php` et `env.php`) dans la base de données :

```bash
bin/magento app:config:import [-n, --no-interaction]
```

L’indicateur facultatif `[-n, --no-interaction]` permet à la commande de s’exécuter sans confirmation supplémentaire.

Pour plus d&#39;informations, consultez la section [Importer des données à partir de fichiers de configuration](../../configuration/cli/import-configuration.md)

### Données sensibles

{{$include /help/_includes/sensitive-data.md}}
