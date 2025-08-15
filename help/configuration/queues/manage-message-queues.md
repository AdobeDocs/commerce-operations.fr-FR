---
title: Gérer les files d'attente de messages
description: Découvrez comment gérer les files d’attente de messages à partir de la ligne de commande pour Adobe Commerce.
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: 8dce1f1e961ec02d7783a7423a51a7d4567dce79
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Gérer les files d&#39;attente de messages

Vous pouvez gérer les files d’attente de messages à partir de la ligne de commande à l’aide de tâches cron ou d’un gestionnaire de processus externe pour vous assurer que les consommateurs récupèrent les messages.

## Gestion des processus

Les tâches cron constituent le mécanisme par défaut pour redémarrer les consommateurs. Les processus lancés par `cron` consomment le nombre de messages spécifié, puis s&#39;arrêtent. La réexécution `cron` redémarre le client.

L’exemple suivant illustre la configuration `crontab` pour l’exécution de consommateurs :

> /app/code/Magento/MessageQueue/etc/crontab.xml

```xml
...
<job name="consumers_runner" instance="Magento\MessageQueue\Model\Cron\ConsumersRunner" method="run">
    <schedule>* * * * *</schedule>
</job>
...
```

>[!INFO]
>
>La fréquence de vérification des files d&#39;attente de messages dépend de la logique de votre entreprise et des ressources système disponibles. En règle générale, vous pouvez rechercher de nouveaux clients et envoyer des e-mails de bienvenue plus fréquemment qu’un processus qui nécessite davantage de ressources, comme la mise à jour de votre catalogue. Vous devez définir des plannings de `cron` en fonction des besoins de votre entreprise.
>
>Il peut être configuré dans les options de configuration Admin Stores > Settings > Configuration > Advanced > System > Cron pour le groupe : consumer.
>
>Voir [Configurer et exécuter cron](../cli/configure-cron-jobs.md) pour plus d’informations sur l’utilisation de `cron` avec Commerce.

Vous pouvez également utiliser un gestionnaire de processus tel que [Superviseur](https://supervisord.readthedocs.io/en/latest/) pour surveiller le statut des processus. Le gestionnaire peut utiliser la ligne de commande pour redémarrer les processus si nécessaire.

## Configuration

### Comportement par défaut

- La tâche cron `consumers_runner` est activée.
- La tâche cron exécute `consumers_runner` tous les consommateurs définis
- Chaque client traite 10000 messages, puis s’arrête

>[!INFO]
>
>Si votre magasin Adobe Commerce est hébergé sur la plateforme cloud, utilisez l’[`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) pour configurer la tâche cron `consumers_runner`.

### Configuration spécifique

Modifiez le fichier `/app/etc/env.php` pour configurer le `consumers_runner` de la tâche cron.

```php
...
    'cron_consumers_runner' => [
        'cron_run' => false,
        'max_messages' => 20000,
        'consumers' => [
            'consumer1',
            'consumer2',
        ],
        'multiple_processes' => [
            'consumer1' => 4
        ]
    ],
...
```

- `cron_run` - Valeur booléenne qui active ou désactive la tâche cron `consumers_runner` (par défaut = `true`).
- `max_messages` - Nombre maximal de messages que chaque client doit traiter avant de s’arrêter (par défaut = `10000`). Bien que nous ne le recommandions pas, vous pouvez utiliser 0 pour empêcher le client de s’arrêter. Consultez [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) pour configurer la manière dont les consommateurs traitent les messages de la file d’attente des messages.
- `consumers` - Tableau de chaînes spécifiant les consommateurs à exécuter. Un tableau vide s’exécute *tous* les consommateurs.
- `multiple_processes` - Tableau de paires clé-valeur spécifiant le client à exécuter dans combien de processus. Pris en charge dans Commerce 2.4.4 ou version ultérieure.

  >[!INFO]
  >
  >Il n’est pas recommandé d’exécuter plusieurs consommateurs sur une file d’attente gérée par MySQL. Voir [Modifier la file d’attente de messages de MySQL vers AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) pour plus d’informations.

  >[!INFO]
  >
  >Si votre boutique Adobe Commerce est hébergée sur la plateforme cloud, utilisez le [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages) pour configurer la manière dont les consommateurs et consommatrices traitent les messages de la file d’attente des messages.

Voir [Démarrer les consommateurs de file d’attente de messages](../cli/start-message-queues.md).
