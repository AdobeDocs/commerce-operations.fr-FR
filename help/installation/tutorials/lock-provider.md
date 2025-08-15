---
title: Configuration du fournisseur de verrous
description: Suivez ces étapes pour empêcher l’exécution des tâches et des groupes cron en double sur votre déploiement Adobe Commerce.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Configuration du fournisseur de verrous

Avant d’exécuter cette commande, vous devez effectuer les opérations suivantes *ou* vous devez [installer l’application](../advanced.md) :

* [Créer ou mettre à jour la configuration de déploiement](deployment.md)
* [Création du schéma de base de données](database.md)

## Installation sécurisée

{{$include /help/_includes/secure-install.md}}

## Configurer le verrou

Configurez un fournisseur de verrous pour empêcher le lancement de tâches et de groupes cron en double. (Nécessite Adobe Commerce 2.2.x, 2.2.5 et versions ultérieures, et 2.3.3 et versions ultérieures.)

Adobe Commerce utilise la base de données pour enregistrer les verrous par défaut. Si vos serveurs comportent plusieurs nœuds, il est recommandé d’utiliser Zookeeper comme fournisseur de verrou.

Si vous exécutez Adobe Commerce sur une infrastructure cloud, vous n’avez pas besoin de configurer les paramètres du fournisseur de verrouillage. L&#39;application configure le fournisseur de verrouillage de fichiers pour les projets Pro pendant le processus d&#39;approvisionnement. Voir [Variables cloud](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud).

### Utilisation des commandes

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descriptions des paramètres

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--lock-provider` | Verrouiller le nom du fournisseur : `db`, `zookeeper` ou `file`.<br><br>Fournisseur de verrous par défaut : `db` | Non |
| `--lock-db-prefix` | Préfixe de base de données spécifique pour éviter les conflits de verrouillage lors de l&#39;utilisation du fournisseur de verrous `db`.<br><br>Valeur par défaut : `NULL` | Non |
| `--lock-zookeeper-host` | Hôte et port pour la connexion au cluster Zookeeper lorsque vous utilisez le fournisseur de verrouillage `zookeeper`.<br><br>Par exemple : `127.0.0.1:2181` | Oui, si vous définissez `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Chemin où Zookeeper enregistre les verrous.<br><br>Le chemin d’accès par défaut est : `/magento/locks` | Non |
| `--lock-file-path` | Chemin d’accès où les verrous de fichier sont enregistrés. | Oui, si vous définissez `--lock-provider=file` |
