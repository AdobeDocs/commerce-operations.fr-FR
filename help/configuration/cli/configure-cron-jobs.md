---
title: Configuration et exécution des tâches cron
description: Découvrez comment configurer et gérer les tâches cron dans Adobe Commerce. Découvrez les techniques de planification, de configuration et de dépannage.
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Configuration des tâches cron

{{file-system-owner}}

Plusieurs fonctionnalités de Commerce nécessitent au moins une tâche cron, qui planifie les activités à venir. Voici une liste partielle de ces activités :

- Règles de prix de catalogue
- Newsletters
- Génération de plans de site Google
- Alertes/notifications du client (modification du prix du produit, retour du produit en stock)
- Réindexation
- Ventes privées (Adobe Commerce uniquement)
- Mise à jour automatique des taux de change
- Tous les e-mails Commerce (y compris la confirmation de commande et les messages transactionnels)

>[!WARNING]
>
>Vous ne pouvez plus exécuter `dev/tools/cron.sh` car le script a été supprimé.

>[!INFO]
>
>Commerce dépend de la configuration correcte de la tâche cron pour de nombreuses fonctions système importantes, y compris l’indexation. Si cette configuration n’est pas effectuée correctement, Commerce ne fonctionnera pas comme prévu.

Les systèmes UNIX planifient les tâches que doivent effectuer des utilisateurs spécifiques à l&#39;aide d&#39;un fichier _crontab_, qui contient des instructions destinées au démon cron indiquant au démon en vigueur d&#39;« exécuter cette commande à ce moment-là à cette date ». Chaque utilisateur possède son propre crontab, et les commandes d&#39;un crontab donné sont exécutées en tant qu&#39;utilisateur propriétaire.

Pour exécuter cron dans un navigateur Web, consultez [Sécuriser cron.php pour l&#39;exécuter dans un navigateur](../security/secure-cron-php.md).

## Création ou suppression du crontab Commerce

Cette section explique comment créer ou supprimer votre crontab Commerce (c’est-à-dire la configuration des tâches cron Commerce).

Le _crontab_ est la configuration utilisée pour exécuter les tâches cron.

L’application Commerce utilise des tâches cron qui peuvent s’exécuter avec différentes configurations. La configuration de ligne de commande PHP contrôle la tâche cron générale qui réindexe les indexeurs, génère des e-mails, génère le plan du site, etc.

>[!WARNING]
>
>- Pour éviter tout problème lors de l&#39;installation et de la mise à niveau, nous vous recommandons vivement d&#39;appliquer les mêmes paramètres PHP à la configuration de ligne de commande PHP et à la configuration du plug-in du serveur web PHP. Pour plus d&#39;informations, voir [Paramètres PHP requis](../../installation/prerequisites/php-settings.md).
>- Dans un système à plusieurs nœuds, crontab ne peut s’exécuter que sur un seul nœud. Cela s’applique uniquement si vous configurez plusieurs nœuds web pour des raisons liées aux performances ou à l’évolutivité.

### Création du crontab Commerce

À partir de la version 2.2, Commerce crée un crontab pour vous. Nous ajoutons le crontab Commerce à tout crontab configuré pour le propriétaire du système de fichiers Commerce. En d’autres termes, si vous configurez déjà crontabs pour d’autres extensions ou applications, nous y ajoutons le crontab Commerce.

Le crontab Commerce se trouve dans `#~ MAGENTO START` et `#~ MAGENTO END` des commentaires dans votre crontab.

Pour créer le crontab Commerce :

1. Connectez-vous en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) ou passez-y.
1. Modifiez votre répertoire d’installation Commerce.
1. Saisissez la commande suivante :

   ```bash
   bin/magento cron:install [--force]
   ```

Utilisez `--force` pour réécrire un crontab existant.

>[!INFO]
>
>- `magento cron:install` ne réécrit pas un crontab existant dans `#~ MAGENTO START` et `#~ MAGENTO END` des commentaires dans votre crontab.
>- `magento cron:install --force` n’a aucun effet sur les tâches cron en dehors des commentaires de Commerce.

Pour afficher crontab, saisissez la commande suivante en tant que propriétaire du système de fichiers :

```bash
crontab -l
```

Voici un exemple :

```
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>Le fichier `update/cron.php` a été supprimé dans Commerce 2.4.0. Si ce fichier existe sur votre installation, il peut être supprimé en toute sécurité.
>
>Toute référence à `update/cron.php` et `bin/magento setup:cron:run` doit également être supprimée de crontab.

### Supprimez le crontab Commerce.

Supprimez le crontab Commerce uniquement avant de désinstaller l’application Commerce.

Pour supprimer le crontab Commerce :

1. Connectez-vous en tant que ou passez au [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
1. Accédez au répertoire d’installation de Commerce.
1. Saisissez la commande suivante :

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Cette commande n’a aucun effet sur les tâches cron en dehors de la `#~ MAGENTO START` et `#~ MAGENTO END` les commentaires dans votre crontab.

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

Pour configurer des tâches et des groupes cron personnalisés, voir [Configuration de tâches et de groupes cron personnalisés](../cron/custom-cron.md).

>[!INFO]
>
>Vous devez exécuter cron deux fois : la première fois pour découvrir les tâches à exécuter et la seconde fois pour exécuter les tâches elles-mêmes. La deuxième exécution cron doit avoir lieu à l’heure `scheduled_at` ou après pour chaque tâche.

## Journalisation

Toutes `cron` informations sur le travail ont été déplacées de `system.log` vers une `cron.log` distincte.
Par défaut, les informations cron se trouvent à l’adresse `<install_directory>/var/log/cron.log`.
Toutes les exceptions des tâches cron sont consignées par `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

En plus d’être connecté `cron.log` :

- Les tâches ayant échoué avec les statuts `ERROR` et `MISSED` sont consignées dans le `<install_directory>/var/log/support_report.log`.

- Les tâches avec un statut `ERROR` sont toujours enregistrées comme `CRITICAL` dans `<install_directory>/var/log/exception.log`.

- Les tâches avec un statut `MISSED` sont consignées comme `INFO` dans le répertoire `<install_directory>/var/log/debug.log` (mode développeur uniquement).

>[!INFO]
>
>Toutes les données cron sont également écrites dans la table `cron_schedule` de la base de données Commerce. Le tableau fournit un historique des tâches cron, notamment :
>
>- Identifiant et code du traitement
>- Statut
>- Date de création
>- Date planifiée
>- Date d’exécution
>- Date de fin
>
>Pour afficher les enregistrements dans la table, connectez-vous à la base de données Commerce sur la ligne de commande et saisissez `SELECT * from cron_schedule;`.
