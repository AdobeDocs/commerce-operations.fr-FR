---
title: Définir le mode de fonctionnement
description: Découvrez comment définir les modes de fonctionnement d’Adobe Commerce.
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# Définir le mode de fonctionnement

{{file-system-owner}}

Pour améliorer la sécurité et la facilité d’utilisation, nous avons ajouté une commande qui permet de basculer [modes d&#39;application](../bootstrap/application-modes.md) du développeur à la production et vice versa.

Les performances du mode de production sont meilleures, car les fichiers d’affichage statique sont renseignés dans la variable `pub/static` et à cause de la compilation du code.

>[!INFO]
>
>Dans les versions 2.0.6 et ultérieures, Commerce ne définit pas explicitement les autorisations de fichier ou d’annuaire lorsque vous passez d’un mode par défaut, de développement à un mode de production. Contrairement aux autres modes, les modes de développement et de production sont définis dans la variable `env.php` fichier . Adobe Commerce sur l’infrastructure cloud prend uniquement en charge les modes de production et de maintenance.
>
>Voir [Propriété commerciale et autorisations dans le développement et la production](../deployment/file-system-permissions.md).

Lorsque vous passez en mode Développeur ou Production, nous effacons le contenu des répertoires suivants :

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

Exceptions :

- `.htaccess` Les fichiers ne sont pas supprimés
- `pub/static` contient un fichier qui spécifie la version du contenu statique ; ce fichier n’est pas supprimé.

>[!INFO]
>
>Par défaut, Commerce utilise la variable `var` répertoires pour stocker le cache, les journaux et le code compilé. Vous pouvez personnaliser ce répertoire, mais dans ce guide, il est supposé être `var`.

## Afficher le mode actuel

La méthode la plus simple consiste à exécuter cette commande en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md). Si vous avez partagé l’hébergement, il s’agit de l’utilisateur que votre fournisseur vous donne pour vous connecter au serveur. Si vous disposez d’un serveur privé, il s’agit généralement d’un compte d’utilisateur local sur le serveur Commerce.

Utilisation des commandes :

```bash
bin/magento deploy:mode:show
```

Un message similaire à celui-ci s’affiche :

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

où :

- **`{mode}`** peut être `default`, `developer`, ou `production`

## Modifier les modes

Utilisation des commandes :

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

où :

- **`{mode}`** est requis ; il peut être `developer` ou `production`

- **`--skip-compilation`** est un paramètre facultatif que vous pouvez utiliser pour ignorer [compilation de code](../cli/code-compiler.md) lorsque vous passez en mode de production.

Voici des exemples.

### Passage en mode de production

```bash
bin/magento deploy:mode:set production
```

Messages similaires à l’affichage suivant :

```terminal
Enabled maintenance mode
Requested languages: en_US
=== frontend -> Magento/luma -> en_US ===
... more ...
Successful: 1884 files; errors: 0
---

=== frontend -> Magento/blank -> en_US ===
... more ...
Successful: 1828 files; errors: 0
---

=== adminhtml -> Magento/backend -> en_US ===
... more ...
---

=== Minify templates ===
... more ...
Successful: 897 files modified
---

New version of deployed files: 1440461332
Static content deployment complete
Gathering css/styles-m.less sources.
Successfully processed LESS and/or Sass files
CSS deployment complete
Generated classes:
      Magento\Sales\Api\Data\CreditmemoCommentInterfacePersistor
      Magento\Sales\Api\Data\CreditmemoCommentInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoCommentSearchResultInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoComment\Repository
      Magento\Sales\Api\Data\CreditmemoItemInterfacePersistor
      ... more ...
Compilation complete
Disabled maintenance mode
Enabled production mode.
```

### Passer en mode Développeur

Lorsque vous passez du mode de production au mode Développeur, vous devez effacer les classes générées et les entités du gestionnaire d’objets telles que les proxies pour éviter les erreurs inattendues. Vous pouvez ensuite modifier les modes. Procédez comme suit :

1. Si vous passez du mode de production au mode développeur, supprimez le contenu de la variable `generated/code` et `generated/metadata` répertoires :

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. Définissez le mode :

   ```bash
   bin/magento deploy:mode:set developer
   ```

   Le message suivant s’affiche :

   ```terminal
   Enabled developer mode.
   ```

### Passer en mode par défaut

```bash
bin/magento deploy:mode:set default
```

Le message suivant s’affiche :

```terminal
Enabled default mode.
```

### Exécutez des commandes de ligne de commande n’importe où

[Exécutez des commandes de ligne de commande n’importe où](../cli/config-cli.md#config-install-cli-first).

Si vous n’avez pas ajouté `<Commerce-install-directory>/bin` sur votre système `PATH`, vous pouvez alors vous attendre à une erreur lors de l’exécution de la commande seule.
