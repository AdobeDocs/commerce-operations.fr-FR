---
title: Déploiement de fichiers de vue statiques
description: Découvrez comment déployer des fichiers de vues statiques sur le système de fichiers Adobe Commerce en mode production. Découvrez les commandes de déploiement et les techniques d’optimisation.
exl-id: 51954738-b999-4982-954b-70f7a70c5a17
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 0%

---

# Déploiement de fichiers de vue statiques

{{file-system-owner}}

La commande de déploiement de fichiers de vue statique vous permet d’écrire des fichiers statiques dans le système de fichiers Commerce lorsque le logiciel Commerce est défini pour le [&#x200B; mode de production &#x200B;](../bootstrap/application-modes.md#production-mode).

Le terme _fichier de vue statique_ fait référence aux éléments suivants :

- « Statique » signifie qu’il peut être mis en cache pour un site (c’est-à-dire que le fichier n’est pas généré dynamiquement). Par exemple, les images et le code CSS générés à partir de LESS.
- « Affichage » fait référence à la couche de présentation (provenant de MVC).

Les fichiers de vue statiques se trouvent dans le répertoire `<magento_root>/pub/static` et certains sont également mis en cache dans le répertoire `<magento_root>/var/view_preprocessed`.

Le déploiement des fichiers de vue statique est affecté par les modes d’application comme suit :

- [Modes par défaut](../bootstrap/application-modes.md#default-mode) et [développeur](../bootstrap/application-modes.md#developer-mode) : Commerce les génère à la demande, mais les autres sont mis en cache dans un fichier pour accélérer l’accès.
- [Mode de production](../bootstrap/application-modes.md#production-mode) : les fichiers statiques ne sont _pas_ générés ou mis en cache.

Vous devez écrire manuellement les fichiers de vue statique dans le système de fichiers Commerce à l’aide de la commande décrite dans cette rubrique. Ensuite, vous pouvez restreindre les autorisations afin de limiter vos vulnérabilités et d’empêcher l’écrasement accidentel ou malveillant des fichiers.

>[!WARNING]
>
>_Mode Développeur uniquement_ : lorsque vous installez ou activez un nouveau module, il se peut que celui-ci charge de nouveaux JavaScript, CSS, mises en page, etc. Pour éviter tout problème lié aux fichiers statiques, vous devez nettoyer les anciens fichiers afin de vous assurer d’obtenir toutes les modifications pour le nouveau module. Vous pouvez nettoyer les fichiers d’affichage statique générés de plusieurs manières. Pour plus d’informations[&#x200B; voir la rubrique &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) Nettoyer le cache de fichiers statiques .

**Pour déployer des fichiers de vue statiques** :

1. Connectez-vous au serveur Commerce en tant que ou [passez au propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).
1. Supprimez le contenu de `<magento_root>/pub/static`, à l’exception du fichier `.htaccess`. Ne supprimez pas ce fichier.
1. Exécutez le `<magento_root>/bin/magento setup:static-content:deploy` de l’outil de déploiement de fichiers de vue statique .

   >[!INFO]
   >
   >Si vous activez la fusion de fichiers de vue statique dans Admin, le système de répertoires `pub/static` doit pouvoir être accessible en écriture.

   Options de commande :

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

Le tableau suivant explique les paramètres et valeurs de cette commande.

| Option | Description | Obligatoire ? |
| ------ | ----------- | --------- |
| `<languages>` | Liste séparée par des espaces de codes de langue [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php) pour lesquels des fichiers de vue statiques doivent être générés. (La valeur par défaut est `en_US`.)<br>Recherchez la liste en exécutant : `bin/magento info:language:list` | Non |
| `--language (-l)` | Générer des fichiers uniquement pour les langues spécifiées. La valeur par défaut, sans option spécifiée, consiste à générer des fichiers pour tous les codes de langue ISO-639. Vous pouvez spécifier le nom d’un code de langue à la fois. La valeur par défaut est **all**.<br>Par exemple : `--language en_US --language es_ES` | Non |
| `--exclude-language` | Générer des fichiers pour les codes de langue spécifiés. La valeur par défaut, sans option spécifiée, consiste à n’exclure rien. Vous pouvez spécifier le nom d’un code de langue ou une liste de codes de langue séparés par des virgules. La valeur par défaut est **aucune**. | Non |
| `--theme <theme>` | Thèmes pour lesquels déployer du contenu statique. La valeur par défaut est **all**.<br>Par exemple : `--theme Magento/blank --theme Magento/luma` | Non |
| `--exclude-theme <theme>` | Thèmes à exclure lors du déploiement de contenu statique. La valeur par défaut est **aucune**.<br>Par exemple, `--exclude-theme Magento/blank` | Non |
| `--area (-a)` | Générer des fichiers uniquement pour les zones spécifiées. La valeur par défaut, sans option spécifiée, consiste à générer des fichiers pour toutes les zones. Les valeurs valides sont `adminhtml` et `frontend`. La valeur par défaut est **all**.<br>Par exemple : `--area adminhtml` | Non |
| `--exclude-area` | Ne générez pas de fichiers pour les zones spécifiées. La valeur par défaut, sans option spécifiée, consiste à n’exclure rien. La valeur par défaut est **aucune**. | Non |
| `--jobs (-j)` | Activez le [traitement parallèle](manage-indexers.md#reindexing-in-parallel-mode) en utilisant le nombre de tâches spécifié. La valeur par défaut est 0 (ne pas exécuter de processus parallèles). La valeur par défaut est **0**. | Non |
| `--symlink-locale` | Créez des liens symboliques pour les fichiers de ces paramètres régionaux, qui sont transmis pour déploiement, mais n’ont pas de personnalisations. | Non |
| `--content-version=CONTENT-VERSION` | Une version personnalisée du contenu statique peut être utilisée en cas d’exécution du déploiement sur plusieurs nœuds afin de garantir que la version du contenu statique est identique et que la mise en cache fonctionne correctement. | Non |
| `--no-javascript` | Ne déployez pas de fichiers JavaScript | Non |
| `--no-css` | Ne déployez pas de fichiers CSS. | Non |
| `--no-less` | Ne déployez pas de fichiers LESS. | Non |
| `--no-images` | Ne déployez pas d’images. | Non |
| `--no-fonts` | Ne déployez pas de fichiers de polices. | Non |
| `--no-html` | Ne déployez pas de fichiers HTML. | Non |
| `--no-misc` | Ne déployez pas d’autres types de fichiers : MD, JBF, CSV, JSON, TXT, HTC, SWF | Non |
| `--no-html-minify` | Ne minimisez pas les fichiers HTML. | Non |
| `-s <quick\|standard\|compact>` | Définissez la stratégie de déploiement. N’utilisez ces options que si vous disposez de plusieurs instances locales.<ul><li>Utilisez la [stratégie rapide](static-view-file-strategy.md#quick-strategy) pour réduire le temps de déploiement. Il s’agit de l’option de commande par défaut si elle n’est pas spécifiée.</li><li>Utilisez la [stratégie standard](static-view-file-strategy.md#standard-strategy) pour déployer tous les fichiers de vue statiques pour tous les packages.</li><li>Utilisez la [&#x200B; stratégie compacte &#x200B;](static-view-file-strategy.md#compact-strategy) pour économiser de l’espace disque sur le serveur.</li></ul> | Non |
| `--no-parent` | Ne générez pas de fichiers pour les thèmes parents du thème actuel. Il est vivement recommandé d’utiliser cet indicateur si vous n’utilisez pas explicitement le thème parent du thème actuel que vous essayez de déployer. Cela augmente considérablement la vitesse du processus. Cet indicateur est disponible dans Commerce 2.4.2 | Non |
| `--force (-f)` | Déployez des fichiers dans n’importe quel mode. (par défaut, l’outil de déploiement de contenu statique ne peut être exécuté qu’en mode de production. Utilisez cette option pour l’exécuter en mode par défaut ou en mode développeur). | Non |

>[!INFO]
>
>Si vous spécifiez des valeurs pour `<languages>` et `--language`, `<languages>` est prioritaire.

## Exemples

Voici quelques exemples de commandes.

### Exclusion d’un thème et de la minimisation HTML

La commande suivante déploie le contenu statique pour la langue anglaise (`en_US`) américaine, exclut le thème Luma fourni avec Commerce et ne minimise pas les fichiers HTML.

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

Exemple de sortie :

```
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

La commande suivante déploie uniquement JavaScript, avec 4 traitements, avec une stratégie de déploiement standard :

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

La commande suivante déploie uniquement des feuilles CSS et LESS avec 3 tâches et une stratégie de déploiement rapide :

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### Génération de fichiers d’affichage statiques pour un thème et une zone

La commande suivante génère des fichiers d’affichage statiques pour toutes les langues, la zone frontale uniquement, le thème Commerce Luma uniquement, sans générer de polices :

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

Exemple de sortie :

```
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

## Déployer des fichiers de vue statiques sans installer Commerce

Vous pouvez exécuter le processus de déploiement dans un environnement distinct, hors production, afin d’éviter tout processus de génération sur des machines de production sensibles.

Pour ce faire, procédez comme suit :

1. Exécutez [`bin/magento app:config:dump`](../cli/export-configuration.md) pour exporter la configuration à partir de votre système de production.
1. Copiez les fichiers exportés vers la base de code hors production.
1. Déployer des fichiers de vue statiques : `bin/magento setup:static-content:deploy`

## Résolution des problèmes liés à l’outil de déploiement des fichiers de vues statiques

[Installez d’abord le logiciel Commerce](../../installation/overview.md) sinon vous ne pouvez pas exécuter l’outil de déploiement de fichiers de vues statiques.

**Symptôme** : l&#39;erreur suivante s&#39;affiche lorsque vous exécutez l&#39;outil de déploiement de fichiers de vues statiques :

```
ERROR: You need to install the Commerce application before running this utility.
```

**Solution** :

Procédez comme suit :

1. Installez le logiciel Commerce à l’aide de la [ligne de commande](../../installation/composer.md).
1. Connectez-vous au serveur d’applications en tant que propriétaire du système de fichiers ou [&#x200B; passez à &#x200B;](../../installation/prerequisites/file-system/overview.md).
1. Supprimez le contenu `<app_root>/pub/static` répertoire , à l’exception du fichier `.htaccess`. Ne supprimez pas ce fichier.
1. Déployer des fichiers de vue statiques : `bin/magento setup:static-content:deploy`

## Conseil à l’intention des développeurs pour la personnalisation de l’outil de déploiement de contenu statique

Lors de la création d’une implémentation personnalisée de l’outil de déploiement de contenu statique, utilisez uniquement l’écriture de fichiers atomiques pour les fichiers qui doivent être disponibles sur le client. Si vous utilisez une écriture de fichiers non atomique, ces fichiers peuvent être chargés sur le client avec un contenu partiel.

Une des options pour le rendre atomique est d’écrire dans des fichiers stockés dans un répertoire temporaire et de les copier ou de les déplacer vers le répertoire de destination (d’où ils sont chargés sur le client) après l’écriture. Pour plus d&#39;informations sur l&#39;écriture dans des fichiers, voir [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
