---
title: Migration de RabbitMQ vers ActiveMQ
description: Découvrez comment remplacer le courtier de file d’attente des messages utilisé pour les installations sur site d’Adobe Commerce.
feature: Services, Configuration
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---

# Migration vers ActiveMQ

ActiveMQ (Apache ActiveMQ Artemis) est un courtier de messages multiprotocole haute performance qui fournit une alternative à RabbitMQ pour la gestion des files d’attente de messages dans Adobe Commerce.

Depuis la version 2.4.8-p3, 2.4.7-p8, 2.4.6-p13 et 2.4.5-p16, Adobe Commerce prend en charge ActiveMQ en tant que courtier de file d’attente de messages. Cela offre une flexibilité supplémentaire aux installations sur site pour choisir entre RabbitMQ et ActiveMQ en fonction de leurs exigences en matière d’infrastructure et de leur expertise.

## Avant de commencer

Avant de commencer la migration, vérifiez les points suivants :

1. Vérifiez votre configuration RabbitMQ actuelle dans `app/etc/env.php`.
1. Effectuez une sauvegarde complète de votre base de données et de votre base de code.
1. Vérifiez que votre installation est conforme à la configuration requise pour ActiveMQ.
1. Planifiez une période de maintenance pour terminer la migration.

## Chemin de migration

La migration vers ActiveMQ est un processus simple, mais il est essentiel de s’assurer que tous les messages en attente sont traités avant de changer de courtier.

Ces instructions de migration supposent qu’Adobe Commerce est la seule application utilisant le courtier de file d’attente de messages.

### Étape 1 : placer le site en mode de maintenance

1. Placez le site en [mode de maintenance](../../installation/tutorials/maintenance-mode.md) :

   ```bash
   bin/magento maintenance:enable
   ```

1. Vérifiez que le mode de maintenance est activé :

   ```bash
   bin/magento maintenance:status
   ```

### Étape 2 : vérifier le nombre de messages RabbitMQ

Avant de poursuivre, vérifiez que tous les messages de RabbitMQ ont été traités. Utilisez l’une des méthodes suivantes :

#### Méthode A : Utilisation du tableau de bord de gestion RabbitMQ

1. Accédez à l’interface utilisateur de gestion RabbitMQ à l’adresse `http://<host>:15672`
1. Informations d’identification par défaut : `guest/guest`
1. Accédez à l’onglet **Files d’attente**
1. Vérifiez que toutes les files d&#39;attente affichent **0 messages**

   ![Tableau de bord de gestion RabbitMQ](../../assets/upgrade-guide/rabbitmq_mgmt_dashboard.png)

#### Méthode B : utilisation de la ligne de commande rabbitmqctl

1. Vérifiez toutes les files d’attente et leur nombre de messages :

   ```bash
   rabbitmqctl list_queues name messages consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl.png" alt="Sortie de l’interface de ligne de commande RabbitMQ" width="500" />

1. Vérifiez les informations détaillées sur la file d’attente :

   ```bash
   rabbitmqctl list_queues name messages messages_ready messages_unacknowledged consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl_detailed.png" alt="Sortie détaillée de l’interface de ligne de commande RabbitMQ" width="500" />

### Etape 3 : Traiter les messages en attente

Si des messages sont en attente dans une file d’attente, traitez-les avant de continuer.

1. Obtenez la liste des consommateurs disponibles :

   ```bash
   bin/magento queue:consumers:list
   ```

1. Traitez les consommateurs en tant que groupe ou par file d’attente de messages individuelle :

   - **Traiter les consommateurs en tant que groupe**

     ```bash
     bin/magento cron:run --group=consumers
     ```

     >[!NOTE]
     >
     >Si cron est déjà en cours d’exécution sur votre système, il n’est pas nécessaire de l’exécuter `bin/magento cron:run --group=consumers` manuellement. Vérifiez plutôt que les messages sont traités en vérifiant le nombre de messages à l’aide des commandes de l’étape 2.

   - **Traitement d’une file d’attente de messages spécifique**

     ```bash
     bin/magento queue:consumers:start <consumer_name> --max-messages=<number>
     ```

     Par exemple, pour traiter des opérations asynchrones :

     ```bash
     bin/magento queue:consumers:start async.operations.all --max-messages=1000
     ```

     >[!NOTE]
     >
     >Le paramètre `--max-messages` limite le nombre de messages à traiter avant l’arrêt du client. Ajustez cette valeur en fonction de la taille de votre file d’attente.

   - **Surveiller le traitement des messages**

     Vérifiez en permanence le nombre de messages jusqu’à ce que toutes les files d’attente soient vides :

     ```bash
     # Check every few seconds until 0 messages remain
     watch -n 5 "rabbitmqctl list_queues name messages | grep -v '^Listing' | grep -v '0$'"
     ```

