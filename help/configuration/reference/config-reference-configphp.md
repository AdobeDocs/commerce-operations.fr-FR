---
title: Référence config.php
description: Voir une liste de valeurs dans le fichier config.php.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Référence config.php

Le `config.php` contient les sections suivantes :

| Nom | Description |
| --------- | -------------------|
| `i18n` | Toutes les données de traduction intégrées. La lecture de cette section n’est pas prise en charge. |
| `modules` | La liste des modules activés et désactivés. |
| `scopes` | Liste des magasins, des groupes de magasins et des sites web contenant des informations connexes. |
| `system` | Configurations système requises pour le déploiement de contenu statique. |
| `themes` | Configuration des thèmes installés. |

## modules

Contient un tableau de modules et leurs états. Si le module est activé, la valeur est 1. Sinon, la valeur est 0.

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

En savoir plus sur [Modules].

## portées

Contient un tableau de valeurs de configuration de portée. Il contient les sous-noeuds suivants :

| Nom | Description |
| ---------- | -----------------------------------|
| `websites` | Configuration du site web |
| `groups` | Configuration des magasins |
| `stores` | Configuration des vues du magasin |

```conf
'scopes' => [
  'websites' => [
    'admin' => [
      'website_id' => '0',
      'code' => 'admin',
      'name' => 'Admin',
      'sort_order' => '0',
      'default_group_id' => '0',
      'is_default' => '0'
    ]
  ],
  'groups' => [
    0 => [
      'group_id' => '0',
      'website_id' => '0',
      'code' => 'default',
      'name' => 'Default',
      'root_category_id' => '0',
      'default_store_id' => '0'
    ]
  ],
  'stores' => [
    'admin' => [
      'store_id' => '0',
      'code' => 'admin',
      'website_id' => '0',
      'group_id' => '0',
      'name' => 'Admin',
      'sort_order' => '0',
      'is_active' => '1'
    ]
  ]
]
```

En savoir plus sur [Portées de commerce][scopes].

## system

Contient un tableau de valeurs de configuration des champs système.

```conf
'system'=> [
    'default' =>[
        'checkout' => [
            'cart' => [
                'delete_quote_after' => 31
            ]
        ]
    ]
]
```

En savoir plus sur [Configurations spécifiques au système](config-reference-sens.md).

## thèmes

Contient un tableau de valeurs pour la configuration du thème.

```conf
'themes' => [
  'frontend/Magento/luma' => [
    'parent_id' => 'Magento/blank',
    'theme_path' => 'Magento/luma',
    'theme_title' => 'Magento Luma',
    'is_featured' => '0',
    'area' => 'frontend',
    'type' => '0',
    'code' => 'Magento/luma'
  ]
]
```

En savoir plus sur [Thèmes].

<!-- link definitions -->

[Modules]: https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html
[scopes]: https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings
[Thèmes]: https://developer.adobe.com/commerce/frontend-core/guide/themes/create-storefront/
