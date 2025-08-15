---
title: Mise à niveau du schéma et des données de la base de données
description: Pour mettre à niveau votre schéma de base de données Adobe Commerce, procédez comme suit.
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Mise à niveau du schéma et des données de la base de données

Avant d’utiliser cette commande, vous devez [installer l’application](../advanced.md).

## Mise à niveau du schéma et des données de la base de données

Chaque fois que vous effectuez une action qui entraîne la modification du schéma ou des données de la base de données, vous devez les mettre à jour en exécutant la commande décrite dans cette section. Voici une liste partielle de raisons :

* Vous avez mis à niveau l’application à l’aide de la ligne de commande
* Pour installer ou mettre à jour un composant, utilisez la ligne de commande
* Vous avez activé ou désactivé un composant en utilisant la ligne de commande

>[!NOTE]
>
>Un *composant* peut être un module, un thème ou un module linguistique ; que le composant vienne du Commerce Marketplace ou non n’a pas d’importance.

1. Démarrez la mise à niveau :

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Où `--keep-generated` est un argument facultatif qui ne met pas à jour les [fichiers d’affichage statiques](../../configuration/cli/static-view-file-deployment.md). Cet argument facultatif est à utiliser *uniquement* dans des circonstances limitées par des intégrateurs système expérimentés. Il doit être utilisé *uniquement* en [mode de production](../../configuration/bootstrap/application-modes.md#production-mode). Il ne doit *pas* être utilisé en [mode Développeur](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Nettoyez le cache :

   ```bash
   bin/magento cache:clean
   ```
