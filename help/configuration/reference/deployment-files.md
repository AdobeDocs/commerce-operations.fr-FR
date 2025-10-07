---
title: Fichiers de configuration pour le déploiement
description: Découvrez le fonctionnement des fichiers de configuration pour le déploiement de l’application Adobe Commerce. Découvrez les bonnes pratiques de gestion des configurations partagées et spécifiques au système.
feature: Configuration, Deploy
exl-id: 772a6814-6b18-4f8f-b31e-72faf790ff37
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Fichiers de configuration pour le déploiement

Adobe Commerce fournit des fichiers de configuration qui vous permettent de personnaliser facilement un composant et de créer des types de configuration pour étendre les fonctionnalités par défaut. Le processus de configuration du déploiement correspond à la configuration partagée et spécifique au système pour votre installation. La configuration du déploiement de Commerce est divisée entre [`app/etc/config.php`](../reference/config-reference-configphp.md) et [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` est le fichier de configuration _partagé_.
Ce fichier contient la liste des modules, thèmes et packages de langue installés, ainsi que les paramètres de configuration partagés.

  Archivez ce fichier pour le contrôle de code source et utilisez-le dans vos systèmes de développement, d’évaluation et de production.

- `app/etc/env.php` contient des paramètres spécifiques à l’environnement d’installation.

Ensemble, `config.php` et `env.php` sont appelés Commerce _configuration du déploiement_, car les fichiers sont créés lors de l’installation et sont nécessaires pour démarrer l’application Commerce.

>[!INFO]
>
>La configuration de déploiement [!DNL Commerce 2] remplace `local.xml` dans [!DNL Magento 1.x].

Contrairement aux autres [fichiers de configuration de module](../reference/module-files.md), la configuration de déploiement de Commerce est chargée en mémoire lors de l’initialisation. Elle n’est pas fusionnée avec d’autres fichiers et ne peut pas être étendue. (`config.php` et `env.php` sont toutefois fusionnés.)

## Détails sur la configuration de déploiement

`config.php` et `env.php` sont des fichiers PHP qui renvoient un [tableau associatif multidimensionnel](https://www.w3schools.com:443/php/php_arrays.asp), qui est fondamentalement une disposition hiérarchique des paramètres et valeurs de configuration.

Au niveau supérieur de ce tableau se trouvent des _segments de configuration_. Un segment comporte du contenu arbitraire (une valeur scalaire ou un tableau imbriqué), se distinguant par une clé arbitraire, où la paire clé-valeur est définie par le framework Commerce.

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) donne simplement accès à ces sections, mais ne vous permet pas de les étendre.

Au niveau de la hiérarchie suivante, les éléments de chaque segment sont triés en fonction de la définition de séquence de module, obtenue en fusionnant tous les fichiers de configuration des modules, à l’exception des modules désactivés.

Les sections suivantes décrivent la structure et le contenu de la configuration de déploiement :

- Gestion des modules installés
- Configuration spécifique au système

## Gestion des modules installés

Le fichier `config.php` contient la liste des modules installés. Adobe Commerce fournit des utilitaires de ligne de commande et web pour gérer les modules (installation, désinstallation, activation, désactivation ou mise à niveau).

Exemples :

- Désinstaller les composants : [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- Vérification du statut des composants : [`bin/magento module:status`](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/cli-reference/commerce-on-premises#modulestatus)
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

Les modules désactivés ne sont pas reconnus par l’application Commerce ; en d’autres termes, ils ne participent pas à la fusion de la configuration, à l’injection de dépendance, aux événements, aux modules externes, etc. Les modules désactivés ne modifient pas le storefront ou l’administrateur et n’affectent pas le routage.

La seule différence pratique entre un module désactivé et un module absent dans la base de code est qu&#39;un module désactivé est trouvé par le chargeur automatique, et ses classes et constantes sont disponibles pour réutilisation dans d&#39;autres codes.
