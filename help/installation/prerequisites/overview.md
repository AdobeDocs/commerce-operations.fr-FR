---
title: Conditions préalables à l’installation sur site
description: En savoir plus sur les dépendances logicielles requises pour les installations sur site d’Adobe Commerce.
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: db2256f5327897a4376a0d038ce697e8f93235af
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 1%

---

# Conditions préalables à l’installation sur site

Avant d’installer Adobe Commerce, procédez comme suit :

* Configurez un ou plusieurs hôtes conformes à la [configuration requise](../system-requirements.md) répertoriée dans l’onglet *Commerce On-Premise*.
* Si vous configurez plusieurs nœuds web avec l’équilibrage de charge, configurez et testez cette partie de votre système _avant_ d’installer l’application.
* Assurez-vous de pouvoir sauvegarder l’ensemble de votre système à différents moments de l’installation afin de pouvoir le restaurer en cas de problèmes.

>[!NOTE]
>
>Nous supposons que vous installez Adobe Commerce dans un **environnement de développement**, que vous disposez d’un accès utilisateur racine à la machine, **et** que la machine n’a pas besoin d’être hautement sécurisée. Si vous configurez une machine plus sécurisée, nous vous recommandons vivement de consulter un administrateur réseau pour obtenir une assistance supplémentaire.

Nous vous recommandons vivement de mettre à jour et à niveau votre logiciel de système d&#39;exploitation. Ces mises à niveau peuvent fournir des correctifs de sécurité et logiciels qui pourraient prévenir de futurs problèmes. Vous ne savez pas ce que ça veut dire ? Consultez notre [page de présentation de l’installation](../overview.md).

Saisissez les commandes suivantes en tant qu’utilisateur disposant de droits d’`root` :

* Ubuntu

  ```bash
  apt-get update
  ```

  ```bash
  apt-get upgrade
  ```

* CentOS

  ```bash
  yum -y update
  ```

  ```bash
  yum -y upgrade
  ```

## Vérification des prérequis

Pour vérifier les prérequis sur votre système, saisissez les commandes suivantes :

### Apache

CentOS : `httpd -v`

Ubuntu : `apache2 -v`

Adobe Commerce prend en charge Apache version 2.4, comme l’indique le résultat suivant :

```
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Pour installer ou mettre à niveau Apache, voir [Apache](web-server/apache.md).

### PHP

Voir l&#39;onglet *Commerce On-premise* dans [Configuration requise](../system-requirements.md) pour les versions supportées de PHP et [PHP](../system-requirements.md#php-settings) pour les exigences PHP.

### MySQL

Vérifiez que vous disposez d’une version de MySQL compatible avec la version d’Adobe Commerce que vous installez. Consultez l’onglet *Commerce On-premise* dans [Configuration requise](../system-requirements.md) pour connaître les versions prises en charge.

```bash
mysql -u <database root user or database owner name> -p
```

Par exemple :

```bash
mysql -u magento -p
```

Le résultat suivant indique la version que vous exécutez.

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

Saisissez `help` ou `\h` pour obtenir de l’aide. Tapez `\c` pour effacer l&#39;instruction d&#39;entrée actuelle.

Saisissez `exit` à l’invite de `mysql>` pour quitter.

Pour installer ou mettre à niveau MySQL, voir [MySQL](database/mysql.md).

### Moteur de recherche

Pour vérifier votre installation OpenSearch :

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

Pour vérifier votre installation Elasticsearch :

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

Par exemple :

```bash
curl -XGET 'localhost:9200'
```

```
{
  "name" : "Z0S2B05",
  "cluster_name" : "elasticsearch_myname",
  "cluster_uuid" : "V-kpikRJQHudN-Wzdt-IrQ",
  "version" : {
    "number" : "6.8.7",
    "build_flavor" : "oss",
    "build_type" : "tar",
    "build_hash" : "c63e621",
    "build_date" : "2020-02-26T14:38:01.193138Z",
    "build_snapshot" : false,
    "lucene_version" : "7.7.2",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
```
