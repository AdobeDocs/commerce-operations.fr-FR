---
title: Définir le mode de fonctionnement
description: Découvrez comment définir les modes de fonctionnement d’Adobe Commerce.
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Définir le mode de fonctionnement

{{file-system-owner}}

Pour améliorer la sécurité et la facilité d&#39;utilisation, nous avons ajouté une commande qui passe de [modes d&#39;application](../bootstrap/application-modes.md) du développeur à la production et vice versa.

Le mode de production offre de meilleures performances car les fichiers de vue statiques sont renseignés dans le répertoire `pub/static` et à cause de la compilation du code.

>[!INFO]
>
>Dans les versions 2.0.6 et ultérieures, Commerce ne définit pas explicitement les autorisations de fichier ou de répertoire lorsque vous passez d’un mode par défaut, de développement à un mode de production. Contrairement aux autres modes, les modes de développement et de production sont définis dans le fichier `env.php`. Adobe Commerce sur l’infrastructure cloud prend uniquement en charge les modes de production et de maintenance.
>
>Voir [Propriété Commerce et autorisations dans le développement et la production](../deployment/file-system-permissions.md).

Lorsque vous passez en mode Développeur ou Production, nous effacons le contenu des répertoires suivants :

```
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

Exceptions :

- `.htaccess` fichiers ne sont pas supprimés
- `pub/static` contient un fichier qui spécifie la version du contenu statique ; ce fichier n’est pas supprimé.

>[!INFO]
>
>Par défaut, Commerce utilise les répertoires `var` pour stocker le cache, les journaux et le code compilé. Vous pouvez personnaliser ce répertoire, mais dans ce guide, il est supposé être `var`.

## Afficher le mode actuel

Pour ce faire, la méthode la plus simple consiste à exécuter cette commande en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md). Si vous avez partagé l’hébergement, il s’agit de l’utilisateur que votre fournisseur vous donne pour vous connecter au serveur. Si vous disposez d’un serveur privé, il s’agit généralement d’un compte utilisateur local sur le serveur Commerce.

Utilisation des commandes :

```bash
bin/magento deploy:mode:show
```

Un message similaire à celui-ci s’affiche :

```
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

où :

- **`{mode}`** peut être `default`, `developer` ou `production`

## Modifier les modes

Utilisation des commandes :

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

où :

- **`{mode}`** est requis ; il peut s’agir de `developer` ou de `production`

- **`--skip-compilation`** est un paramètre facultatif que vous pouvez utiliser pour ignorer la [compilation de code](../cli/code-compiler.md) lorsque vous passez en mode de production.

Voici des exemples.

### Passage en mode de production

```bash
bin/magento deploy:mode:set production
```

Messages similaires à l’affichage suivant :

```
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

1. Si vous passez du mode de production au mode développeur, supprimez le contenu des répertoires `generated/code` et `generated/metadata` :

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. Définissez le mode :

   ```bash
   bin/magento deploy:mode:set developer
   ```

   Le message suivant s’affiche :

   ```
   Enabled developer mode.
   ```

### Passer en mode par défaut

```bash
bin/magento deploy:mode:set default
```

Le message suivant s’affiche :

```
Enabled default mode.
```

### Exécutez des commandes de ligne de commande n’importe où

[Exécutez les commandes de l’interface de ligne de commande n’importe où](../cli/config-cli.md#config-install-cli-first).

Si vous n&#39;avez pas ajouté `<Commerce-install-directory>/bin` à votre système `PATH`, vous pouvez vous attendre à une erreur lors de l&#39;exécution de la commande seule.
