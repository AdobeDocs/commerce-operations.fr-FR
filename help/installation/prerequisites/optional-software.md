---
title: Logiciels facultatifs
description: Découvrez les logiciels facultatifs que vous pouvez installer pour prendre en charge les installations sur site d’Adobe Commerce et de Magento Open Source.
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---

# Logiciels facultatifs

Nous vous recommandons vivement d’installer NTP pour vous assurer que les tâches liées à cron fonctionnent correctement. (Les dates du serveur peuvent être passées ou futures, par exemple.)

Les autres utilitaires facultatifs abordés dans cette rubrique peuvent vous aider à effectuer votre installation. Toutefois, ils ne sont pas nécessaires pour installer ou utiliser Adobe Commerce ou Magento Open Source.

## Installation et configuration du protocole NTP (Network Time Protocol)

[NTP](https://www.ntp.org/) permet aux serveurs de synchroniser leurs horloges système à l’aide de [serveurs de pool disponibles globalement](https://www.ntppool.org/en/). Nous vous recommandons d’utiliser des serveurs NTP en qui vous avez confiance, qu’il s’agisse de solutions matérielles dédiées à votre réseau interne ou de serveurs publics externes.

Si vous déployez Adobe Commerce ou Magento Open Source sur plusieurs hôtes, NTP est un moyen simple de garantir que leurs horloges sont toutes synchronisées, quel que soit le fuseau horaire des serveurs. En outre, les tâches liées à cron (telles que l’indexation et les emails transactionnels) dépendent de la précision de l’horloge du serveur.

### Installation et configuration de NTP sur Ubuntu

Saisissez la commande suivante pour installer NTP :

```bash
apt-get install ntp
```

Passez à la [Utiliser les serveurs de pool NTP](#use-ntp-pool-servers).

### Installation et configuration de NTP sur CentOS

Pour installer et configurer NTP :

1. Saisissez la commande suivante pour trouver le logiciel NTP approprié :

   ```bash
   yum search ntp
   ```

1. Sélectionnez un package à installer. Par exemple, `ntp.x86_64`.

1. Installez le package.

   ```bash
   yum -y install ntp.x86_64
   ```

1. Saisissez la commande suivante afin que NTP démarre au démarrage du serveur.

   ```bash
   chkconfig ntpd on
   ```

1. Passez à la section suivante.

### Utiliser les serveurs de pool NTP

C’est à vous de choisir les serveurs de pool. Si vous utilisez des serveurs de pool NTP, ntp.org vous recommande d&#39;utiliser [serveurs de pool](https://www.ntppool.org/en/) qui sont proches du fuseau horaire de vos serveurs, comme indiqué dans la section [Page de projet de pool NTP](https://www.ntppool.org/en/use.html). Si votre déploiement comprend un serveur NTP privé disponible pour tous les hôtes, vous pouvez utiliser ce serveur à la place.

1. Ouvrir `/etc/ntp.conf` dans un éditeur de texte.

1. Recherchez des lignes similaires à celles-ci :

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. Remplacez ces lignes ou ajoutez des lignes supplémentaires qui spécifient votre serveur de pool NTP ou d&#39;autres serveurs NTP. C&#39;est une bonne idée de spécifier plus d&#39;un.

1. Voici un exemple d’utilisation de trois serveurs NTP basés aux États-Unis :

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. Enregistrez vos modifications dans `/etc/ntp.conf` et quittez l’éditeur de texte.

1. Redémarrez le service.

   * Ubuntu : `service ntp restart`

   * CentOS : `service ntpd restart`

1. Entrée `date` pour vérifier la date du serveur.

   Si la date est incorrecte, assurez-vous que le port client NTP (généralement UDP 123) est ouvert dans votre pare-feu.

   Essayez le `ntpdate _[pool server hostname]_` . En cas d’échec, recherchez l’erreur renvoyée.

   Si tout le reste échoue, essayez de redémarrer le serveur.

## Créer phpinfo.php

La variable [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) affiche une grande quantité d’informations sur PHP et ses extensions.

>[!NOTE]
>
>Utilisation `phpinfo.php` dans un système de développement _only_. Il peut s’agir d’un problème de sécurité en production.

Ajoutez le code suivant n’importe où dans la docroot de votre serveur web :

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

Pour plus d’informations, voir [page manuelle phpinfo](https://www.php.net/manual/en/function.phpinfo.php).

Pour afficher les résultats, saisissez l’URL suivante dans le champ de l’emplacement ou de l’adresse de votre navigateur :

```http
http://<web server host or IP>/phpinfo.php
```

Si une erreur 404 (Introuvable) s’affiche, vérifiez les points suivants :

* Démarrez le serveur web si nécessaire.
* Assurez-vous que votre pare-feu autorise le trafic sur le port 80.

  [Aide pour Ubuntu](https://help.ubuntu.com/community/UFW)

  [Aide de CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)

## phpMyAdmin

L’application phpMyAdmin est un utilitaire d’administration de base de données gratuit et facile à utiliser. Vous pouvez l’utiliser pour vérifier et manipuler le contenu de votre base de données. Vous devez vous connecter à phpMyAdmin en tant qu’utilisateur administrateur de base de données MySQL.

Pour plus d’informations sur phpMyAdmin, voir [page d’accueil phpMyAdmin](https://www.phpmyadmin.net/).

Pour plus d’informations sur l’installation, voir [Documentation sur l’installation de phpMyAdmin](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>Utilisation de phpMyAdmin dans un système de développement _only_. Il peut s’agir d’un problème de sécurité en production.

1. Pour utiliser phpMyAdmin, saisissez la commande suivante dans le champ d’adresse ou d’emplacement de votre navigateur :

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. Lorsque vous y êtes invité, connectez-vous à l’aide de votre base de données MySQL. `root` ou le nom d’utilisateur et le mot de passe de l’administrateur.
