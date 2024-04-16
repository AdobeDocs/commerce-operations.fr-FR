---
title: Outil de ligne de commande
description: Utilisez l’outil de ligne de commande Commerce pour exécuter les tâches d’installation et de configuration.
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Outil de ligne de commande

Commerce possède une interface de ligne de commande —`<magento_root>/bin/magento`: exécute les tâches d’installation et de configuration, notamment :

- L’installation de Commerce (et les tâches associées, telles que la mise à jour du schéma de base de données, créer une configuration de déploiement)
- Effacement du cache
- Gestion des index, notamment réindexation
- Création de dictionnaires de traduction et de packages de traduction
- Génération de classes inexistantes, telles que des usines et des intercepteurs pour les modules externes, générant la configuration d’injection de dépendance pour le gestionnaire d’objets
- Déploiement de fichiers d’affichage statique
- Création d’une page CSS à partir de less

Autres avantages :

- Une seule commande (`<magento_root>/bin/magento list`) répertorie toutes les commandes d’installation et de configuration disponibles.
- Interface utilisateur cohérente basée sur Symfony.
- L’interface en ligne de commande est extensible, de sorte que les développeurs tiers puissent y &quot;se connecter&quot;. Cela permet également d’éliminer la courbe d’apprentissage des utilisateurs.
- Les commandes des modules désactivés ne s’affichent pas.

Cette rubrique aborde la configuration du logiciel Adobe Commerce à l’aide de l’interface en ligne de commande. Pour plus d’informations sur l’installation de Commerce, voir [Flux d’installation](../../installation/overview.md) dans le _Guide d’installation_.

## Conditions préalables

Avant de commencer à utiliser l’interface en ligne de commande, assurez-vous que :

1. Votre système répond aux exigences décrites dans la section [Configuration requise](../../installation/system-requirements.md) dans le _Guide d’installation_.
1. Vous avez effectué toutes les tâches prérequises décrites dans la section [Conditions préalables](../../installation/prerequisites/overview.md) dans le _Guide d’installation_.
1. Une fois que vous êtes connecté au serveur Commerce, basculez vers un utilisateur autorisé à écrire sur le système de fichiers Commerce. Voir [passer au propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) dans le _Guide d’installation_.

## Exécution des commandes

Pour le shell bash, utilisez la syntaxe suivante pour passer au propriétaire du système de fichiers et saisissez la commande en même temps :

```bash
su <file system owner> -s /bin/bash -c <command>
```

Si le propriétaire du système de fichiers n’autorise pas les connexions, vous pouvez utiliser les éléments suivants :

```bash
sudo -u <file system owner> <command>
```

**Pour exécuter des commandes d’interface de ligne de commande depuis n’importe quel répertoire**:

Ajouter `<magento_root>/bin` sur votre système `PATH`.

Exemple de shell bash pour CentOS :

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

Vous pouvez éventuellement exécuter les opérations suivantes :

- `cd <magento_root>/bin` et exécutez-les comme `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` est un sous-répertoire de votre serveur web docroot
