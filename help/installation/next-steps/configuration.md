---
title: Configuration de l’application
description: Découvrez la configuration post-installation requise pour les déploiements sur site d’Adobe Commerce.
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: a7c98879e027948fc887e28d4baa5fb04214ca95
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# Configuration de l’application

Maintenant que vous avez terminé l’installation d’Adobe Commerce, vous devez le configurer. Cette rubrique fournit quelques paramètres de configuration recommandés.

## Configurer cron

Le planificateur de tâches UNIX, cron, est essentiel au fonctionnement quotidien de l&#39;application. Il planifie des éléments tels que la réindexation, les newsletters, les e-mails et les plans de site. Un *crontab* est une configuration cron.

Vous devez installer les services Adobe Commerce dans le *crontab*, faute de quoi certaines fonctionnalités de base (et certaines extensions tierces) ne fonctionneront pas correctement.

Pour plus d’informations sur cron, notamment sur la suppression d’un cron tab et l’exécution de cron à partir de la ligne de commande, consultez [Configuration et exécution de cron](../../configuration/cli/configure-cron-jobs.md).

## Paramètres de sécurité et recommandations

Après l’installation, nous recommandons ce qui suit :

* Assurez-vous que la propriété et les autorisations des fichiers sont correctement définies [](../prerequisites/file-system/configure-permissions.md)
* Nous vous recommandons vivement de [modifier l’URI d’administration par défaut](../tutorials/admin-uri.md) de `admin` à autre chose
* Assurez-vous que l’en-tête HTTP [`X-Frame-Option`](../../configuration/security/xframe-options.md) est correctement défini.
* Prenez des précautions contre le cross-site scripting (XSS) en [ sécurisant vos modèles ](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

Si vous avez installé en [clonant le référentiel GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/), assurez-vous, lors du déploiement de l’application, d’inclure uniquement les fichiers et les dossiers requis pour l’environnement de production. Les fichiers et les dossiers qui ne sont pas requis peuvent présenter des risques de sécurité.

## Activer les réécritures du serveur Apache

Si vous utilisez le serveur web Apache, vous devez activer les réécritures serveur pour que les pages s’affichent correctement. Dans le cas contraire, vous verrez des pages sans styles et d’autres problèmes.

[Section sur les réécritures du serveur Apache](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## Mise en cache dans un environnement à plusieurs nœuds Web

Si vous disposez de plusieurs nœuds web, vous *ne pouvez pas* utiliser la mise en cache de fichiers par défaut de l’application, car il n’existe aucune synchronisation entre les nœuds web. En d’autres termes, l’activité sur un nœud web est écrite uniquement dans le système de fichiers de ce nœud. Une activité ultérieure, si elle est effectuée sur un autre nœud web, peut entraîner l’écriture de fichiers inutiles ou des erreurs.

Utilisez plutôt [Redis](../../configuration/cache/config-redis.md) pour le cache par défaut et le cache de page.

## Paramètres du serveur

Cette section décrit brièvement les paramètres que nous vous recommandons de prendre en compte pour le serveur sur lequel l’application s’exécute. Certains de ces paramètres ne sont pas directement liés à l’application ; ils sont fournis uniquement à titre de suggestions.

### Rotation des logs

L&#39;utilitaire `logrotate` UNIX permet d&#39;administrer les systèmes qui génèrent un grand nombre de fichiers journaux. Il permet la rotation, la compression, la suppression et le publipostage automatiques des fichiers journaux. Chaque fichier journal peut être géré tous les jours, toutes les semaines, tous les mois ou lorsqu’il dépasse une taille spécifiée.

Pour plus d’informations, voir l’une des rubriques suivantes :

* [Comment faire : tutoriel ultime sur la commande de rotation du journal avec dix exemples](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Échange de pile](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` page man](https://linuxconfig.org/logrotate-8-manual-page)

>[!AVAILABILITY]
>
>Les informations de disponibilité suivantes s’appliquent aux projets d’infrastructure cloud d’Adobe Commerce :
>
>* Les environnements de démarrage n’ont pas de rotation de journal.
>
>* Vous ne pouvez pas configurer la rotation du journal sur les environnements d’intégration Pro. Vous devez implémenter une solution/un script personnalisé(e) et [configurer votre cron](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property) pour exécuter le script selon vos besoins.

### Configurez les règles iptables pour permettre à divers services de communiquer

Que vous ayez un ou plusieurs serveurs, vous devez ouvrir les ports du pare-feu pour permettre aux services de communiquer. Par exemple, si vous utilisez le moteur de recherche Solr avec Adobe Commerce, vous devez l’activer pour communiquer avec le serveur web. Si vous disposez de plusieurs nœuds web, vous devez les autoriser à communiquer entre eux.

Plus d’informations :

* Ubuntu : [page de documentation Ubuntu](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS : procédure [CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).

### Règles de sécurité Linux (SELinux) améliorées

Nous n&#39;avons pas de recommandation pour savoir si vous utilisez SELinux ; cependant, si vous l&#39;utilisez, vous devez configurer des services pour communiquer entre eux de la même manière que pour configurer iptables.

Plus d’informations :

* Ubuntu : [ Manuel Debian ](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS : [wiki CentOS](https://wiki.centos.org/HowTos/SELinux)

### Configuration d&#39;un serveur de messagerie

Adobe Commerce requiert un serveur de messagerie. Nous ne recommandons pas un serveur en particulier, mais vous pouvez essayer l’une des méthodes suivantes :

* Correctif pour CentOS ([tutoriel Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [documentation CentOS](https://www.centos.org))
* Postfix pour Ubuntu ([Digital Ocean tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [documentation Ubuntu](https://help.ubuntu.com/community/MailServer))

### Affinez le moteur de recherche pour améliorer les performances :

Elasticsearch ou OpenSearch est requis pour toutes les installations à compter de la version 2.4.0.

* [Installation et configuration du moteur de recherche](../../configuration/search/overview-search.md)

### Configurer une file d’attente de messages

Depuis la version 2.3.0, Adobe Commerce inclut la fonctionnalité de file d’attente de messages. Dans les versions antérieures, elle était uniquement disponible pour Adobe Commerce.

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Paramètres pour Adobe Commerce uniquement

Vous ne pouvez configurer les éléments suivants que si vous utilisez Adobe Commerce :

* [Bases de données fractionnées pour l&#39;extraction, la gestion des commandes et d&#39;autres tables de base de données](../../configuration/storage/multi-master.md)
