---
title: Activation de la journalisation
description: Découvrez comment activer et désactiver les types de journalisation.
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Activation de la journalisation

{{file-system-owner}}

## Journalisation de débogage

Par défaut, Commerce écrit dans le journal de débogage (`<install_directory>/var/log/debug.log`) lorsqu’il est en mode par défaut ou de développement, mais pas lorsqu’il est en mode de production. Utilisez la variable `bin/magento setup:config:set --enable-debug-logging` pour modifier la valeur par défaut.

>[!INFO]
>
>À compter de Commerce 2.3.1, vous ne pourrez plus utiliser la variable `bin/magento config:set dev/debug/debug_logging` pour activer ou désactiver la journalisation de débogage pour le mode actuel.

### Pour activer la journalisation du débogage

1. Utilisez la variable `setup:config:set` pour activer la journalisation de débogage pour le mode actuel.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Videz le cache.

   ```bash
   bin/magento cache:flush
   ```

### Pour désactiver la journalisation du débogage

1. Utilisez la variable `setup:config:set` pour désactiver la journalisation de débogage pour le mode actuel.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Videz le cache.

   ```bash
   bin/magento cache:flush
   ```

## Journalisation de base de données

Par défaut, Commerce écrit les journaux d’activité de la base de données dans la variable `<install-dir>/var/debug/db.log` fichier .

### Activation de la journalisation de la base de données

1. Utilisez la variable `dev:query-log` pour activer ou désactiver la journalisation de la base de données.

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

Avec la version 2.3.1, Commerce crée désormais un `cron` log. \
Commerce a récemment rendu la journalisation cron plus détaillée, ce qui a fourni plus d’informations mais a rallongé la durée de la `system.log` considérablement.
Déplacement `cron` Les informations d’un journal dédié facilitent la lecture des deux journaux.

Par défaut, Commerce écrit : `cron` pour `<install-directory>/var/log/cron.log` fichier .

## Journalisation Syslog

Par défaut, Commerce écrit : _syslog_ se connecte au système d’exploitation `syslog` fichier .
Depuis Commerce 2.3.1, vous devez utiliser la variable `magento` pour activer ou désactiver le syslog.
Le paramètre dans l’administrateur a été supprimé.

### Pour activer la journalisation du journal des syslogs

Connexion à `syslog` est désactivé par défaut.

1. Utilisez la variable `setup:config:set` pour modifier la variable `dev/syslog/syslog_logging` valeur de la base de données vers `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Videz le cache.

   ```bash
   bin/magento cache:flush
   ```

### Pour désactiver la journalisation du journal du système

1. Utilisez la variable `setup:config:set` pour modifier la variable `dev/syslog/syslog_logging` valeur de la base de données vers `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Videz le cache.

   ```bash
   bin/magento cache:flush
   ```
