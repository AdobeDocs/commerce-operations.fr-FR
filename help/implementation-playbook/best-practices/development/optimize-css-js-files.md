---
title: Optimisation des fichiers de ressources CSS et JS
description: Découvrez comment fusionner et réduire les fichiers CSS et JavaScript (JS) pour les projets Adobe Commerce à partir de l’Administration ou de la ligne de commande.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: a08560eb307638a36fdc52224c41bdf2c5d47763
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Optimisation des fichiers de ressources

Pour un site Commerce plus réactif, optimisez les fichiers de ressources CSS et JavaScript (JS) et éliminez les ressources bloquant le rendu.

- **Optimiser les fichiers CSS et JS** : réduisez le temps nécessaire au chargement des fichiers CSS et JavaScript (JS) en configurant Adobe Commerce pour réduire et regrouper les fichiers.
- **Éliminer les ressources bloquant le rendu**—Envisagez de fournir des fonctionnalités JS et CSS essentielles en ligne et de différer tous les styles JS/CSS non critiques. Pour obtenir des conseils, voir [Éliminer les ressources bloquant le rendu](https://web.dev/render-blocking-resources/).

## Produits et versions concernés

[Toutes les versions prises en charge, 2.3 et ultérieures](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Fusion ou minimisation de fichiers CSS

Le temps de chargement des fichiers CSS et JavaScript (JS) peut être réduit en fusionnant, en réduisant et en regroupant des fichiers distincts en un seul fichier.

>[!IMPORTANT]
>
>Adobe Commerce sur l’infrastructure cloud s’exécute toujours en mode Production et il n’est pas possible de le définir autrement. Vous devez donc utiliser la méthode de ligne de commande pour activer la fusion, la minimisation et le regroupement.

Ne fusionnez pas ou ne regroupez pas les fichiers si votre déploiement utilise HTTP/2. HTTP/2 télécharge les fichiers statiques de manière asynchrone. Les navigateurs doivent télécharger un fichier fusionné complet avant de traiter le contenu du fichier.

### Utilisation de l’administrateur

Pour activer la fusion ou la minimisation CSS, accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL CSS Settings]**.

### Utilisation de la ligne de commande

Pour activer la fusion CSS dans Adobe Commerce sur l’infrastructure cloud :

1. Exécutez cette commande localement :

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Validez les modifications dans le fichier `app/etc/config.php` et redéployez-le.

Pour activer la minimisation CSS dans Adobe Commerce sur l’infrastructure cloud :

1. Exécutez cette commande localement :

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Validez les modifications dans le fichier `app/etc/config.php` et redéployez-le.

## Minimiser les fichiers JS

### Utilisation de [!UICONTROL Admin]

Sur la barre latérale [!UICONTROL Admin], accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**.

### Utilisation de la ligne de commande

Pour activer la minimisation JS dans Adobe Commerce sur l’infrastructure cloud :

1. Exécutez cette commande localement :

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Validez les modifications dans le fichier `app/etc/config.php` et redéployez-le.

## Regrouper les fichiers JS

Vous pouvez activer le regroupement dans l’[!UICONTROL Admin] Commerce : **[!UICONTROL Stores]** > ***[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**.

>[!NOTE]
>
>La fusion et le regroupement ne peuvent pas être activés en même temps.

Vous pouvez également activer le groupement natif Adobe Commerce (groupement de base) à partir de la ligne de commande :

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Fusion de fichiers JS (non recommandée) {#merge-js-files}

>[!WARNING]
>
>Il est déconseillé d’activer **[!UICONTROL Merge JavaScript Files]**. Ce paramètre a été conçu uniquement pour le JavaScript chargé de manière synchrone dans la section **[!UICONTROL HEAD]** de la page. Il peut entraîner un fonctionnement incorrect de la logique de regroupement et de [!DNL RequireJS]. Il est conservé uniquement à des fins de rétrocompatibilité et ne présente aucun avantage en termes de performances lorsque le HTTP/2 est activé.
>
>Si vous avez activé **[!UICONTROL Merge JavaScript Files]** et rencontrez des problèmes, essayez de le désactiver avant d’appliquer des correctifs. Voir [ACSD-67908](../../../tools/quality-patches-tool/patches-available-in-qpt/v1-1-73/acsd-67908.md) si vous ne pouvez pas désactiver la fusion.

## Informations supplémentaires

- [Paramètres d’optimisation côté client](../../../performance/configuration.md#client-side-optimization-settings)
- [Conseils sur le regroupement](../../../performance/configuration.md#bundling-tips) dans *Bonnes pratiques de configuration* : outils de regroupement tiers, HTTP/2, et conseils sur la fusion JS et CSS obsolète
- [Guide de l’utilisateur : optimisation des fichiers de ressources](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [Guide de développement de Frontend : fusion CSS, minification et performances du site](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Groupement JavaScript avancé](../../../performance/advanced-js-bundling.md)
