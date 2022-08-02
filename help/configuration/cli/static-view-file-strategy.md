---
title: Stratégies de déploiement pour les fichiers de vue statiques
description: Découvrez les stratégies de déploiement de l’application Commerce.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# Stratégies de déploiement pour les fichiers de vue statiques

Lors du déploiement de fichiers d’affichage statiques, vous pouvez choisir l’une des trois stratégies disponibles. Chacune d’elles fournit des résultats de déploiement optimaux pour différents cas d’utilisation :

- [Standard](#standard-strategy): le processus de déploiement régulier.
- [Quick](#quick-strategy) (_default_) : réduit le temps nécessaire au déploiement des fichiers pour plusieurs paramètres régionaux.
- [Compact](#compact-strategy): réduit l’espace occupé par les fichiers d’affichage publiés.

Les sections suivantes décrivent les détails et les fonctionnalités de mise en oeuvre de chaque stratégie.

## Stratégie standard

Lorsque la stratégie Standard est utilisée, tous les fichiers d’affichage statique de tous les modules sont déployés, c’est-à-dire traités par [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

Pour plus d’informations, voir [Déploiement de fichiers d’affichage statique](../cli/static-view-file-deployment.md).

## Stratégie rapide

La stratégie rapide effectue les actions suivantes :

1. Pour chaque thème, un paramètre régional arbitraire est sélectionné et tous les fichiers de ce paramètre régional sont déployés, comme dans la stratégie standard.
1. Pour tous les autres paramètres régionaux du thème :

   1. Les fichiers qui remplacent les paramètres régionaux déployés sont définis et déployés.
   1. Tous les autres fichiers sont considérés comme similaires pour tous les paramètres régionaux et sont copiés à partir des paramètres régionaux déployés.

>[!INFO]
>
>Par _similaire_, nous entendons par fichiers indépendants des paramètres régionaux, du thème ou de la zone. Il peut s’agir de fichiers CSS, d’images et de polices.

Cette approche réduit le temps de déploiement requis pour plusieurs paramètres régionaux, bien que de nombreux fichiers soient dupliqués.

## Stratégie compacte

La stratégie compacte évite la duplication des fichiers en stockant des fichiers similaires dans `base` sous-répertoires.

Pour le résultat le plus optimisé, trois portées pour une similarité possible sont attribuées : zone, thème et paramètre régional. Le `base` les sous-répertoires sont créés pour toutes les combinaisons de ces portées.

Les fichiers sont déployés dans ces sous-répertoires selon les modèles suivants.

| Modèle | Description |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | Fichiers spécifiques à une zone, un thème et un paramètre régional spécifique |
| `<area>/<theme>/default` | Fichiers similaires pour tous les paramètres régionaux d’un thème particulier d’une zone particulière. |
| `<area>/Magento/base/<locale>` | Fichiers spécifiques à une zone et à un paramètre régional spécifiques, mais similaires pour tous les thèmes. |
| `<area>/Magento/base/default` | Fichiers spécifiques à une zone particulière, mais similaires pour tous les thèmes et paramètres régionaux. |
| `base/Magento/base/<locale>` | Fichiers similaires pour tous les domaines et thèmes, mais spécifiques à un paramètre régional spécifique. |
| `base/Magento/base/default` | Similaire à pour tous les domaines, thèmes et paramètres régionaux. |

### Mappage des fichiers déployés

L’approche de déploiement utilisée dans la stratégie compacte signifie que les fichiers sont hérités des thèmes de base et des paramètres régionaux. Ces relations d’héritage sont stockées dans les fichiers de mappage pour chaque combinaison de zone, de thème et de paramètres régionaux. Il existe des fichiers map distincts pour PHP et JS :

- `map.php`
- `requirejs-map.js`

Le `map.php` est utilisé par [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) pour créer des URL correctes.

Le `requirejs-map.js` est utilisé par la variable `baseUrlResolver` module externe pour RequireJS.

Exemple d&#39;un `map.php`:

```php?start_inline=1
return [
    'Magento_Checkout::cvv.png' => [
        'area' => 'frontend',
        'theme' => 'Magento/luma',
        'locale' => 'en_US',
    ],
    '...' => [
        'area' => '...',
        'theme' => '...',
        'locale' => '...'
    ]
];
```

Exemple d&#39;un `requirejs-map.js`:

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## Conseils pour les développeurs d’extensions

Pour créer des URL vers des fichiers d’affichage statique, utilisez [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

N’utilisez pas de concaténations d’URL pour éviter des problèmes liés à l’absence de fichiers statiques et à leur non-affichage lors du rendu de la page.
