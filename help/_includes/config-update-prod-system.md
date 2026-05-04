---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# Mettre à jour le système de production

**Pour mettre à jour le système d’exploitation** :

1. Connectez-vous au système d’exploitation en tant que propriétaire du système de fichiers.
1. Passez à la racine de l’application et activez le mode de maintenance.

   ```shell
   cd <Magento root dir>
   ```

   ```shell
   bin/magento maintenance:enable
   ```

   Pour d’autres options, telles que la possibilité de définir une liste autorisée d’adresses IP, voir [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md).

1. Arrêtez tous les programmes de traitement de file d’attente en cours d’exécution en définissant `cron_run` sur `false` dans `app/etc/env.php` comme suit :

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Mettez à jour la configuration.

   ```shell
   bin/magento app:config:import
   ```

1. Enfin, `kill` tous les processus consommateurs actifs.

   ```shell
   kill <PID>
   ```

   Où `PID` est l’ID du processus à interrompre, par exemple :

   ```shell
   kill 1234
   ```

1. Extrayez le code du contrôle de code source.

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. Mettez à jour la configuration.

   ```shell
   bin/magento app:config:import
   ```

1. Nettoyez le cache.

   ```shell
   bin/magento cache:clean
   ```

1. Terminez le mode de maintenance.

   ```shell
   bin/magento maintenance:disable
   ```
