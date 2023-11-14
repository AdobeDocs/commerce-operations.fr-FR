---
title: Configuration de l’application
description: Découvrez la configuration post-installation requise pour les déploiements Adobe Commerce et Magento Open Source sur site.
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---

# Configuration de l’application

Maintenant que vous avez fini d’installer Adobe Commerce ou Magento Open Source, vous devez le configurer. Cette rubrique fournit quelques paramètres de configuration recommandés.

## Configuration de cron

Le planificateur de tâches UNIX, cron, est essentiel aux opérations quotidiennes de l’application. Il planifie des choses comme la réindexation, les newsletters, les e-mails et les plans de site. A *crontab* est une configuration cron.

Vous devez installer Adobe Commerce et les services Magento Open Source dans le *crontab* ou certaines fonctionnalités de base (et certaines extensions tierces) ne fonctionnent pas correctement.

Pour plus d’informations sur cron, notamment sur la suppression d’un crontab et l’exécution de cron à partir de la ligne de commande, voir [Configuration et exécution de cron](../../configuration/cli/configure-cron-jobs.md).

## Paramètres de sécurité et recommandations

Après l’installation, nous vous recommandons ce qui suit :

* Assurez-vous que la propriété et les autorisations du fichier sont correctement définies.
* Nous vous recommandons vivement [modification de l’URI d’administration par défaut](../tutorials/admin-uri.md) de `admin` vers autre chose
* Assurez-vous que la variable [`X-Frame-Option` En-tête HTTP](../../configuration/security/xframe-options.md) est définie correctement.
* Prenez des précautions contre les scripts de site à site (XSS) en [Sécurisation des modèles](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

Si vous avez installé [clonage du référentiel GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/), assurez-vous que lorsque vous déployez l’application, vous n’incluez que les fichiers et dossiers requis pour l’environnement de production. Les fichiers et les dossiers qui ne sont pas requis peuvent présenter des risques de sécurité.

## Activation des réécritures du serveur Apache

Si vous utilisez le serveur web Apache, vous devez activer les réécritures du serveur pour que les pages s’affichent correctement. Sinon, vous verrez des pages sans styles et d’autres problèmes.

[Section sur les réécritures du serveur Apache](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## Mise en cache dans un environnement multinoeud

Si vous avez plusieurs noeuds web, vous pouvez : *cannot* utilisez la mise en cache de fichier par défaut de l’application, car il n’existe aucune synchronisation entre les noeuds web. En d’autres termes, l’activité sur un noeud web n’est écrite que dans le système de fichiers de ce noeud web. L’activité suivante, si elle est exécutée sur un autre noeud web, peut entraîner l’écriture de fichiers inutiles ou entraîner des erreurs.

Utilisez plutôt [Redis](../../configuration/cache/config-redis.md) pour le cache par défaut et le cache de page.

## Paramètres du serveur

Cette section décrit brièvement les paramètres que nous vous recommandons de prendre en compte pour le serveur sur lequel l’application s’exécute. Certains de ces paramètres ne sont pas directement liés à l’application ; ils sont fournis sous forme de suggestions uniquement.

### Rotation des logs

UNIX `logrotate` permet d’administrer des systèmes qui génèrent un grand nombre de fichiers journaux. Il permet la rotation, la compression, la suppression et l’envoi automatiques des fichiers journaux. Chaque fichier journal peut être traité tous les jours, toutes les semaines, tous les mois ou lorsque la taille du fichier journal dépasse la taille spécifiée.

Pour plus d’informations, voir l’une des sections suivantes :

* [HowTo : tutoriel sur la commande de rotation de journal avec dix exemples](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Stack Exchange](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` page principale](https://linuxconfig.org/logrotate-8-manual-page)

### Configuration de règles iptables pour permettre à différents services de communiquer

Que vous ayez un ou plusieurs serveurs, vous devez ouvrir les ports dans le pare-feu pour permettre aux services de communiquer. Par exemple, si vous utilisez le moteur de recherche Solr avec Adobe Commerce, vous devez l’activer pour communiquer avec le serveur web. Si vous disposez de plusieurs noeuds web, vous devez leur permettre de communiquer entre eux.

En savoir plus :

* Ubuntu : [Page de documentation Ubuntu](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS : [Procédures relatives à CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).

### Règles Linux améliorées (SELinux) de sécurité

Nous n’avons pas de recommandation pour savoir si vous utilisez SELinux ; toutefois, si vous l’utilisez, vous devez configurer les services pour communiquer les uns avec les autres comme pour configurer les iptables.

En savoir plus :

* Ubuntu : [Manuel Debian](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS : [Wiki de CentOS](https://wiki.centos.org/HowTos/SELinux)

### Configuration d’un serveur de messagerie

Adobe Commerce et Magento Open Source nécessitent un serveur de messagerie. Nous ne recommandons pas un serveur particulier, mais vous pouvez essayer l’une des méthodes suivantes :

* Postfix pour CentOS ([Tutoriel sur les océans numériques](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [Documentation CentOS](https://www.centos.org))
* Postfix pour Ubuntu ([Tutoriel sur les océans numériques](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Documentation Ubuntu](https://help.ubuntu.com/community/MailServer))

### Affiner le moteur de recherche pour améliorer les performances :

Elasticsearch ou OpenSearch est requis pour toutes les installations à partir de la version 2.4.0.

* [Installation et configuration du moteur de recherche](../../configuration/search/overview-search.md)

### Configuration d’une file de messages

Depuis la version 2.3.0, Adobe Commerce et Magento Open Source incluent la fonctionnalité de file d’attente des messages. Dans les versions antérieures, il est disponible uniquement pour Adobe Commerce.

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Paramètres pour Adobe Commerce uniquement

Vous ne pouvez configurer les éléments suivants que si vous utilisez Adobe Commerce :

* [Partage de bases de données pour le passage en caisse, la gestion des commandes et d&#39;autres tables de base de données](../../configuration/storage/multi-master.md)
