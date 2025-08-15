---
title: Exporter les paramètres de configuration
description: Exportez les paramètres de configuration Adobe Commerce dans des fichiers de configuration, également appelés image mémoire de configuration.
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Exporter les paramètres de configuration

Dans Commerce 2.2 et les versions ultérieures [modèle de déploiement de pipeline](../deployment/technical-details.md), vous pouvez gérer une configuration cohérente entre les systèmes. Une fois que vous avez configuré les paramètres dans Admin sur votre système de développement, exportez-les dans les fichiers de configuration à l’aide de la commande suivante :

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ est une liste séparée par des espaces de types de configuration à vider. Les types disponibles sont les `scopes`, les `system`, les `themes` et les `i18n`. Si aucun type de configuration n’est spécifié, la commande vide toutes les informations de configuration système.

L’exemple suivant vide uniquement les étendues et les thèmes :

```bash
bin/magento app:config:dump scopes themes
```

Suite à l’exécution de la commande, les fichiers de configuration suivants sont mis à jour :

- `app/etc/config.php`

  Il s’agit du fichier de configuration partagé pour toutes vos instances Commerce.
Incluez-le dans votre contrôle de code source afin qu’il puisse être partagé entre les systèmes de développement, de génération et de production.

  Voir [config.php référence](../reference/config-reference-configphp.md).

- `app/etc/env.php`

  Il s’agit du fichier de configuration spécifique à l’environnement.
Il contient des paramètres sensibles et spécifiques au système pour des environnements individuels.

  N&#39;incluez _ce fichier_ dans le contrôle de code source.

  Voir [référence env.php](../reference/config-reference-envphp.md).

## Paramètres sensibles ou spécifiques au système

Pour définir les paramètres sensibles écrits dans `env.php`, utilisez la commande [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values).

Les valeurs de configuration sont spécifiées comme sensibles ou spécifiques au système en référençant [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) dans le fichier [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) du module.

Pour exporter des paramètres système supplémentaires lors de l’utilisation de `config_types`, pensez à utiliser la commande [`bin/magento config:set`](set-configuration-values.md#set-values) .
