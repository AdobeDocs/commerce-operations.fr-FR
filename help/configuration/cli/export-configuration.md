---
title: Exportation des paramètres de configuration
description: Exportez les paramètres de configuration Adobe Commerce vers les fichiers de configuration, également appelés fichier de sauvegarde de configuration.
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Exportation des paramètres de configuration

Dans Commerce 2.2 et versions ultérieures [modèle de déploiement de pipeline](../deployment/technical-details.md), vous pouvez conserver une configuration cohérente sur tous les systèmes. Après avoir configuré les paramètres dans l’administrateur de votre système de développement, exportez ces paramètres vers les fichiers de configuration à l’aide de la commande suivante :

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ est une liste de types de configuration à vider séparés par des espaces. Les types disponibles incluent : `scopes`, `system`, `themes`, et `i18n`. Si aucun type de configuration n’est spécifié, la commande vide toutes les informations de configuration du système.

L’exemple suivant illustre uniquement les portées et les thèmes :

```bash
bin/magento app:config:dump scopes themes
```

Suite à l&#39;exécution de la commande, les fichiers de configuration suivants sont mis à jour :

- `app/etc/config.php`

  Il s’agit du fichier de configuration partagé pour toutes vos instances Commerce.
Incluez-le dans votre contrôle de code source afin qu’il puisse être partagé entre les systèmes de développement, de génération et de production.

  Voir [Référence config.php](../reference/config-reference-configphp.md).

- `app/etc/env.php`

  Il s’agit du fichier de configuration spécifique à l’environnement.
Il contient des paramètres sensibles et spécifiques au système pour des environnements individuels.

  Do _not_ inclure ce fichier dans le contrôle de code source.

  Voir [référence env.php](../reference/config-reference-envphp.md).

## Paramètres sensibles ou spécifiques au système

Pour définir les paramètres sensibles écrits sur `env.php`, utilisez le [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) .

Les valeurs de configuration sont spécifiées comme sensibles ou spécifiques au système en référençant [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) dans le de [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) fichier .

Pour exporter des paramètres système supplémentaires lors de l’utilisation de `config_types`, pensez à utiliser la variable [`bin/magento config:set`](set-configuration-values.md#set-values) .
