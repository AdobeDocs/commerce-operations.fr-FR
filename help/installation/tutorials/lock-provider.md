---
title: Configuration du fournisseur de verrouillage
description: Suivez ces étapes pour empêcher les tâches cron en double et les groupes cron de s’exécuter sur votre déploiement Adobe Commerce ou Magento Open Source.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Configuration du fournisseur de verrouillage

Avant d’exécuter cette commande, procédez comme suit : *ou* vous devez [installation de l’application](../advanced.md):

* [Création ou mise à jour de la configuration du déploiement](deployment.md)
* [Création du schéma de la base de données](database.md)

## Installation sécurisée

{{$include /help/_includes/secure-install.md}}

## Configuration du verrouillage

Configurez un fournisseur de verrouillage pour empêcher le lancement de tâches cron en double et de groupes cron. (Nécessite Adobe Commerce ou Magento Open Source 2.2.x, 2.2.5 et versions ultérieures, 2.3.3 et versions ultérieures.)

Adobe Commerce et Magento Open Source utilisent la base de données pour enregistrer les verrous par défaut. Si vos serveurs contiennent plusieurs noeuds, nous vous recommandons d’utiliser Zookeeper en tant que fournisseur de verrouillage.

Si vous exécutez Adobe Commerce sur l’infrastructure cloud, il n’est pas nécessaire de configurer les paramètres du fournisseur de verrouillage. L’application configure le fournisseur de verrouillage de fichier pour les projets Pro pendant le processus d’approvisionnement. Voir [Variables cloud](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### Utilisation des commandes

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descriptions des paramètres

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--lock-provider` | Verrouiller le nom du fournisseur : `db`, `zookeeper`, ou `file`.<br><br>Le fournisseur de verrouillage par défaut : `db` | Non |
| `--lock-db-prefix` | Le préfixe db spécifique pour éviter les conflits de verrouillage lors de l’utilisation de la fonction `db` fournisseur de verrouillage.<br><br>La valeur par défaut : `NULL` | Non |
| `--lock-zookeeper-host` | Hébergez et port pour vous connecter à la grappe Zookeeper lorsque vous utilisez la méthode `zookeeper` fournisseur de verrouillage.<br><br>Par exemple: `127.0.0.1:2181` | Oui, si vous définissez `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Chemin d’accès dans lequel le gardien de page enregistre les verrous.<br><br>Le chemin par défaut est le suivant : `/magento/locks` | Non |
| `--lock-file-path` | Chemin d’accès où les verrous de fichier sont enregistrés. | Oui, si vous définissez `--lock-provider=file` |
