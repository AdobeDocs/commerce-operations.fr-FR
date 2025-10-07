---
title: Définir le mode de fonctionnement
description: Découvrez comment définir des modes de fonctionnement Adobe Commerce entre le développement et la production. Découvrez les commandes de changement de mode et leurs implications en matière de sécurité.
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Définir le mode de fonctionnement

{{file-system-owner}}

Pour améliorer la sécurité et la facilité d’utilisation, nous avons ajouté une commande qui fait basculer [modes d’application](../bootstrap/application-modes.md) du développement vers la production et vice versa.

Le mode de production offre de meilleures performances car les fichiers d’affichage statiques sont renseignés dans le répertoire `pub/static` et en raison de la compilation de code.

>[!INFO]
>
>Dans les versions 2.0.6 et ultérieures, Commerce ne définit pas explicitement les autorisations de fichiers ou de répertoires lorsque vous basculez entre les modes par défaut, de développement et de production. Contrairement aux autres modes, les modes de développement et de production sont définis dans le fichier `env.php`. Adobe Commerce sur les infrastructures cloud prend uniquement en charge les modes de production et de maintenance.
>
>Voir [Propriété et autorisations Commerce en développement et en production](../deployment/file-system-permissions.md).

Lorsque vous passez en mode de développement ou de production, nous effaçons le contenu des répertoires suivants :

```
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

Exceptions :

- Les fichiers `.htaccess` ne sont pas supprimés
- `pub/static` contient un fichier qui spécifie la version du contenu statique ; ce fichier n’est pas supprimé

>[!INFO]
>
>Par défaut, Commerce utilise les répertoires `var` pour stocker le cache, les journaux et le code compilé. Vous pouvez personnaliser ce répertoire, mais dans ce guide, il est supposé être `var`.

## Afficher le mode actuel

Pour ce faire, le plus simple consiste à exécuter cette commande en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md). Si vous avez partagé l’hébergement, il s’agit de l’utilisateur que votre fournisseur vous donne pour vous connecter au serveur. Si vous disposez d’un serveur privé, il s’agit généralement d’un compte utilisateur local sur le serveur Commerce.

Utilisation des commandes :

```bash
bin/magento deploy:mode:show
```

Un message similaire au suivant s’affiche :

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

- **`{mode}`** est obligatoire ; il peut être `developer` ou `production`

- **`--skip-compilation`** est un paramètre facultatif que vous pouvez utiliser pour ignorer [compilation de code](../cli/code-compiler.md) lorsque vous passez en mode de production.

Des exemples suivent.

### Passage en mode de production

```bash
bin/magento deploy:mode:set production
```

Des messages similaires à ce qui suit s’affichent :

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

Lorsque vous passez du mode de production au mode de développement, vous devez effacer les classes générées et les entités Object Manager telles que les proxies pour éviter les erreurs inattendues. Après cela, vous pouvez changer de mode. Procédez comme suit :

1. Si vous passez du mode production au mode développement, supprimez le contenu des répertoires `generated/code` et `generated/metadata` :

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

### Exécutez les commandes de l’interface de ligne de commande n’importe où.

[Exécutez les commandes de l’interface de ligne de commande n’importe où](../cli/config-cli.md#config-install-cli-first).

Si vous n’avez pas ajouté de `<Commerce-install-directory>/bin` à votre `PATH` système, vous pouvez vous attendre à une erreur lors de l’exécution de la commande seule.
