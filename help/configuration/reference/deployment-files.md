---
title: Fichiers de configuration pour le déploiement
description: Découvrez comment les fichiers de configuration fonctionnent pour l’installation de l’application Commerce.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---


# Fichiers de configuration pour le déploiement

Adobe Commerce fournit des fichiers de configuration qui vous permettent de personnaliser facilement un composant et de créer des types de configuration pour étendre les fonctionnalités par défaut. Le processus de configuration du déploiement comprend la configuration partagée et spécifique au système pour votre installation. La configuration de déploiement de Commerce est divisée entre [`app/etc/config.php`](../reference/config-reference-configphp.md) et [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` est la valeur _shared_ fichier de configuration.
Ce fichier contient la liste des modules, thèmes et modules linguistiques installés ; et les paramètres de configuration partagés.

   Archivez ce fichier pour le contrôle de code source et utilisez-le dans vos systèmes de développement, d’évaluation et de production.

   À compter de la version 2.2, la variable `app/etc/config.php` n’est plus une entrée dans `.gitignore` fichier .
Cela a été fait pour faciliter [déploiement du pipeline](../deployment/technical-details.md).

- `app/etc/env.php` contient des paramètres spécifiques à l’environnement d’installation.

Ensemble, `config.php` et `env.php` sont appelées Commerce. _configuration du déploiement_ car les fichiers sont créés pendant l’installation et sont nécessaires pour démarrer l’application Commerce.

>[!INFO]
>
>Le [!DNL Commerce 2] la configuration de déploiement remplace `local.xml` in [!DNL Magento 1.x].

Contrairement à d’autres [fichiers de configuration de module](../reference/module-files.md), la configuration du déploiement Commerce est chargée en mémoire lors de l’initialisation. Elle n’est fusionnée avec aucun autre fichier et ne peut pas être étendue. (`config.php` et `env.php` sont fusionnés entre eux, toutefois.)

## Détails sur la configuration du déploiement

`config.php` et `env.php` sont des fichiers PHP qui renvoient une [tableau associatif multidimensionnel](https://www.w3schools.com:443/php/php_arrays.asp), qui est essentiellement une structure hiérarchique de paramètres et de valeurs de configuration.

Au niveau supérieur de ce tableau, vous trouverez _segments de configuration_. Un segment a un contenu arbitraire (une valeur scalaire ou un tableau imbriqué) distingué par une clé arbitraire, où les paires clé-valeur sont définies par la structure Commerce.

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) donne simplement accès à ces sections, mais ne vous permet pas de les étendre.

Au niveau de la hiérarchie suivante, les éléments de chaque segment sont triés en fonction de la définition de séquence de module, qui est obtenue en fusionnant les fichiers de configuration de tous les modules, à l’exception des modules désactivés.

Les sections suivantes abordent la structure et le contenu de la configuration du déploiement :

- Gestion des modules installés
- Configuration spécifique au système

## Gestion des modules installés

Le `config.php` contient une liste des modules installés. Adobe Commerce fournit des utilitaires de ligne de commande et web pour gérer les modules (installation, désinstallation, activation, désactivation ou mise à niveau).

Exemples :

- Désinstallation des composants : [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- Vérifiez l’état des composants : [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
- Activation ou désactivation de composants : [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md), [`bin/magento module:enable`](../../installation/tutorials/manage-modules.md).

> _config.php_

```php
return array (
  'modules' =>
  array (
    'Magento_Core' => 1,
    'Magento_Store' => 1,
    'Magento_Theme' => 1,
    'Magento_Authorization' => 1,
    'Magento_Directory' => 1,
    'Magento_Backend' => 1,
    'Magento_Backup' => 1,
    'Magento_Eav' => 1,
    'Magento_Customer' => 1,
...
  ),
);
```

La valeur `1` ou `0` indique si un module est activé ou désactivé.

Les modules désactivés ne sont pas reconnus par l’application Commerce ; en d’autres termes, ils ne participent pas à la configuration de fusion, à l’injection de dépendances, aux événements, aux modules externes, etc. Les modules désactivés ne modifient pas le storefront ou l’administrateur et n’affectent pas le routage.

La seule différence pratique d’un module désactivé et d’un module absent de la base de code est qu’un module désactivé est trouvé par l’outil de chargement automatique, et ses classes et constantes sont disponibles pour réutilisation dans d’autres codes.
