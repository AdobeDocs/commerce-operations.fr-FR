---
title: config.php référence
description: Découvrez les valeurs du fichier config.php et les sections pour la configuration d’Adobe Commerce. Découvrez les modules, les portées, les paramètres système et les bonnes pratiques de déploiement.
exl-id: 9b355d6d-ea66-480b-ad96-0ea9e7e61844
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 1%

---

# config.php référence

Le fichier `config.php` contient les sections suivantes :

| Nom | Description |
| --------- | -------------------|
| `i18n` | Toutes les données de traduction intégrées. La lecture de cette section n’est pas prise en charge. |
| `modules` | La liste des modules activés et désactivés. |
| `scopes` | Liste de magasins, de groupes de magasins et de sites web avec des informations connexes. |
| `system` | Les configurations système requises pour le déploiement de contenu statique. |
| `themes` | La configuration des thèmes installés. |

## modules

Contient un tableau de modules et leurs états. Si le module est activé, la valeur est 1. Dans le cas contraire, la valeur est 0.

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

En savoir plus sur les [modules].

## portées

Contient un tableau de valeurs de configuration de l’étendue. Il comporte les sous-nœuds suivants :

| Nom | Description |
| ---------- | -----------------------------------|
| `websites` | Configuration du site web |
| `groups` | Stocke la configuration |
| `stores` | Configuration des vues de magasin |

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

En savoir plus sur les [étendues de Commerce][scopes].

## système

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

En savoir plus sur les [&#x200B; configurations spécifiques au système &#x200B;](config-reference-sens.md).

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

En savoir plus sur les [thèmes].

<!-- link definitions -->

[Modules]: https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html
[scopes]: https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings
[Thèmes]: https://developer.adobe.com/commerce/frontend-core/guide/themes/create-storefront/
