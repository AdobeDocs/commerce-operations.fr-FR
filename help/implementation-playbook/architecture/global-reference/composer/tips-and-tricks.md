---
title: Conseils et astuces du compositeur
description: Découvrez les tâches courantes de développement du compositeur et des conseils pour résoudre rapidement les problèmes.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 5ead5fb1-3bb3-4e77-a4f1-8e10c4f91efb
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# Conseils et astuces du compositeur

Vous pouvez rencontrer des problèmes lors du développement de modules Adobe Commerce avec le compositeur. Ces bonnes pratiques décrivent certaines tâches courantes afin de faciliter le développement et de vous aider à résoudre rapidement les problèmes.

>[!NOTE]
>
>Ces instructions s’appliquent principalement aux projets [d’architecture de référence globale (GRA)](../overview.md).

## Compositeur d’accélération

Installez [https://github.com/hirak/prestissimo](https://github.com/hirak/prestissimo) pour accélérer le compositeur avec les téléchargements de modules asynchrones.

```bash
composer global require hirak/prestissimo
```

Si vous rencontrez des problèmes, désinstallez `prestissimo` :

```bash
composer global remove hirak/prestissimo
```

## Résoudre les problèmes de contrôle de version vagues

Le compositeur est parfois bloqué par les versions de package. Vous pouvez voir des messages sur les versions qui sont incompatibles même si elles ne le sont pas. Avant de résoudre les problèmes de compatibilité, essayez de réinitialiser le compositeur :

1. Effacez le cache du compositeur.

   ```bash
   composer clearcache
   ```

1. Supprimez le fichier `composer.lock` pour tous les packages.

   ```bash
   rm -rf vendor/* composer.lock
   ```

1. Réinstallez les packages du compositeur.

   ```bash
   composer install
   ```

>[!TIP]
>
>Ces étapes mettent à jour tous les packages vers la dernière version disponible. Rétablissez le fichier `composer.lock` à partir de Git pour annuler ces mises à niveau.

## Rechercher les éventuelles mises à jour dans les packages client

1. Découvrez quels packages peuvent être obsolètes.

   ```bash
   composer outdated
   ```

1. Filtrez à l’aide de caractères génériques et/ou de l’option `--minor-only` pour ignorer les mises à niveau incompatibles en amont :

   ```bash
   composer outdated 'magento/*'
   composer outdated --minor-only 'magento/*'
   ```

## Déterminer si un module est installé

Affichez les détails de tous les packages installés sur une branche Git.

```bash
composer info
```

Exécutez `composer install` après avoir changé de branches Git et avant d’exécuter `composer info`. Sinon, le compositeur affiche des détails sur la branche précédente que vous avez extraite.

>[!TIP]
>
>Pour filtrer ou rechercher, utilisez l’une des commandes suivantes.
>
>```bash
>composer info '*magento*'
>composer info | grep magento
>```

## Découvrez pourquoi un package (version spécifique d’un package) est installé

Parfois, le compositeur installe la dernière version disponible d’un module en raison d’une dépendance stricte dans un autre module.

Découvrez s’il existe une dépendance stricte dans un autre package.

```bash
composer why client/module-example
```

Si les résultats affichent une liste de métapaquages ou un autre package qui n’est pas explicitement requis, exécutez la commande sur ce package :

```bash
composer why example/metapackage
```

## Découvrez pourquoi un package n’est pas installé

Parfois, le compositeur n’installe pas de package, car il entre en conflit avec un autre package, un autre package le remplace, ou vous ne l’avez pas défini comme une dépendance.

Découvrez pourquoi un package n’est pas installé.

```bash
composer why-not client/module-example
```

## Hébergement d’un référentiel de compositeur privé

Si vous avez besoin d’un référentiel de compositeur privé, utilisez [Private Packagist](https://packagist.com/) ou [JFrog Artifactory](https://jfrog.com/integration/php-composer-repository/). N’utilisez pas [Satis](https://github.com/composer/satis).

- **Private Packagist** est sécurisé, coûte environ 600 USD par an avec trois utilisateurs administrateurs et est hébergé.

- **JFrog Artifactory** commence à $1,176 USD par an. Il n&#39;est pas aussi couramment utilisé que Packagist, mais il prend en charge plus de langages que PHP.

- **Satis** n’a pas de sécurité intégrée, n’a pas d’automatisation et nécessite un hébergement supplémentaire. Il n&#39;est gratuit que si votre temps est également gratuit.

## Modules de contrôle de version

Utilisez [ version sémantique 2.0.0](https://semver.org/spec/v2.0.0.html) comme décrit dans le [schéma de contrôle de version](https://developer.adobe.com/commerce/php/development/versioning/) d’Adobe Commerce. Ne réinventez pas la roue.

Pour les dépendances des modules Adobe Commerce, suivez la documentation [Dépendances des versions de module](https://developer.adobe.com/commerce/php/development/versioning/dependencies/) .

N’utilisez pas la définition de version dans le fichier `composer.json`. Utilisez plutôt des balises Git pour les versions. Voir [Versions et contraintes du compositeur](https://getcomposer.org/doc/articles/versions.md#versions-and-constraints).

## Où placer les modules qui s’affichent dans un fichier d’archive et non dans le compositeur

Créez un référentiel Git pour les modules d’une archive et hébergez-les vous-même. Chaque module Adobe Commerce possède un fichier `composer.json`. Après l’avoir hébergé dans Git et synchronisé avec Private Packagist, vous pouvez l’installer avec Composer.

Lorsque vous recevez une nouvelle version du module, téléchargez le code dans Git, balisez-le, puis installez la nouvelle version avec le compositeur.
