---
title: Configuration et exécution de tâches cron
description: Découvrez comment gérer les tâches cron.
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%

---

# Configuration des tâches cron

{{file-system-owner}}

Plusieurs fonctionnalités de Commerce nécessitent au moins une tâche cron, qui planifie les activités à venir. Une liste partielle de ces activités est la suivante :

- Règles de prix du catalogue
- Newsletters
- Génération de plans de site Google
- Alertes/notifications client (changement de prix du produit, retour en stock)
- Réindexation
- Ventes privées (Adobe Commerce uniquement)
- Mise à jour automatique des taux de change
- Tous les courriers électroniques Commerce (y compris la confirmation de commande et les transactions)

>[!WARNING]
>
>Vous ne pouvez plus exécuter `dev/tools/cron.sh`, car le script a été supprimé.

>[!INFO]
>
>Commerce dépend de la configuration correcte des tâches cron pour de nombreuses fonctions système importantes, y compris l’indexation. Si vous ne le configurez pas correctement, Commerce ne fonctionnera pas comme prévu.

Les systèmes UNIX planifient les tâches à effectuer par des utilisateurs particuliers à l’aide d’un _crontab_, qui est un fichier contenant des instructions au démon cron qui indique au démon en vigueur d’&quot;exécuter cette commande à cette date&quot;. Chaque utilisateur possède son propre crontab et les commandes de n’importe quel crontab donné sont exécutées en tant qu’utilisateur propriétaire.

Pour exécuter cron dans un navigateur web, voir [Secure cron.php à exécuter dans un navigateur](../security/secure-cron-php.md).

## Création ou suppression de l’onglet crontab Commerce

Cette section explique comment créer ou supprimer votre crontab Commerce (c’est-à-dire la configuration des tâches Commerce cron).

_crontab_ est la configuration utilisée pour exécuter des tâches cron.

L’application Commerce utilise des tâches cron qui peuvent s’exécuter avec différentes configurations. La configuration de ligne de commande PHP contrôle la tâche cron générale qui reindexe les indexeurs, génère des courriers électroniques, génère le plan du site, etc.

>[!WARNING]
>
>- Pour éviter tout problème lors de l’installation et de la mise à niveau, nous vous recommandons vivement d’appliquer les mêmes paramètres PHP à la configuration de la ligne de commande PHP et à la configuration du plug-in du serveur web PHP. Pour plus d’informations, voir [Paramètres PHP requis](../../installation/prerequisites/php-settings.md).
>- Dans un système à plusieurs noeuds, crontab ne peut s’exécuter que sur un seul noeud. Cela s’applique uniquement si vous configurez plusieurs noeuds web pour des raisons de performances ou d’évolutivité.

### Création de l’onglet crontab Commerce

À partir de la version 2.2, Commerce crée un crontab pour vous. Nous ajoutons le crontab Commerce à tout crontab configuré pour le propriétaire du système de fichiers Commerce. En d’autres termes, si vous avez déjà configuré des onglets pour d’autres extensions ou applications, nous lui ajoutons le crontab Commerce.

Le crontab Commerce se trouve à l’intérieur des commentaires `#~ MAGENTO START` et `#~ MAGENTO END` de votre crontab.

Pour créer le sous-onglet Commerce :

1. Connectez-vous en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) ou basculez vers cet emplacement.
1. Accédez au répertoire d’installation de Commerce.
1. Saisissez la commande suivante :

   ```bash
   bin/magento cron:install [--force]
   ```

Utilisez `--force` pour réécrire un crontab existant.

>[!INFO]
>
>- `magento cron:install` ne réécrit pas un crontab existant dans les commentaires `#~ MAGENTO START` et `#~ MAGENTO END` de votre crontab.
>- `magento cron:install --force` n’a aucun effet sur les tâches cron en dehors des commentaires Commerce.

Pour afficher crontab, saisissez la commande suivante en tant que propriétaire du système de fichiers :

```bash
crontab -l
```

Voici un exemple :

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>Le fichier `update/cron.php` a été supprimé dans Commerce 2.4.0. S’il existe dans votre installation, il peut être supprimé en toute sécurité.
>
>Toute référence à `update/cron.php` et `bin/magento setup:cron:run` doit également être supprimée de crontab&#39;

### Suppression de l’onglet crontab Commerce

Vous ne devez supprimer le crontab Commerce que avant de désinstaller l’application Commerce.

Pour supprimer le crontab Commerce :

1. Connectez-vous en tant que ou basculez vers le [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
1. Accédez au répertoire d’installation de Commerce.
1. Saisissez la commande suivante :

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Cette commande n’a aucun effet sur les tâches cron en dehors des commentaires `#~ MAGENTO START` et `#~ MAGENTO END` de votre crontab.

## Exécutez cron depuis la ligne de commande

Options de commande :

```bash
bin/magento cron:run [--group="<cron group name>"]
```

où `--group` spécifie le groupe cron à exécuter (omettez cette option pour exécuter cron pour tous les groupes)

Pour exécuter la tâche cron d’indexation, saisissez :

```bash
bin/magento cron:run --group index
```

Pour exécuter la tâche cron par défaut, saisissez :

```bash
bin/magento cron:run --group default
```

Pour configurer des tâches et des groupes cron personnalisés, voir [Configuration de tâches cron personnalisées et de groupes cron](../cron/custom-cron.md).

>[!INFO]
>
>Vous devez exécuter cron deux fois : la première fois pour découvrir des tâches à exécuter et la deuxième fois — pour exécuter les tâches elles-mêmes. La seconde exécution cron doit avoir lieu au ou après l’heure `scheduled_at` de chaque tâche.

## Journalisation

Toutes les informations sur la tâche `cron` ont été déplacées de `system.log` vers un `cron.log` distinct.
Par défaut, les informations cron se trouvent à l’adresse `<install_directory>/var/log/cron.log`.
Toutes les exceptions des tâches cron sont consignées par `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

En plus d&#39;être connecté à `cron.log` :

- Les tâches ayant échoué avec les états `ERROR` et `MISSED` sont consignées dans le journal `<install_directory>/var/log/support_report.log`.

- Les tâches avec un état `ERROR` sont toujours consignées sous la forme `CRITICAL` dans `<install_directory>/var/log/exception.log`.

- Les tâches avec l’état `MISSED` sont consignées en tant que `INFO` dans le répertoire `<install_directory>/var/log/debug.log` (mode développeur uniquement).

>[!INFO]
>
>Toutes les données cron sont également écrites dans la table `cron_schedule` de la base de données Commerce. Le tableau fournit un historique des tâches cron, notamment :
>
>- Identifiant et code de la tâche
>- État
>- Date de création
>- Date planifiée
>- Date d&#39;exécution
>- Date de fin
>
>Pour afficher les enregistrements dans la table, connectez-vous à la base de données Commerce sur la ligne de commande et saisissez `SELECT * from cron_schedule;`.
