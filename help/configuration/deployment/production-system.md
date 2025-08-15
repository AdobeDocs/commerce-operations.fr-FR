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

Vous pouvez avoir un seul système de production. Tout ce qui suit doit être vrai :

- Tout le code Commerce se trouve dans le contrôle de code source dans le même référentiel que les systèmes de développement et de création
- Assurez-vous que tous les éléments suivants sont _inclus_ dans le contrôle de code source :

   - `app/etc/config.php`
   - Répertoire `generated` (et sous-répertoires)
   - répertoire `pub/media`
   - Répertoire `pub/media/wysiwyg` (et sous-répertoires)
   - Répertoire `pub/static` (et sous-répertoires)

- Commerce 2.2 ou une version ultérieure doit être installé et défini pour le [mode de production](../bootstrap/application-modes.md#production-mode)
- La propriété et les autorisations du système de fichiers sont définies, comme indiqué dans la section [Prérequis pour les systèmes de développement, de version et de production](../deployment/prerequisites.md).

## Configuration d’une machine de production

Pour configurer une machine de production :

1. Après l’installation de Commerce ou son extraction du contrôle de code source, connectez-vous au serveur de production en tant que propriétaire du système de fichiers ou passez à celui-ci.
1. Créez des `~/.ssh/.composer/auth.json` si vous ne l’avez pas déjà fait.

   Créez le répertoire :

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   Créez des `auth.json` dans ce répertoire.

   `auth.json` devez contenir vos [ clés d’authentification ](../../installation/prerequisites/authentication-keys.md).

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
1. Copiez le `<Commerce root dir>/app/etc/env.php` de votre système de développement vers votre système de production.
1. Ouvrez `env.php` dans un éditeur de texte et modifiez les valeurs nécessaires (par exemple, les informations de connexion à la base de données).
1. Exécutez la commande [`magento config:set`](../cli/set-configuration-values.md) ou [`magento config:set-sensitive`](../cli/set-configuration-values.md) pour définir les valeurs de toutes les valeurs de configuration sensibles ou spécifiques au système, respectivement.

   La section suivante présente un exemple.

## Définissez les valeurs de configuration sur votre système de production.

Cette section explique comment définir des valeurs sensibles sur votre système d’exploitation à l’aide de la commande `magento config:sensitive:set`.

Pour définir des valeurs sensibles :

1. Recherchez une valeur à définir à l’aide de la [référence de valeur sensible](../reference/config-reference-sens.md).
1. Notez le chemin de configuration du paramètre .
1. Connectez-vous au système de production en tant que propriétaire du système de fichiers ou passez à ce système.
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

   Lorsque vous y êtes invité, saisissez une valeur pour chaque paramètre sensible ou appuyez sur Entrée pour ignorer une valeur et passer à la suivante.

1. Pour vérifier que la valeur a été définie, connectez-vous à l’administration.
1. Recherchez le paramètre dans Admin.

   Par exemple, le paramètre de clé API YouTube se trouve dans **Magasins** > Paramètres > **Configuration** > **Catalogue** > **Catalogue** > **Vidéo du produit**.

   Le paramètre s’affiche dans l’interface d’administration et ne peut pas être modifié. La figure suivante en est un exemple.

   ![Paramètre Sensible dans l’administration](../../assets/configuration/sensitive-set.png)
