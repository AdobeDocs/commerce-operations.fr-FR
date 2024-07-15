---
title: Optimisation des fichiers de ressources CSS et JS
description: Découvrez comment fusionner et réduire des fichiers CSS et JavaScript (JS) pour les projets Adobe Commerce à partir de l’administrateur ou de la ligne de commande.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Optimisation des fichiers de ressources

Pour un site Commerce plus réactif, optimisez les fichiers de ressources CSS et JavaScript (JS) et supprimez les ressources de blocage du rendu.

- **Optimiser les fichiers CSS et JS** : réduisez le temps nécessaire au chargement des fichiers CSS et JavaScript (JS) en configurant Adobe Commerce pour fusionner, minifier et regrouper des fichiers séparés dans un seul fichier.
- **Éliminer les ressources de blocage de rendu** : envisagez de fournir des fonctionnalités JS et CSS critiques en ligne et de différer tous les styles JS/CSS non critiques. Pour plus d’informations, voir [Eliminer les ressources de blocage de rendu](https://web.dev/render-blocking-resources/).

## Produits et versions concernés

[Toutes les versions prises en charge, 2.3 et versions ultérieures](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Fusion ou minimisation de fichiers CSS

Il est possible de réduire le temps nécessaire au chargement des fichiers CSS et JavaScript (JS) en fusionnant, en minimisant et en regroupant des fichiers distincts dans un seul fichier.

>[!IMPORTANT]
>
>Adobe Commerce sur l’infrastructure cloud s’exécute toujours en mode de production et il n’est pas possible de le définir autrement. Par conséquent, vous devez utiliser la méthode de ligne de commande pour activer la fusion, la minification et le regroupement.

Ne fusionnez ou ne regroupez pas de fichiers si votre déploiement utilise HTTP/2. HTTP/2 télécharge les fichiers statiques de manière asynchrone. Les navigateurs doivent télécharger un fichier fusionné entier avant de traiter le contenu du fichier.

### Utilisation de l’administrateur

Pour activer la fusion ou la minification CSS, accédez à [!UICONTROL **Admin** > **Magasins** > **Paramètre** > **Configuration** > **Avancé** > **Développeur** > **Paramètres CSS**].

### Utilisation de la ligne de commande

Pour activer la fusion CSS dans Adobe Commerce sur l’infrastructure cloud :

1. Exécutez cette commande localement :

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Validez les modifications apportées au fichier `app/etc/config.php` et redéployez-les.

Pour activer la minimisation CSS dans Adobe Commerce sur l’infrastructure cloud :

1. Exécutez cette commande localement :

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Validez les modifications apportées au fichier `app/etc/config.php` et redéployez-les.

## Minimisation des fichiers JS

### Utilisation de l’administrateur

Sur la barre latérale *Admin*, accédez à **Magasins** > **Paramètres** > **Configuration** > **Avancé** > **Développeur** > **Paramètres JavaScript**.

### Utilisation de la ligne de commande

Pour activer la minification JS dans Adobe Commerce sur l’infrastructure cloud :

1. Exécutez cette commande localement :

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Validez les modifications apportées au fichier `app/etc/config.php` et redéployez-les.

## Fusion et regroupement de fichiers JS

Vous pouvez activer la fusion ou le regroupement dans l’administration Commerce (la fusion et le regroupement ne peuvent pas être activés en même temps) : [!UICONTROL **Magasins** > **Paramètres** > **Configuration** > **Avancé** > **Développeur** > **Paramètres JavaScript**].

Vous pouvez également activer le regroupement intégré Adobe Commerce (regroupement de base) à partir de la ligne de commande :

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Informations supplémentaires

- [Paramètres d’optimisation côté client](../../../performance/configuration.md#client-side-optimization-settings)
- [Guide de l’utilisateur : optimisation des fichiers de ressources](https://docs.magento.com/user-guide/system/file-optimization.html)
- [Guide du développeur front-end : fusion, minification CSS et performances du site](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Lots JavaScript avancés](../../../performance/advanced-js-bundling.md)