### Étape 4 : vérifier que tous les messages sont traités

Avant de passer à l’étape suivante, assurez-vous que **toutes les files d’attente affichent 0 message**. Exécutez à nouveau les commandes de vérification à partir de l’étape 2.

>[!WARNING]
>
>Ne passez pas à l’étape suivante si des messages restent non traités. Une perte de données peut se produire si vous changez de courtier alors que les messages sont toujours en attente.

### Étape 5 : Arrêter les consommateurs et les tâches cron

1. Arrêtez tous les consommateurs de files d’attente de messages en cours d’exécution :

   ```bash
   # If using supervisor
   supervisorctl stop all
   
   # Or manually kill consumer processes
   pkill -f "queue:consumers:start"
   ```

1. Désactivez les tâches cron :

   ```bash
   bin/magento cron:remove
   ```

1. Vérifiez que les tâches cron sont supprimées :

   ```bash
   crontab -l
   ```

### Étape 6 : Sauvegarder la configuration actuelle

Créez une sauvegarde de votre configuration actuelle :

```bash
cp app/etc/env.php app/etc/env.php.backup.rabbitmq
```

### Étape 7 : Désinstallez éventuellement RabbitMQ

Vous pouvez désinstaller RabbitMQ s’il n’est plus nécessaire.

### Étape 8 : installer et configurer ActiveMQ dans Adobe Commerce

Pour effectuer les tâches d&#39;installation et de configuration d&#39;ActiveMQ telles que la configuration du protocole STOMP et la vérification de la connexion, consultez le [ Guide d&#39;installation et de configuration](../../installation/prerequisites/activemq.md).

### Étape 9 : réinstaller les tâches cron

1. Une fois le test terminé, réinstallez les tâches cron :

   ```bash
   bin/magento cron:install
   ```

1. Vérifiez que les tâches cron sont planifiées :

   ```bash
   crontab -l
   ```

### Étape 10 : Désactiver le mode de maintenance

1. Après avoir vérifié que tout fonctionne correctement, désactivez le mode de maintenance :

   ```bash
   bin/magento maintenance:disable
   ```

1. Vérifiez que le mode de maintenance est désactivé :

   ```bash
   bin/magento maintenance:status
   ```

### Étape 11 : surveiller le système

Surveillez votre système pendant 24 à 48 heures après la migration pour vous assurer que toutes les opérations de file d’attente fonctionnent correctement :

- Vérifiez régulièrement le débit des messages dans la console web ActiveMQ
- Surveiller les journaux d’application pour détecter les erreurs liées à la file d’attente
- Vérifiez que les opérations asynchrones (enregistrements de configuration, exportations, etc.) fonctionnent.
- Vérifiez les journaux cron pour vous assurer que les consommateurs et consommatrices fonctionnent.

```bash
# Monitor system logs for queue activity
tail -f var/log/system.log | grep -i queue

# Monitor cron logs
tail -f var/log/cron.log

# Check running consumer processes
ps aux | grep "queue:consumers:start"
```

## Restaurer

Si des problèmes se produisent pendant ou après la migration, vous pouvez revenir à RabbitMQ :

1. Activez le mode de maintenance :

   ```bash
   bin/magento maintenance:enable
   ```

1. Arrêtez tous les consommateurs et désactivez cron :

   ```bash
   pkill -f "queue:consumers:start"
   bin/magento cron:remove
   ```

1. Restaurez la configuration précédente :

   ```bash
   cp app/etc/env.php.backup.rabbitmq app/etc/env.php
   ```

1. Démarrez RabbitMQ (si arrêté) :

   ```bash
   sudo systemctl start rabbitmq-server
   ```

1. Effacer le cache :

   ```bash
   bin/magento cache:flush
   ```

1. Réinstallez cron :

   ```bash
   bin/magento cron:install
   ```

1. Désactivez le mode de maintenance :

   ```bash
   bin/magento maintenance:disable
   ```

Aucune autre modification de la valeur de configuration n’est nécessaire une fois la migration terminée.

