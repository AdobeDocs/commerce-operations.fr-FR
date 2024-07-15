---
title: Gestion des files d’attente de messages
description: Découvrez comment gérer les files d’attente de messages à partir de la ligne de commande d’Adobe Commerce.
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: 8dce1f1e961ec02d7783a7423a51a7d4567dce79
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Gestion des files d’attente de messages

Vous pouvez gérer les files d’attente de messages à partir de la ligne de commande à l’aide de tâches cron ou d’un gestionnaire de processus externe pour vous assurer que les consommateurs récupèrent les messages.

## Gestion des processus

Les tâches Cron sont le mécanisme par défaut pour redémarrer les consommateurs. Les processus démarrés par `cron` utilisent le nombre spécifié de messages, puis s’arrêtent. La réexécution de `cron` redémarre le consommateur.

L’exemple suivant illustre la configuration `crontab` pour l’exécution des consommateurs :

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
>La fréquence à laquelle vous vérifiez les files d’attente des messages peut dépendre de la logique métier et des ressources système disponibles. En règle générale, vous pouvez rechercher de nouveaux clients et envoyer plus souvent des emails de bienvenue qu’un processus plus gourmand en ressources, tel que la mise à jour de votre catalogue. Vous devez définir des planifications `cron` en fonction des besoins de votre entreprise.
>
>Il peut être configuré dans les options de configuration Admin Magasins > Paramètres > Configuration > Avancé > Système > Cron pour le groupe : consommateurs.
>
>Voir [Configuration et exécution de cron](../cli/configure-cron-jobs.md) pour plus d’informations sur l’utilisation de `cron` avec Commerce.

Vous pouvez également utiliser un gestionnaire de processus tel que [Superviseur](https://supervisord.readthedocs.io/en/latest/) pour surveiller l’état des processus. Le gestionnaire peut utiliser la ligne de commande pour redémarrer les processus selon les besoins.

## Configuration

### Comportement par défaut

- La tâche Cron `consumers_runner` est activée.
- La tâche Cron `consumers_runner` exécute tous les consommateurs définis.
- Chaque consommateur traite 10 000 messages, puis s’arrête

>[!INFO]
>
>Si votre boutique Adobe Commerce est hébergée sur la plateforme Cloud, utilisez [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) pour configurer la tâche cron `consumers_runner`.

### Configuration spécifique

Modifiez le fichier `/app/etc/env.php` pour configurer la tâche cron `consumers_runner`.

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

- `cron_run` - Une valeur booléenne qui active ou désactive la tâche `consumers_runner` cron (par défaut = `true`).
- `max_messages` - Nombre maximal de messages que chaque consommateur doit traiter avant de s’arrêter (par défaut = `10000`). Bien que nous ne le recommandions pas, vous pouvez utiliser 0 pour empêcher le consommateur de s’arrêter. Voir [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) pour configurer la manière dont les consommateurs traitent les messages de la file d’attente des messages.
- `consumers` - Un tableau de chaînes spécifiant les consommateurs à exécuter. Un tableau vide exécute *tous les* consommateurs.
- `multiple_processes` - Un tableau de paires clé-valeur spécifiant le consommateur à exécuter dans le nombre de processus. Pris en charge dans Commerce 2.4.4 ou version ultérieure.

  >[!INFO]
  >
  >Il est déconseillé d’exécuter plusieurs consommateurs sur une file d’attente gérée par MySQL. Pour plus d’informations, voir [Changement de la file d’attente des messages de MySQL en AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) .

  >[!INFO]
  >
  >Si votre boutique Adobe Commerce est hébergée sur la plateforme Cloud, utilisez [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages) pour configurer la manière dont les clients traitent les messages de la file d’attente des messages.

Voir [Démarrage des consommateurs de la file d’attente de messages](../cli/start-message-queues.md).
