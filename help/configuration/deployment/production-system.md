---
title: Configuration du système de production
description: Découvrez comment configurer un système de production pour l’application Commerce.
exl-id: e678e97e-d9f2-4f24-bb6b-1994a2a1167c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Configuration du système de production

Vous pouvez avoir un seul système de production. Tous les éléments suivants doivent être vrais :

- Tout le code Commerce est sous contrôle de code source dans le même référentiel que les systèmes de développement et de création.
- Assurez-vous que tous les éléments suivants sont _inclus_ dans le contrôle source :

   - `app/etc/config.php`
   - Répertoire `generated` (et sous-répertoires)
   - répertoire `pub/media`
   - Répertoire `pub/media/wysiwyg` (et sous-répertoires)
   - Répertoire `pub/static` (et sous-répertoires)

- Commerce 2.2 ou version ultérieure doit être installé et défini pour le [mode de production](../bootstrap/application-modes.md#production-mode)
- Il dispose de droits de propriété et d’autorisations du système de fichiers, comme décrit dans la section [Condition préalable requise pour votre développement, création et production ](../deployment/prerequisites.md).

## Configurer une machine de production

Pour configurer une machine de production :

1. Après avoir installé Commerce ou l’avoir extrait du contrôle de code source, connectez-vous au serveur de production ou passez au propriétaire du système de fichiers.
1. Créez `~/.ssh/.composer/auth.json` si vous ne l’avez pas déjà fait.

   Créez le répertoire :

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   Créez `auth.json` dans ce répertoire.

   `auth.json` doit contenir vos [clés d&#39;authentification](../../installation/prerequisites/authentication-keys.md).

   Voici un exemple :

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. Enregistrez vos modifications dans `auth.json`.
1. Copiez `<Commerce root dir>/app/etc/env.php` de votre système de développement vers votre système de production.
1. Ouvrez `env.php` dans un éditeur de texte et modifiez les valeurs nécessaires (par exemple, les informations de connexion à la base de données).
1. Exécutez la commande [`magento config:set`](../cli/set-configuration-values.md) ou [`magento config:set-sensitive`](../cli/set-configuration-values.md) pour définir les valeurs de toutes les valeurs de configuration sensibles ou spécifiques au système, respectivement.

   La section suivante présente un exemple.

## Définition des valeurs de configuration sur votre système de production

Cette section explique comment définir des valeurs sensibles sur votre système de production à l’aide de la commande `magento config:sensitive:set`.

Pour définir des valeurs sensibles :

1. Recherchez une valeur à définir à l’aide de la [référence de valeur sensible](../reference/config-reference-sens.md).
1. Notez le chemin de configuration du paramètre.
1. Connectez-vous au système de production en tant que propriétaire du système de fichiers ou passez à .
1. Accédez au répertoire d’installation de Commerce.
1. Saisissez la commande suivante :

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   Par exemple, pour définir la valeur de la clé API YouTube sur `1234`, saisissez

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   Vous pouvez également définir une ou plusieurs valeurs de manière interactive comme suit :

   ```bash
   bin/magento config:sensitive:set -i
   ```

   Lorsque vous y êtes invité, saisissez une valeur pour chaque paramètre sensible ou appuyez sur Entrée pour ignorer une valeur et passer à la valeur suivante.

1. Pour vérifier que la valeur a été définie, connectez-vous à l’administrateur.
1. Localisez le paramètre dans Admin.

   Par exemple, le paramètre de clé de l’API YouTube se trouve dans **Magasins** > Paramètres > **Configuration** > **Catalogue** > **Catalogue** > **Vidéo produit**.

   Le paramètre s’affiche dans l’onglet Administration et ne peut pas être modifié. La figure suivante illustre un exemple.

   ![Paramètre sensible dans l’Admin](../../assets/configuration/sensitive-set.png)
