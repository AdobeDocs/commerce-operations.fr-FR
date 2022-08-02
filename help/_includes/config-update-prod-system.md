---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---
# Mettre à jour le système de production

**Mise à jour du système de production**:

1. Connectez-vous au système de production en tant que propriétaire du système de fichiers.
1. Passez à la racine de l’application et activez le mode de maintenance.

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   Pour connaître d’autres options, telles que la possibilité de définir une liste autorisée d’adresses IP, voir [`magento maintenance:enable`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. Arrêtez tous les programmes de traitement des files d’attente en cours d’exécution en définissant `cron_run` to `false` in `app/etc/env.php` comme suit :

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Mettez à jour la configuration.

   ```bash
   bin/magento app:config:import
   ```

1. Enfin, `kill` tout processus client principal.

   ```bash
   kill <PID>
   ```

   Où `PID` est l’ID de processus à supprimer, par exemple :

   ```bash
   kill 1234
   ```

1. Extrayez le code du contrôle source.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Mettez à jour la configuration.

   ```bash
   bin/magento app:config:import
   ```

1. Nettoyez le cache.

   ```bash
   bin/magento cache:clean
   ```

1. Mode de maintenance de fin.

   ```bash
   bin/magento maintenance:disable
   ```
