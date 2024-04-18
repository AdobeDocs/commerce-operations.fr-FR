---
title: Conditions préalables à l’installation sur site
description: En savoir plus sur les dépendances logicielles requises pour les installations sur site d’Adobe Commerce.
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 1%

---

# Conditions préalables à l’installation sur site

Avant d’installer Adobe Commerce, vous devez effectuer les opérations suivantes :

* Configurez un ou plusieurs hôtes qui répondent aux [configuration requise](../system-requirements.md).
* Si vous configurez plusieurs noeuds web avec l’équilibrage de charge, configurez et testez cette partie de votre système. _before_ vous installez l’application.
* Assurez-vous de pouvoir sauvegarder l’ensemble du système à différents moments pendant l’installation afin de pouvoir le restaurer en cas de problème.

>[!NOTE]
>
>Nous supposons que vous installez Adobe Commerce dans une **environnement de développement**, que vous disposez d’un accès utilisateur root à la machine, **et** que la machine n&#39;a pas besoin d&#39;être hautement sécurisée. Si vous configurez une machine plus sécurisée, nous vous recommandons vivement de consulter un administrateur réseau pour obtenir de l’aide supplémentaire.

Nous vous recommandons vivement de mettre à jour et de mettre à niveau votre logiciel de système d’exploitation. Ces mises à niveau peuvent fournir des correctifs logiciels et de sécurité susceptibles d’empêcher des problèmes futurs. Vous ne savez pas ce que cela signifie ? Consultez notre [page d’aperçu de l’installation](../overview.md).

Saisissez les commandes suivantes en tant qu’utilisateur avec `root` privilèges :

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

## Vérification requise

Pour vérifier la configuration système requise, saisissez les commandes suivantes :

### Apache

CentOS : `httpd -v`

Ubuntu : `apache2 -v`

Adobe Commerce prend en charge la version 2.4 d’Apache, car le résultat suivant indique :

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Pour installer ou mettre à niveau Apache, voir [Apache](web-server/apache.md).

### PHP

Voir [configuration requise](../system-requirements.md) pour les versions prises en charge de PHP et [PHP](../system-requirements.md#php-settings) pour les exigences de PHP.

### MySQL

Vérifiez que vous disposez d’une version compatible de MySQL pour la version d’Adobe Commerce que vous installez. Voir [Configuration requise](../system-requirements.md) pour les versions prises en charge

```bash
mysql -u <database root user or database owner name> -p
```

Par exemple :

```bash
mysql -u magento -p
```

Le résultat suivant indique la version que vous exécutez.

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

Type `help` ou `\h` pour obtenir de l’aide. Type `\c` pour effacer l’instruction d’entrée actuelle.

Entrée `exit` à l’adresse `mysql>` pour quitter.

Pour installer ou mettre à niveau MySQL, voir [MySQL](database/mysql.md).

### Moteur de recherche

Pour vérifier votre installation OpenSearch :

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

Pour vérifier l’installation de votre Elasticsearch :

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

Par exemple :

```bash
curl -XGET 'localhost:9200'
```

```terminal
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
