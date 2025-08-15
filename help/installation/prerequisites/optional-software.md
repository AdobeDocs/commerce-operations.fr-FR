---
title: Logiciels en option
description: En savoir plus sur les logiciels en option que vous pouvez installer pour prendre en charge les installations sur site d’Adobe Commerce.
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Logiciels en option

Nous vous recommandons vivement d’installer NTP pour vous assurer que les tâches liées à cron s’exécutent correctement. (Les dates du serveur peuvent être dans le passé ou dans le futur, par exemple.)

Les autres utilitaires facultatifs décrits dans cette rubrique peuvent vous aider à installer ; toutefois, ils ne sont pas nécessaires pour installer ou utiliser Adobe Commerce.

## Installation et configuration du protocole NTP (Network Time Protocol)

[NTP](https://www.ntp.org/) permet aux serveurs de synchroniser leurs horloges système à l’aide de [serveurs de pool disponibles dans le monde entier](https://www.ntppool.org/en/). Nous vous recommandons d&#39;utiliser des serveurs NTP de confiance, qu&#39;il s&#39;agisse de solutions matérielles dédiées sur votre réseau interne ou de serveurs externes publics.

Si vous déployez Adobe Commerce sur plusieurs hôtes, NTP est un moyen simple de garantir que leurs horloges sont toutes synchronisées, quel que soit le fuseau horaire dans lequel se trouvent les serveurs. En outre, les tâches liées à cron (telles que l’indexation et les e-mails transactionnels) dépendent de l’exactitude de l’horloge du serveur.

### Installer et configurer NTP sur Ubuntu

Saisissez la commande suivante pour installer NTP :

```bash
apt-get install ntp
```

Continuez avec [Utiliser les serveurs de pool NTP](#use-ntp-pool-servers).

### Installation et configuration de NTP sur CentOS

Pour installer et configurer NTP :

1. Saisissez la commande suivante pour trouver le logiciel NTP approprié :

   ```bash
   yum search ntp
   ```

1. Sélectionnez un package à installer. Par exemple, `ntp.x86_64`.

1. Installez le package .

   ```bash
   yum -y install ntp.x86_64
   ```

1. Saisissez la commande suivante afin que NTP démarre au démarrage du serveur.

   ```bash
   chkconfig ntpd on
   ```

1. Passez à la section suivante.

### Utiliser les serveurs du pool NTP

C&#39;est à vous de choisir les serveurs du pool. Si vous utilisez des serveurs de pool NTP, ntp.org vous recommande d&#39;utiliser des serveurs [pool](https://www.ntppool.org/en/) proches du fuseau horaire de vos serveurs, comme indiqué sur la page [projet de pool NTP](https://www.ntppool.org/en/use.html). Si vous disposez d’un serveur NTP privé disponible pour tous les hôtes de votre déploiement , vous pouvez utiliser ce serveur à la place.

1. Ouvrez `/etc/ntp.conf` dans un éditeur de texte.

1. Recherchez des lignes similaires à ce qui suit :

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. Remplacez ces lignes ou ajoutez des lignes supplémentaires qui spécifient votre serveur de pool NTP ou d&#39;autres serveurs NTP. Il est préférable d&#39;en spécifier plusieurs.

1. Voici un exemple d’utilisation de trois serveurs NTP basés aux États-Unis :

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. Enregistrez vos modifications dans `/etc/ntp.conf` et quittez l’éditeur de texte.

1. Redémarrez le service .

   * Ubuntu : `service ntp restart`

   * CentOS : `service ntpd restart`

1. Saisissez `date` pour vérifier la date du serveur.

   Si la date est incorrecte, assurez-vous que le port client NTP (généralement, UDP 123) est ouvert dans votre pare-feu.

   Essayez la commande `ntpdate _[pool server hostname]_`. En cas d’échec, recherchez l’erreur renvoyée.

   Si tout le reste échoue, essayez de redémarrer le serveur.

## Créer phpinfo.php

Le fichier [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) affiche une grande quantité d&#39;informations sur PHP et ses extensions.

>[!NOTE]
>
>Utilisez `phpinfo.php` dans un système de développement _uniquement_. Il peut s’agir d’un problème de sécurité en production.

Ajoutez le code suivant n’importe où dans la racine docroot de votre serveur web :

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

Pour plus d&#39;informations, reportez-vous à la [page du manuel phpinfo](https://www.php.net/manual/en/function.phpinfo.php).

Pour afficher les résultats, saisissez l’URL suivante dans le champ d’emplacement ou d’adresse de votre navigateur :

```http
http://<web server host or IP>/phpinfo.php
```

Si une erreur 404 (Introuvable) s’affiche, vérifiez les points suivants :

* Démarrez le serveur web si nécessaire.
* Vérifiez que votre pare-feu autorise le trafic sur le port 80.

  [Aide pour Ubuntu](https://help.ubuntu.com/community/UFW)

  [Aide de CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)

## phpMyAdmin

L&#39;application phpMyAdmin est un utilitaire d&#39;administration de base de données gratuit et facile à utiliser. Vous pouvez l’utiliser pour vérifier et manipuler le contenu de votre base de données. Vous devez vous connecter à phpMyAdmin en tant qu&#39;utilisateur administrateur de la base de données MySQL.

Pour plus d&#39;informations sur phpMyAdmin, consultez la page d&#39;accueil de [phpMyAdmin](https://www.phpmyadmin.net/).

Pour plus d’informations sur l’installation, consultez la documentation d’installation de [phpMyAdmin](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>Utilisez phpMyAdmin dans un système de développement _uniquement_. Il peut s’agir d’un problème de sécurité en production.

1. Pour utiliser phpMyAdmin, saisissez la commande suivante dans le champ adresse ou emplacement de votre navigateur :

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. Lorsque vous y êtes invité, connectez-vous en utilisant votre `root` de base de données MySQL ou le nom d&#39;utilisateur et le mot de passe de l&#39;utilisateur administrateur.
