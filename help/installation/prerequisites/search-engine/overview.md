---
title: Prérequis du moteur de recherche
description: Pour installer et configurer les logiciels de moteur de recherche pris en charge pour les installations sur site d’Adobe Commerce, procédez comme suit.
feature: Install, Search
exl-id: 44ea638a-7200-4269-be1b-b0851de2c4f4
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# Prérequis du moteur de recherche

Depuis Adobe Commerce 2.4, toutes les installations doivent être configurées pour utiliser [Elasticsearch](https://www.elastic.co) ou [OpenSearch](https://opensearch.org/) en tant que solution de recherche catalogue.

>[!NOTE]
>
>La prise en charge d’OpenSearch a été ajoutée à la version 2.4.4. OpenSearch est un double compatible d’Elasticsearch. Toutes les instructions pour configurer Elasticsearch 7 s’appliquent à OpenSearch. [Migration de l’Elasticsearch vers OpenSearch](../../../upgrade/prepare/opensearch-migration.md) fournit des conseils sur le passage à OpenSearch.

## Versions prises en charge

Vous devez installer et configurer Elasticsearch ou OpenSearch avant d’installer Adobe Commerce 2.4.4 et versions ultérieures.

Voir [Configuration requise](../../system-requirements.md) pour des informations de version spécifiques.

## Configuration recommandée

Nous vous recommandons ce qui suit :

* [Configuration de nginx pour votre moteur de recherche](configure-nginx.md)
* [Configuration d’Apache pour votre moteur de recherche](configure-apache.md)

## Emplacement d’installation

Les tâches suivantes supposent que vous avez configuré votre système selon le diagramme suivant :

![Diagramme du moteur de recherche](../../../assets/installation/search-engine-config.svg)

Le diagramme qui précède affiche :

* L’application Commerce et le moteur de recherche sont installés sur différents hôtes.

  L’exécution sur des hôtes distincts nécessite un proxy pour fonctionner. (La mise en grappe du moteur de recherche va au-delà de ce guide, mais vous trouverez plus d’informations dans la section [Documentation sur la mise en grappe des Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).)

* Chaque hôte possède son propre serveur web ; les serveurs web ne doivent pas nécessairement être les mêmes.

  Par exemple, l’application Commerce peut exécuter Apache et le moteur de recherche peut exécuter nginx.

* Les deux serveurs web utilisent TLS (Transport Layer Security).

  La configuration de TLS dépasse la portée de notre documentation.

Les requêtes de recherche sont traitées comme suit :

1. Une requête de recherche d’un utilisateur est reçue par le serveur web Commerce, qui la transfère au serveur du moteur de recherche.

   Vous configurez le moteur de recherche pour qu’il se connecte à l’hôte et au port du proxy. Nous vous recommandons le port SSL du serveur web (par défaut, 443).

1. Le serveur web du moteur de recherche (écoute sur le port 443) envoie une requête par proxy au serveur du moteur de recherche (par défaut, il écoute sur le port 9200).

1. L’accès au moteur de recherche est protégé par l’authentification HTTP de base. Pour qu’une requête atteigne le moteur de recherche, il doit passer par SSL. *et* indiquez un nom d’utilisateur et un mot de passe valides.

1. Le moteur de recherche traite la requête.

1. La communication renvoie le même itinéraire, le serveur web Elasticsearch agissant comme un proxy inverse sécurisé.

## Conditions préalables

Les tâches abordées dans cette section nécessitent les éléments suivants :

* [Pare-feu et SELinux](#firewall-and-selinux)
* [Installation de Java Software Development Kit (JDK)](#install-the-java-software-development-kit)
* [Installation du moteur de recherche](#install-the-search-engine)
* [Mise à niveau d’Elasticsearch](#upgrading-elasticsearch)

### Pare-feu et SELinux

Les logiciels liés à la sécurité (iptables, SELinux, AppArmor) peuvent être configurés par défaut pour bloquer la communication entre les sous-systèmes. C&#39;est peut-être une bonne idée de les vérifier s&#39;il y a des problèmes.

#### Configuration de règles pour iptables et SELinux

Pour configurer des règles permettant la communication avec le pare-feu ou SELinux activé, consultez les ressources suivantes :

* [procédure iptables](https://help.ubuntu.com/community/IptablesHowTo)
* [Comment modifier les règles iptables (projet fedora)](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [Introduction à SELinux (CentOS.org)](https://www.centos.org)
* [Wiki pratique SELinux (CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### Installation du Java Software Development Kit

Pour déterminer si Java est déjà installé, saisissez la commande suivante :

```bash
java -version
```

Si le message `java: command not found` s’affiche, vous devez installer le SDK Java, comme décrit dans la section suivante.

Consultez l’une des sections suivantes :

* [Installation du dernier JDK sur CentOS](#install-the-jdk-on-centos)
* [Installation du dernier JDK sur Ubuntu](#install-the-jdk-on-ubuntu)

#### Installation du JDK sur CentOS

Voir [Tutoriel sur les océans numériques](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

Assurez-vous d’installer le JDK et *not* JRE.

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>Il se peut que la version 8 de Java ne soit pas disponible pour tous les systèmes d’exploitation. Par exemple, vous pouvez [rechercher la liste des packages disponibles pour Ubuntu ;](https://packages.ubuntu.com/).

#### Installation du JDK sur Ubuntu

Pour installer JDK 1.8 sur Ubuntu, saisissez les commandes suivantes en tant qu’utilisateur avec `root` privilèges :

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

Pour connaître les autres options, voir [Documentation Oracle](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### Installation du moteur de recherche

Suivez [Installation de l’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) ou [Installation et configuration d’OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) pour les étapes spécifiques à votre plateforme.

Pour vérifier que l’Elasticsearch fonctionne, saisissez la commande suivante sur le serveur sur lequel il s’exécute :

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

Un message similaire au suivant s’affiche :

```terminal
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

Pour vérifier que OpenSearch fonctionne, saisissez les commandes suivantes :

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## Mise à niveau d’Elasticsearch

Voir [Mise à niveau d’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) pour obtenir des instructions complètes sur la sauvegarde de vos données, la détection des problèmes de migration potentiels et le test des mises à niveau avant le déploiement en production. Selon votre version actuelle d’Elasticsearch, un redémarrage complet de la grappe peut être nécessaire ou non.

Elasticsearch requiert JDK 1.8 ou version ultérieure. Voir [Installation du Java Software Development Kit](#install-the-java-software-development-kit) pour vérifier quelle version de JDK est installée.

## Ressources supplémentaires

Voir [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) ou [OpenSearch](https://opensearch.org/docs/latest/) la documentation.
