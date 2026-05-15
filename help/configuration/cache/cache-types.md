---
title: Configurer les fronts du cache
description: Découvrez comment définir des fronts de cache et les associer à des types de cache dans Adobe Commerce. Découvrez la syntaxe de configuration pour env.php et di.xml.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: de613310ad701dd594a6ee8fcd973aa2c3769870
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Configurer les fronts du cache

Un cache frontal est une interface entre Commerce et le serveur principal de stockage du cache. Vous pouvez définir plusieurs fronts, chacun avec des paramètres de serveur principal différents, puis attribuer des [types de cache](../cli/manage-cache.md#clean-and-flush-cache-types) spécifiques à chaque front-end.

Cela s’avère utile lorsque vous souhaitez utiliser différents serveurs principaux de cache ou des configurations pour différents types de données mises en cache. Par exemple, vous pouvez `full_page` la mise en cache sur une base de données Redis dédiée lors de l’utilisation d’une base de données distincte pour la mise en cache `default`.

## Utiliser le serveur frontal par défaut

Commerce fournit une interface de cache `default` qui fonctionne pour tous les types de cache. Il étend [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) en implémentant le cache frontal [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php).

Dans la plupart des cas, vous n’avez pas besoin de personnaliser le serveur frontal. Il vous suffit de configurer le serveur principal. Voir [Options du serveur principal de cache](cache-options.md).

## Définition d’un fichier frontal de cache personnalisé

Les étapes suivantes expliquent comment associer un serveur frontal de cache à un type de cache.

### Étape 1 : définir un cache frontal et attribuer des types de cache

Pour définir un front-end de cache personnalisé, ajoutez la configuration à `app/etc/env.php` (qui remplace `di.xml`) :

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
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

Où :

- `<unique frontend id>` : nom unique permettant d&#39;identifier le serveur frontal (par exemple, `default`, `page_cache`, `stale_cache_enabled`)
- `<cache options>` : type de serveur principal et options de ce serveur frontal (voir [Options de cache](cache-options.md)).
- `<cache type>` : type de cache Commerce à affecter à ce serveur frontal (par exemple, `config`, `layout`, `block_html`, `full_page`)

>[!TIP]
>
>**Implémentation moderne de Symfony Cache (version 2.4.9+) :** à partir de la version 2.4.9 de Commerce, vous pouvez utiliser des types principaux simplifiés tels que `redis`, `valkey` ou `file` avec l’implémentation moderne de Symfony Cache. Voir [Utiliser Redis pour le cache par défaut](redis-pg-cache.md) et [Utiliser Valkey pour le cache par défaut](valkey-pg-cache.md) pour plus d’informations.

### Étape 2 : configurer les options frontales et principales

Vous pouvez spécifier les options de configuration du cache front-end et back-end dans `env.php` ou `di.xml`. Cette tâche est facultative. Si vous ne spécifiez pas d’options, Commerce utilise les paramètres frontaux et principaux par défaut.

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

Où :

- `<frontend_type>` : type de cache front-end de bas niveau. Spécifiez un nom de classe compatible avec `Zend\Cache\Core`.
Si cet attribut est omis, [](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) est utilisé.

- `<frontend_option>`, `<frontend_option_value>` : nom et valeur des options que le framework Commerce transmet sous forme de tableau associatif au cache front-end lors de la création.

- `<backend_type>` : type de cache du serveur principal de bas niveau. Vous pouvez spécifier les éléments suivants :
   - **Modern Symfony Cache (2.4.9+, recommandé)** : noms simplifiés tels que `redis`, `valkey` ou `file`
   - **Hérité (basé sur Zend)** : nom de classe complet compatible avec les `Zend_Cache_Backend` qui implémentent `Zend_Cache_Backend_Interface`

- `<backend_option>`, `<backend_option_value>` : le nom et la valeur des options que le framework Commerce transmet sous forme de tableau associatif au cache du serveur principal lors de la création.

>[!NOTE]
>
>**Implémentation héritée ou moderne :**
>
>- **Hérité (basé sur Zend)** : `'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis'`
>- **Moderne (cache Symfony)** : `'backend' => 'redis'` (recommandé pour Commerce 2.4.9+)
>
>L’implémentation moderne de Symfony Cache offre de meilleures performances grâce à la conformité PSR-6, la sérialisation Igbinary, la compression gzip, les scripts Lua et les connexions persistantes.

Voir la [Documentation Laminas](https://docs.laminas.dev/) pour les options basées sur Zend, ou les guides modernes de Symfony Cache pour [Redis](redis-pg-cache.md) et [Valkey](valkey-pg-cache.md).
