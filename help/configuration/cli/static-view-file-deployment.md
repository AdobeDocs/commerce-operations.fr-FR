---
title: Déploiement de fichiers d’affichage statique
description: Découvrez comment écrire des fichiers statiques dans le système de fichiers Commerce en mode de production.
exl-id: 51954738-b999-4982-954b-70f7a70c5a17
source-git-commit: 0a72bc492dfec0a9014a518282a97ab21e59f96d
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---

# Déploiement de fichiers d’affichage statique

{{file-system-owner}}

La commande de déploiement des fichiers d’affichage statique vous permet d’écrire des fichiers statiques dans le système de fichiers Commerce lorsque le logiciel Commerce est défini pour [mode de production](../bootstrap/application-modes.md#production-mode).

Le terme _fichier d’affichage statique_ fait référence à ce qui suit :

- &quot;Statique&quot; signifie qu’il peut être mis en cache pour un site (c’est-à-dire que le fichier n’est pas généré dynamiquement). Par exemple, les images et les CSS générés à partir de LESS.
- &quot;Vue&quot; fait référence à la couche de présentation (mode MVC).

Les fichiers d’affichage statique se trouvent dans la variable `<magento_root>/pub/static` et certains sont mis en cache dans le `<magento_root>/var/view_preprocessed` également.

Le déploiement des fichiers d’affichage statique est affecté par les modes d’application comme suit :

- [Par défaut](../bootstrap/application-modes.md#default-mode) et [développeur](../bootstrap/application-modes.md#developer-mode) modes : le commerce les génère à la demande, mais les autres sont mis en cache dans un fichier pour accélérer l’accès.
- [Production](../bootstrap/application-modes.md#production-mode) mode : les fichiers statiques sont _not_ généré ou mis en cache.

Vous devez écrire manuellement des fichiers d’affichage statique dans le système de fichiers Commerce à l’aide de la commande décrite dans cette rubrique. Ensuite, vous pouvez restreindre les autorisations afin de limiter vos vulnérabilités et d’empêcher le remplacement accidentel ou malveillant de fichiers.

>[!WARNING]
>
>_Mode Développeur uniquement_: lorsque vous installez ou activez un nouveau module, il se peut qu’il charge du nouveau code JavaScript, CSS, mises en page, etc. Pour éviter des problèmes avec les fichiers statiques, vous devez nettoyer les anciens fichiers pour vous assurer d’obtenir toutes les modifications pour le nouveau module. Vous pouvez nettoyer les fichiers d’affichage statique générés de plusieurs façons. Voir [Rubrique Nettoyage du cache des fichiers statiques pour plus de détails](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) pour plus d’informations.

**Pour déployer des fichiers d’affichage statique**:

1. Connectez-vous au serveur Commerce en tant que ou [passer au propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
1. Supprimer le contenu de `<magento_root>/pub/static`, à l’exception de `.htaccess` fichier . Ne supprimez pas ce fichier.
1. Exécution de l’outil de déploiement des fichiers d’affichage statique `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >Si vous activez la fusion des fichiers d’affichage statique dans l’Admin, la variable `pub/static` Le système d’annuaire doit pouvoir être écrit.

   Options de commande :

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

Le tableau suivant explique les paramètres et les valeurs de cette commande.

| Option | Description | Obligatoire ? |
| ------ | ----------- | --------- |
| `<languages>` | Liste séparée par des espaces de [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php) codes de langue pour lesquels générer des fichiers d’affichage statique. (Par défaut : `en_US`.)<br>Recherchez la liste en exécutant : `bin/magento info:language:list` | Non |
| `--language (-l)` | Générez des fichiers uniquement pour les langues spécifiées. La valeur par défaut, sans option spécifiée, est de générer des fichiers pour tous les codes de langue ISO-639. Vous pouvez spécifier le nom d’un code de langue à la fois. La valeur par défaut est **all**.<br>Par exemple : `--language en_US --language es_ES` | Non |
| `--exclude-language` | Générez des fichiers pour les codes de langue spécifiés. La valeur par défaut, sans option spécifiée, est de n’exclure rien. Vous pouvez spécifier le nom d’un code de langue ou d’une liste de codes de langue séparés par des virgules. La valeur par défaut est **none**. | Non |
| `--theme <theme>` | Thèmes pour lesquels déployer du contenu statique. La valeur par défaut est **all**.<br>Par exemple : `--theme Magento/blank --theme Magento/luma` | Non |
| `--exclude-theme <theme>` | Thèmes à exclure lors du déploiement de contenu statique. La valeur par défaut est **none**.<br>Par exemple : `--exclude-theme Magento/blank` | Non |
| `--area (-a)` | Générez des fichiers uniquement pour les zones spécifiées. La valeur par défaut, sans option spécifiée, est de générer des fichiers pour toutes les zones. Les valeurs valides sont `adminhtml` et `frontend`. La valeur par défaut est **all**.<br>Par exemple : `--area adminhtml` | Non |
| `--exclude-area` | Ne générez pas de fichiers pour les zones spécifiées. La valeur par défaut, sans option spécifiée, est de n’exclure rien. La valeur par défaut est **none**. | Non |
| `--jobs (-j)` | Activer [traitement parallèle](manage-indexers.md#reindexing-in-parallel-mode) en utilisant le nombre de tâches spécifié. La valeur par défaut est 0 (ne pas exécuter dans les processus parallèles). La valeur par défaut est **0**. | Non |
| `--symlink-locale` | Créez des liens symboliques pour les fichiers de ces paramètres régionaux, qui sont transmis pour le déploiement, mais sans personnalisation. | Non |
| `--content-version=CONTENT-VERSION` | La version personnalisée du contenu statique peut être utilisée si vous exécutez le déploiement sur plusieurs noeuds afin de vous assurer que la version du contenu statique est identique et que la mise en cache fonctionne correctement. | Non |
| `--no-javascript` | Ne pas déployer de fichiers JavaScript | Non |
| `--no-css` | Ne déployez pas de fichiers CSS. | Non |
| `--no-less` | Ne déployez pas de fichiers LESS. | Non |
| `--no-images` | Ne déployez pas d’images. | Non |
| `--no-fonts` | Ne déployez pas de fichiers de polices. | Non |
| `--no-html` | Ne déployez pas de fichiers de HTML. | Non |
| `--no-misc` | Ne déployez pas d’autres types de fichiers : MD, JBF, CSV, JSON, TXT, HTC, SWF | Non |
| `--no-html-minify` | Ne minimisez pas les fichiers de HTML. | Non |
| `-s <quick\|standard\|compact>` | Définissez la stratégie de déploiement. Utilisez ces options uniquement si vous avez plusieurs locaux.<ul><li>Utilisez la variable [stratégie rapide](static-view-file-strategy.md#quick-strategy) afin de réduire le temps de déploiement. Il s’agit de l’option de commande par défaut si elle n’est pas spécifiée.</li><li>Utilisez la variable [stratégie standard](static-view-file-strategy.md#standard-strategy) pour déployer tous les fichiers d’affichage statique pour tous les modules.</li><li>Utilisez la variable [stratégie compacte](static-view-file-strategy.md#compact-strategy) pour économiser de l’espace disque sur le serveur.</li></ul> | Non |
| `--no-parent` | Ne générez pas de fichiers pour les thèmes parents du thème actuel. Il est vivement recommandé d’utiliser cet indicateur si vous n’utilisez pas explicitement le thème parent du thème actuel que vous essayez de déployer. Cela augmente considérablement la vitesse du processus. Cet indicateur est disponible dans Commerce 2.4.2 | Non |
| `--force (-f)` | Déployez des fichiers dans n’importe quel mode. (par défaut, l’outil de déploiement de contenu statique ne peut être exécuté qu’en mode de production. Utilisez cette option pour l’exécuter en mode par défaut ou en mode développeur). | Non |

>[!INFO]
>
>Si vous spécifiez des valeurs pour les deux `<languages>` et `--language`, `<languages>` a la priorité .

## Exemples

Voici quelques exemples de commande.

### Exclusion d’un thème et d’une minification de HTML

La commande suivante déploie le contenu statique pour l’anglais américain (`en_US`), exclut le thème Luma fourni avec Commerce et ne réduit pas les fichiers de HTML.

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

Exemple de sortie :

```terminal
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/backend
=== frontend -> Magento/blank -> en_US ===
=== adminhtml -> Magento/backend -> en_US ===
...........................................................
... more ...
Successful: 2055 files; errors: 0
---

New version of deployed files: 1466710645
............
Successful: 1993 files; errors: 0
---
```

La commande suivante déploie uniquement JavaScript, avec 4 tâches, avec une stratégie de déploiement standard :

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

La commande suivante déploie uniquement CSS et LESS avec 3 tâches, ainsi qu’une stratégie de déploiement rapide :

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### Génération de fichiers d’affichage statique pour un thème et une zone

La commande suivante génère des fichiers d’affichage statique pour toutes les langues, la zone frontale uniquement, le thème Commerce Luma uniquement, sans générer de polices :

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

Exemple de sortie :

```terminal
Requested languages: en_US
Requested areas: frontend
Requested themes: Magento/luma
=== frontend -> Magento/luma -> en_US ===
...........................................................
... more ...
........................................................................
Successful: 2092 files; errors: 0
---

New version of deployed files: 1466711110
```

## Déployer des fichiers d’affichage statique sans installer Commerce

Vous pouvez exécuter le processus de déploiement dans un environnement distinct, hors production, afin d’éviter tout processus de création sur des machines de production sensibles.

Pour ce faire, procédez comme suit :

1. Exécuter [`bin/magento app:config:dump`](../cli/export-configuration.md) pour exporter la configuration de votre système de production.
1. Copiez les fichiers exportés vers la base de code hors production.
1. Déployer des fichiers d’affichage statique : `bin/magento setup:static-content:deploy`

## Dépannage de l’outil de déploiement des fichiers d’affichage statique

[Installez d’abord le logiciel Commerce.](../../installation/overview.md); dans le cas contraire, vous ne pouvez pas exécuter l’outil de déploiement des fichiers d’affichage statique.

**Symptôme**: l’erreur suivante s’affiche lorsque vous exécutez l’outil de déploiement des fichiers d’affichage statique :

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**Solution**:

Procédez comme suit :

1. Installez le logiciel Commerce à l’aide de la méthode [ligne de commande](../../installation/composer.md).
1. Connectez-vous au serveur d’applications en tant que ou [passer à](../../installation/prerequisites/file-system/overview.md), propriétaire du système de fichiers.
1. Supprimer le contenu de `<app_root>/pub/static` , à l’exception de `.htaccess` fichier . Ne supprimez pas ce fichier.
1. Déployer des fichiers d’affichage statique : `bin/magento setup:static-content:deploy`

## Conseil à l’intention des développeurs sur la personnalisation de l’outil de déploiement de contenu statique

Lors de la création d’une mise en oeuvre personnalisée de l’outil de déploiement de contenu statique, utilisez uniquement l’écriture de fichiers atomiques pour les fichiers qui doivent être disponibles sur le client. Si vous utilisez l’écriture de fichiers non atomiques, ces fichiers peuvent être chargés sur le client avec du contenu partiel.

L’une des options pour la rendre atomique consiste à écrire dans des fichiers stockés dans un répertoire temporaire et à les copier ou à les déplacer vers le répertoire de destination (à partir duquel ils sont chargés sur le client) une fois l’écriture terminée. Pour plus d’informations sur l’écriture dans des fichiers, voir [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
