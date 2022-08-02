---
title: Gestion des files d’attente de messages
description: Découvrez comment gérer les files d’attente de messages à partir de la ligne de commande d’Adobe Commerce.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# Gestion des files d’attente de messages

Vous pouvez gérer les files d’attente de messages à partir de la ligne de commande à l’aide de tâches cron ou d’un gestionnaire de processus externe pour vous assurer que les consommateurs récupèrent les messages.

## Gestion des processus

Les tâches Cron sont le mécanisme par défaut pour redémarrer les consommateurs. Processus démarrés par `cron` consommez le nombre de messages spécifié, puis arrêtez-le. Relecture `cron` redémarre le consommateur.

L’exemple suivant illustre la variable `crontab` configuration pour les consommateurs actifs :

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
>La fréquence à laquelle vous vérifiez les files d’attente des messages dépend de la logique métier et des ressources système disponibles. En règle générale, vous pouvez rechercher de nouveaux clients et envoyer plus souvent des emails de bienvenue qu’un processus plus gourmand en ressources, tel que la mise à jour de votre catalogue. Vous devez définir `cron` planifications en fonction des besoins de votre entreprise.
>
>Il peut être configuré dans les options de configuration Admin Magasins > Paramètres > Configuration > Avancé > Système > Cron pour le groupe : consommateurs.
>
>Voir [Configuration et exécution de cron](../cli/configure-cron-jobs.md) pour plus d’informations sur l’utilisation de `cron` avec Commerce.

Vous pouvez également utiliser un gestionnaire de processus tel que [Superviseur](http://supervisord.org/index.html) pour surveiller l’état des processus. Le gestionnaire peut utiliser la ligne de commande pour redémarrer les processus selon les besoins.

## Configuration

### Comportement par défaut

- Tâche Cron `consumers_runner` est activé
- Tâche Cron `consumers_runner` exécute tous les consommateurs définis
- Chaque consommateur traite 10 000 messages, puis s’arrête.

>[!INFO]
>
>Si votre boutique Adobe Commerce est hébergée sur la plateforme Cloud, utilisez la variable [`CRON_CONSUMERS_RUNNER`](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) pour configurer la variable `consumers_runner` tâche cron.

### Configuration spécifique

Modifiez la variable `/app/etc/env.php` fichier pour configurer la tâche cron `consumers_runner`.

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

- `cron_run` - Une valeur booléenne qui active ou désactive la variable `consumers_runner` tâche cron (par défaut = `true`).
- `max_messages` - Nombre maximum de messages que chaque consommateur doit traiter avant de s’arrêter (valeur par défaut = `10000`). Bien que nous ne le recommandions pas, vous pouvez utiliser 0 pour empêcher le consommateur de s’arrêter. Voir [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) pour configurer la manière dont les consommateurs traitent les messages de la file d’attente des messages.
- `consumers` - Un tableau de chaînes spécifiant les consommateurs à exécuter. Un tableau vide s’exécute. *all* consommateurs.
- `multiple_processes` - Un tableau de paires clé-valeur spécifiant le consommateur à exécuter dans le nombre de processus.

   >[!INFO]
   >
   >Il n’est pas recommandé d’exécuter plusieurs consommateurs sur une file d’attente gérée par MySQL. Voir [Remplacer la file d’attente des messages de MySQL par AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) pour plus d’informations.

   >[!INFO]
   >
   >Si votre boutique Adobe Commerce est hébergée sur la plateforme Cloud, utilisez la variable [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://devdocs.magento.com/cloud/env/variables-deploy.html#consumers_wait_for_max_messages) pour configurer la manière dont les consommateurs traitent les messages de la file d’attente des messages.

Voir [Démarrage des consommateurs de la file de messages](../cli/start-message-queues.md).
