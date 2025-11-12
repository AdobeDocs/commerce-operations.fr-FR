---
title: Activer la journalisation
description: Découvrez comment activer et désactiver différents types de connexion dans Adobe Commerce. Découvrez la configuration et les techniques de gestion de la journalisation.
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: aff705cefcd4de38d17cad41628bc8dbd6d630cb
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Activer la journalisation

{{file-system-owner}}

## Journalisation du débogage

Par défaut, Commerce écrit dans le journal de débogage (`<install_directory>/var/log/debug.log`) lorsqu’il est en mode par défaut ou en mode de développement, mais pas lorsqu’il est en mode de production. Utilisez la commande `bin/magento setup:config:set --enable-debug-logging` pour modifier la valeur par défaut.

>[!INFO]
>
>Depuis Commerce version 2.3.1, vous ne pouvez plus utiliser la commande `bin/magento config:set dev/debug/debug_logging` pour activer ou désactiver l’enregistrement de débogage pour le mode actuel.

### Pour activer la journalisation du débogage

1. Utilisez la commande `setup:config:set` pour activer l’enregistrement de débogage pour le mode actuel.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Videz le cache.

   ```bash
   bin/magento cache:flush
   ```

### Pour désactiver l’enregistrement de débogage

1. Utilisez la commande `setup:config:set` pour désactiver l’enregistrement de débogage pour le mode actuel.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Videz le cache.

   ```bash
   bin/magento cache:flush
   ```

## Journalisation de la base de données

Par défaut, Commerce écrit les journaux d’activité de la base de données dans le fichier `<install-dir>/var/debug/db.log`.

### Emplacement de stockage de la journalisation des requêtes

Lorsque la journalisation de la base de données est activée, Commerce stocke les journaux de requête à l’emplacement suivant :

- **Fichier journal de requête** : `<install-directory>/var/debug/db.log`
- **Répertoire des journaux** : `<install-directory>/var/debug/`

Le journal des requêtes contient :
- Requêtes SQL exécutées par l’application
- Délais d’exécution des requêtes
- Paramètres de requête et liaisons
- Informations de connexion à la base de données

>[!NOTE]
>
>Le fichier journal de requête peut croître rapidement dans les environnements à trafic élevé. Surveillez l’espace disque et envisagez d’implémenter la rotation du journal ou le nettoyage périodique du fichier journal des requêtes.

### Pour activer la journalisation de la base de données

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

### Pour afficher les journaux de requête

Vous pouvez afficher les journaux de requête à l’aide des commandes d’affichage de fichier standard :

```bash
# View the entire query log
cat var/debug/db.log

# View the last 100 lines of the query log
tail -n 100 var/debug/db.log

# Monitor the query log in real-time
tail -f var/debug/db.log

# Search for specific queries
grep "SELECT" var/debug/db.log
```

## Journalisation cron

Avec la version 2.3.1 de , Commerce crée désormais un journal de `cron` distinct. \
Commerce a récemment rendu la journalisation cron plus détaillée, ce qui a fourni plus d’informations mais a considérablement allongé la `system.log`.
Le déplacement `cron` informations vers un journal dédié facilite la lecture des deux journaux.

Par défaut, Commerce écrit `cron` informations dans le fichier `<install-directory>/var/log/cron.log`.

## Journalisation Syslog

Par défaut, Commerce écrit les journaux _syslog_ dans le fichier `syslog` du système d’exploitation.
À compter de la version 2.3.1 de Commerce, vous devez utiliser la commande `magento` pour activer ou désactiver le journal système.
Le paramètre dans Admin a été supprimé.

### Pour activer la journalisation syslog

La connexion à `syslog` est désactivée par défaut.

1. Utilisez la commande `setup:config:set` pour remplacer la valeur de la base de données `dev/syslog/syslog_logging` par `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Videz le cache.

   ```bash
   bin/magento cache:flush
   ```

### Pour désactiver la journalisation du journal système

1. Utilisez la commande `setup:config:set` pour remplacer la valeur de la base de données `dev/syslog/syslog_logging` par `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Videz le cache.

   ```bash
   bin/magento cache:flush
   ```
