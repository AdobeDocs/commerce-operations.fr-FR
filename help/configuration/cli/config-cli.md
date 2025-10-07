---
title: Outil de ligne de commande
description: Découvrez comment utiliser l’outil de ligne de commande Adobe Commerce pour les tâches d’installation et de configuration. Découvrez les commandes de l’interface de ligne de commande et les fonctions administratives.
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Outil de ligne de commande

Commerce dispose d’une interface de ligne de commande (CLI), `<magento_root>/bin/magento`, qui exécute les tâches d’installation et de configuration, notamment :

- Installation de Commerce (et des tâches associées, telles que la mise à jour du schéma de base de données et la création d’une configuration de déploiement)
- Effacement du cache
- Gestion des index, y compris la réindexation
- Création de dictionnaires de traduction et de packages de traduction
- Génération de classes inexistantes telles que des usines et des intercepteurs pour les plug-ins, génération de la configuration d&#39;injection de dépendance pour le gestionnaire d&#39;objets
- Déploiement de fichiers d’affichage statiques
- Création d’un fichier CSS à partir de moins

Autres avantages :

- Une seule commande (`<magento_root>/bin/magento list`) répertorie toutes les commandes d’installation et de configuration disponibles.
- Interface utilisateur cohérente basée sur Symfony.
- L’interface de ligne de commande est extensible afin que les développeurs tiers puissent s’y connecter. Cela a l&#39;avantage supplémentaire d&#39;éliminer la courbe d&#39;apprentissage des utilisateurs.
- Les commandes des modules désactivés ne s’affichent pas.

Cette rubrique aborde la configuration du logiciel Adobe Commerce à l’aide de l’interface de ligne de commande. Pour plus d’informations sur l’installation de Commerce, voir [Flux d’installation](../../installation/overview.md) dans le _Guide d’installation_.

## Conditions préalables

Avant de commencer à utiliser l’interface en ligne de commande, vérifiez les points suivants :

1. Votre système répond à la configuration requise décrite dans la section [ Configuration requise ](../../installation/system-requirements.md) dans le _Guide d’installation_.
1. Vous avez terminé toutes les tâches préalables décrites dans [Conditions préalables](../../installation/prerequisites/overview.md) dans le _Guide d’installation_.
1. Après vous être connecté au serveur Commerce, passez à un utilisateur disposant des autorisations d’écriture sur le système de fichiers Commerce. Voir [passer au propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) dans le _Guide d’installation_.

## Exécution des commandes

Pour le shell bash, utilisez la syntaxe suivante pour passer au propriétaire du système de fichiers et saisissez simultanément la commande :

```bash
su <file system owner> -s /bin/bash -c <command>
```

Si le propriétaire du système de fichiers n’autorise pas les connexions, vous pouvez utiliser les méthodes suivantes :

```bash
sudo -u <file system owner> <command>
```

**Pour exécuter des commandes d’interface de ligne de commande à partir de n’importe quel répertoire** :

Ajoutez des `<magento_root>/bin` à votre `PATH` système.

Exemple de shell Bash pour CentOS :

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

Vous pouvez éventuellement exécuter les opérations suivantes :

- `cd <magento_root>/bin` et exécutez-les en tant que `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` est un sous-répertoire de votre serveur web docroot
