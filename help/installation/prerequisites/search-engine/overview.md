---
title: Conditions préalables relatives aux moteurs de recherche
description: Pour installer et configurer le logiciel de moteur de recherche pris en charge pour les installations sur site d’Adobe Commerce, procédez comme suit.
feature: Install, Search
exl-id: 44ea638a-7200-4269-be1b-b0851de2c4f4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# Conditions préalables relatives aux moteurs de recherche

Depuis Adobe Commerce 2.4, toutes les installations doivent être configurées pour utiliser [Elasticsearch](https://www.elastic.co) ou [OpenSearch](https://opensearch.org/) comme solution de recherche de catalogue.

>[!NOTE]
>
>Ajout de la prise en charge d’OpenSearch dans la version 2.4.4. OpenSearch est un formulaire compatible d’Elasticsearch. Toutes les instructions pour configurer Elasticsearch 7 s’appliquent à OpenSearch. [Migration d’Elasticsearch vers OpenSearch](../../../upgrade/prepare/opensearch-migration.md) fournit des conseils sur le passage à OpenSearch.

## Versions prises en charge

Vous devez installer et configurer Elasticsearch ou OpenSearch avant d’installer Adobe Commerce 2.4.4 et versions ultérieures.

Reportez-vous à la section [Configuration requise](../../system-requirements.md) pour obtenir des informations de version spécifiques.

## Configuration recommandée

Nous recommandons ce qui suit :

* [Configuration de Nginx pour votre moteur de recherche](configure-nginx.md)
* [Configuration d’Apache pour votre moteur de recherche](configure-apache.md)

## Emplacement d’installation

Les tâches suivantes supposent que vous ayez configuré votre système en fonction du diagramme suivant :

![Diagramme Moteur de recherche](../../../assets/installation/search-engine-config.svg)

Le diagramme précédent montre :

* L’application Commerce et le moteur de recherche sont installés sur différents hôtes.

  L’exécution sur des hôtes distincts nécessite le fonctionnement d’un proxy. (La mise en cluster du moteur de recherche ne fait pas partie de ce guide, mais vous trouverez plus d’informations dans la [documentation sur la mise en cluster d’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).)

* Chaque hôte possède son propre serveur web ; les serveurs web ne doivent pas nécessairement être les mêmes.

  Par exemple, l’application Commerce peut exécuter Apache et le moteur de recherche nginx.

* Les deux serveurs web utilisent TLS (Transport Layer Security).

  La configuration de TLS dépasse le cadre de notre documentation.

Les demandes de recherche sont traitées comme suit :

1. Une requête de recherche d’un utilisateur est reçue par le serveur web Commerce, qui la transmet au serveur du moteur de recherche.

   Vous configurez le moteur de recherche pour qu’il se connecte à l’hôte et au port du proxy. Nous recommandons le port SSL du serveur web (par défaut, 443).

1. Le serveur web du moteur de recherche (qui écoute sur le port 443) envoie par proxy la requête au serveur du moteur de recherche (par défaut, il écoute sur le port 9200).

1. L’accès au moteur de recherche est également protégé par l’authentification HTTP de base. Pour qu&#39;une requête atteigne le moteur de recherche, il doit passer par SSL *et* fournir un nom d&#39;utilisateur et un mot de passe valides.

1. Le moteur de recherche traite la demande.

1. Les retours de communication s’effectuent le long du même itinéraire, le serveur web Elasticsearch agissant comme proxy inverse sécurisé.

## Conditions préalables

Les tâches décrites dans cette section nécessitent les éléments suivants :

* [Firewall et SELinux](#firewall-and-selinux)
* [Installation du kit de développement logiciel Java (JDK)](#install-the-java-software-development-kit)
* [Installation du moteur de recherche](#install-the-search-engine)
* [Mise à niveau d’Elasticsearch](#upgrading-elasticsearch)

### Firewall et SELinux

Les logiciels liés à la sécurité (iptables, SELinux, AppArmor) peuvent être configurés par défaut pour bloquer la communication entre les sous-systèmes. Il serait peut-être bon de les vérifier s&#39;il y a des problèmes.

#### Configurer des règles pour iptables et SELinux

Pour configurer des règles permettant d’autoriser la communication avec le pare-feu ou SELinux activé, consultez les ressources suivantes :

* [procédure pour iptables](https://help.ubuntu.com/community/IptablesHowTo)
* [Modification des règles d&#39;iptables (projet fedora)](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [Présentation de SELinux (CentOS.org)](https://www.centos.org)
* [SELinux Comment Wiki (CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### Installation du kit de développement logiciel Java

Pour déterminer si Java est déjà installé, saisissez la commande suivante :

```bash
java -version
```

Si le message `java: command not found` s’affiche, vous devez installer Java SDK comme décrit dans la section suivante.

Consultez l’une des sections suivantes :

* [Installer le dernier JDK sous CentOS](#install-the-jdk-on-centos)
* [Installer le dernier JDK sur Ubuntu](#install-the-jdk-on-ubuntu)

#### Installation du JDK sous CentOS

Voir ce [tutoriel sur l’océan numérique](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

Veillez à installer le JDK et *pas* l’environnement JRE.

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>La version 8 de Java peut ne pas être disponible pour tous les systèmes d’exploitation. Par exemple, vous pouvez [rechercher Ubuntu dans la liste des packages disponibles](https://packages.ubuntu.com/).

#### Installation du JDK sur Ubuntu

Pour installer JDK 1.8 sur Ubuntu, saisissez les commandes suivantes en tant qu’utilisateur disposant de droits d’`root` :

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

Pour d’autres options, consultez la [documentation Oracle](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### Installation du moteur de recherche

Suivez [Installation d’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) ou [Installation et configuration d’OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) pour connaître les étapes spécifiques à votre plateforme.

Pour vérifier qu’Elasticsearch fonctionne, saisissez la commande suivante sur le serveur sur lequel il est exécuté :

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

Un message similaire au suivant s’affiche :

```
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

Consultez la section [Mise à niveau d’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) pour obtenir des instructions complètes sur la sauvegarde de vos données, la détection de problèmes de migration potentiels et le test des mises à niveau avant le déploiement en production. Selon la version d’Elasticsearch que vous utilisez, un redémarrage complet du cluster peut être requis.

Elasticsearch nécessite JDK 1.8 ou une version ultérieure. Consultez [Installation du kit de développement logiciel Java](#install-the-java-software-development-kit) pour vérifier quelle version du JDK est installée.

## Ressources supplémentaires

Voir la documentation [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) ou [OpenSearch](https://opensearch.org/docs/latest/).
