---
title: Activation de la journalisation
description: Découvrez comment activer et désactiver les types de journalisation.
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Activation de la journalisation

{{file-system-owner}}

## Journalisation de débogage

Par défaut, Commerce écrit dans le journal de débogage (`<install_directory>/var/log/debug.log`) lorsqu’il est en mode par défaut ou de développement, mais pas lorsqu’il est en mode de production. Utilisez la commande `bin/magento setup:config:set --enable-debug-logging` pour modifier la valeur par défaut.

>[!INFO]
>
>Depuis Commerce 2.3.1, vous ne pouvez plus utiliser la commande `bin/magento config:set dev/debug/debug_logging` pour activer ou désactiver la journalisation de débogage pour le mode actuel.

### Pour activer la journalisation du débogage

1. Utilisez la commande `setup:config:set` pour activer la journalisation de débogage pour le mode actuel.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Videz le cache.

   ```bash
   bin/magento cache:flush
   ```

### Pour désactiver la journalisation du débogage

1. Utilisez la commande `setup:config:set` pour désactiver la journalisation de débogage pour le mode actuel.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Videz le cache.

   ```bash
   bin/magento cache:flush
   ```

## Journalisation de base de données

Par défaut, Commerce écrit les journaux d’activité de la base de données dans le fichier `<install-dir>/var/debug/db.log`.

### Activation de la journalisation de la base de données

1. Utilisez la commande `dev:query-log` pour activer ou désactiver la journalisation de la base de données.

   ```bash
   bin/magento dev:query-log:enable
   ```

   ```bash
   bin/magento dev:query-log:disable
   ```

1. Videz le cache.

   ```bash
   bin/magento cache:flush
   ```

## Journalisation Cron

Avec la version 2.3.1, Commerce crée désormais un journal `cron` distinct. \
Commerce a récemment rendu la journalisation cron plus détaillée, ce qui a fourni plus d’informations mais a considérablement allongé le `system.log`.
Le déplacement de `cron` informations vers un journal dédié facilite la lecture des deux journaux.

Par défaut, Commerce écrit les informations `cron` dans le fichier `<install-directory>/var/log/cron.log`.

## Journalisation Syslog

Par défaut, Commerce écrit les _logs syslog_ dans le fichier `syslog` du système d’exploitation.
Depuis Commerce 2.3.1, vous devez utiliser la commande `magento` pour activer ou désactiver le syslog.
Le paramètre dans l’administrateur a été supprimé.

### Pour activer la journalisation du journal des syslogs

La connexion à `syslog` est désactivée par défaut.

1. Utilisez la commande `setup:config:set` pour remplacer la valeur de base de données `dev/syslog/syslog_logging` par `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Videz le cache.

   ```bash
   bin/magento cache:flush
   ```

### Pour désactiver la journalisation du journal du système

1. Utilisez la commande `setup:config:set` pour remplacer la valeur de base de données `dev/syslog/syslog_logging` par `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Videz le cache.

   ```bash
   bin/magento cache:flush
   ```
