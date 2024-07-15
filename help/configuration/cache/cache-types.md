---
title: Types de cache
description: Associez les frondes du cache aux types de cache.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Types de cache

Les étapes suivantes décrivent l’association du front de cache à un type de cache.

## Étape 1 : définition d’un front de cache

L’application Commerce dispose d’un front de cache `default` que vous pouvez utiliser pour n’importe quel [type de cache](../cli/manage-cache.md#clean-and-flush-cache-types). Cette section explique comment définir éventuellement une interface de cache avec un nom différent, ce qui est préférable si vous prévoyez de personnaliser votre interface.

>[!INFO]
>
>Pour utiliser le type de cache `default`, il n&#39;est pas du tout nécessaire de modifier `env.php` ; vous modifiez le type global de Commerce `di.xml`. Voir [Options de cache de bas niveau](cache-options.md).

Vous devez spécifier une interface de cache personnalisée `app/etc/env.php` ou Commerce global `app/etc/di.xml`.

L’exemple suivant montre comment le définir dans le fichier `env.php`, qui remplace le fichier `di.xml` :

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<unique frontend id>' => [
             <cache options>
        ],
    ],
    'type' => [
         <cache type 1> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
    'type' => [
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

Où `<unique frontend id>` est un nom unique pour identifier votre front-end et `<cache options>` sont des options discutées dans les rubriques spécifiques à chaque type de mise en cache (base de données, Redis, etc.).

## Étape 2 : configurer le cache

Vous pouvez spécifier les options de configuration du cache frontal et principal dans `env.php` ou `di.xml`. Cette tâche est facultative.

Exemple `env.php` :

```php?start_inline=1
'frontend' => <frontend_type>,
'frontend_options' => [
    <frontend_option> => <frontend_option_value>,
    ...
],
'backend' => <backend_type>,
'backend_options' => [
    <backend_option> => <backend_option_value>,
    ...
],
```

where

- `<frontend_type>` est le type de cache frontal de bas niveau. Indiquez le nom d’une classe compatible avec `Zend\Cache\Core`.
Si vous omettez `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) est utilisé.

- `<frontend_option>`, `<frontend_option_value>` sont le nom et la valeur des options que la structure Commerce transmet en tant que tableau associatif au cache frontal lors de sa création.
- `<backend_type>` est le type de cache principal de bas niveau. Indiquez le nom d’une classe compatible avec `Zend_Cache_Backend` et qui implémente `Zend_Cache_Backend_Interface`.
- `<backend_option>` et `<backend_option_value>` sont le nom et la valeur des options que la structure Commerce transmet sous la forme d’un tableau associatif pour mettre en cache le serveur principal lors de sa création.

Consultez la [documentation de Laminas](https://docs.laminas.dev/) pour obtenir les informations les plus récentes sur Zend.
