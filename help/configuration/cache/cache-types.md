---
title: Types de cache
description: Associez les fronts de cache aux types de cache.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Types de cache

Les étapes suivantes expliquent comment associer le serveur frontal du cache à un type de cache.

## Étape 1 : définir un cache frontal

L’application Commerce dispose d’une interface de cache `default` que vous pouvez utiliser pour n’importe quel [type de cache](../cli/manage-cache.md#clean-and-flush-cache-types). Cette section explique comment définir éventuellement un front-end de cache avec un nom différent, ce qui est préférable si vous prévoyez de personnaliser votre front-end.

>[!INFO]
>
>Pour utiliser le type de cache `default`, vous n’avez pas besoin de modifier le `env.php` ; vous modifiez les `di.xml` globaux de Commerce. Voir [Options de cache de bas niveau](cache-options.md).

Vous devez spécifier un `app/etc/env.php` global de cache personnalisé `app/etc/di.xml` ou Commerce.

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

Où `<unique frontend id>` est un nom unique permettant d’identifier votre serveur frontal et `<cache options>` sont des options abordées dans les rubriques spécifiques à chaque type de mise en cache (base de données, Redis, etc.).

## Étape 2 : configurer le cache

Vous pouvez spécifier les options de configuration du cache front-end et back-end dans `env.php` ou `di.xml`. Cette tâche est facultative.

`env.php` exemple :

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

où

- `<frontend_type>` est le type de cache front-end de bas niveau. Spécifiez le nom d’une classe compatible avec `Zend\Cache\Core`.
Si vous omettez `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) est utilisé.

- `<frontend_option>`, `<frontend_option_value>` sont le nom et la valeur des options que le framework Commerce transmet en tant que tableau associatif au cache front-end lors de sa création.
- `<backend_type>` est le type de cache du serveur principal de bas niveau. Spécifiez le nom d’une classe compatible avec `Zend_Cache_Backend` et implémentant `Zend_Cache_Backend_Interface`.
- `<backend_option>` et `<backend_option_value>` sont le nom et la valeur des options que le framework Commerce transmet en tant que tableau associatif au cache principal lors de sa création.

Voir la [Documentation Laminas](https://docs.laminas.dev/) pour obtenir les dernières informations sur Zend.
