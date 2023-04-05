---
title: Mise à niveau du schéma et des données de la base de données
description: Procédez comme suit pour mettre à niveau votre schéma de base de données Adobe Commerce ou Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# Mise à niveau du schéma et des données de la base de données

Avant d’utiliser cette commande, vous devez : [installation de l’application](../advanced.md).

## Mise à niveau du schéma et des données de la base de données

Chaque fois que vous effectuez une action qui entraîne la modification du schéma ou des données de la base de données, vous devez les mettre à jour en exécutant la commande décrite dans cette section. Voici une liste partielle des raisons :

* Vous avez mis à niveau l’application à l’aide de la ligne de commande
* Vous avez installé ou mis à jour un composant à l’aide de la ligne de commande.
* Vous avez activé ou désactivé un composant à l’aide de la ligne de commande.

>[!NOTE]
>
>A *component* peut être un module, un thème ou un module de langue ; peu importe que le composant provienne ou non du Commerce Marketplace.

1. Démarrez la mise à niveau :

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Où `--keep-generated` est un argument facultatif qui ne met pas à jour [fichiers d’affichage statique](../../configuration/cli/static-view-file-deployment.md). Cet argument facultatif est à utiliser *only* dans des circonstances limitées par des intégrateurs système expérimentés. Il doit être utilisé. *only* in [mode de production](../../configuration/bootstrap/application-modes.md#production-mode). Elle devrait *not* être utilisé dans [mode développeur](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Nettoyez le cache :

   ```bash
   bin/magento cache:clean
   ```
