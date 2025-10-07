---
title: Stratégies de déploiement pour les fichiers de vue statiques
description: Découvrez les stratégies de déploiement des fichiers de vue statiques dans les applications Adobe Commerce. Découvrez des méthodes de déploiement optimales pour différents cas d’utilisation.
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Stratégies de déploiement pour les fichiers de vue statiques

Lors du déploiement de fichiers de vue statique, vous pouvez choisir l’une des trois stratégies disponibles. Chacune d’elles fournit des résultats de déploiement optimaux pour différents cas d’utilisation :

- [Standard](#standard-strategy) : processus de déploiement standard.
- [Rapide](#quick-strategy) (_par défaut_) : réduit le temps nécessaire au déploiement lorsque des fichiers de plusieurs paramètres régionaux sont déployés.
- [Compact](#compact-strategy) : permet de réduire l’espace occupé par les fichiers de vue publiés.

Les sections suivantes décrivent les détails et les fonctionnalités de mise en œuvre de chaque stratégie.

## Stratégie standard

Lorsque la stratégie Standard est utilisée, tous les fichiers de vue statiques de tous les packages sont déployés, c’est-à-dire traités par [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

Pour plus d’informations, voir [Déployer des fichiers de vue statiques](../cli/static-view-file-deployment.md).

## Stratégie rapide

La stratégie rapide effectue les actions suivantes :

1. Pour chaque thème, un paramètre régional arbitraire est choisi et tous les fichiers pour ce paramètre régional sont déployés, comme dans la stratégie standard.
1. Pour tous les autres paramètres régionaux du thème :

   1. Les fichiers qui remplacent les paramètres régionaux déployés sont définis et déployés.
   1. Tous les autres fichiers sont considérés comme similaires pour tous les paramètres régionaux et sont copiés à partir du paramètre régional déployé.

>[!INFO]
>
>Par _similaire_, nous entendons des fichiers indépendants du paramètre régional, du thème ou de la zone. Ces fichiers peuvent inclure des fichiers CSS, des images et des polices.

Cette approche réduit le temps de déploiement requis pour plusieurs paramètres régionaux, bien que de nombreux fichiers soient dupliqués.

## Stratégie compacte

La stratégie compacte évite la duplication des fichiers en stockant des fichiers similaires dans des sous-répertoires `base`.

Pour le résultat le plus optimisé, trois portées pour les similitudes possibles sont attribuées : zone, thème et paramètre régional. Les sous-répertoires `base` sont créés pour toutes les combinaisons de ces étendues.

Les fichiers sont déployés dans ces sous-répertoires selon les modèles suivants.

| Modèle | Description |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | Fichiers spécifiques à une zone, un thème et des paramètres régionaux spécifiques |
| `<area>/<theme>/default` | Fichiers similaires pour tous les paramètres régionaux d’un thème spécifique d’une zone particulière. |
| `<area>/Magento/base/<locale>` | Fichiers spécifiques à une zone et à des paramètres régionaux spécifiques, mais similaires pour tous les thèmes. |
| `<area>/Magento/base/default` | Fichiers spécifiques à une zone particulière, mais similaires pour tous les thèmes et paramètres régionaux. |
| `base/Magento/base/<locale>` | Fichiers similaires pour toutes les zones et tous les thèmes, mais spécifiques à un paramètre régional particulier. |
| `base/Magento/base/default` | Similaire pour toutes les zones, thèmes et paramètres régionaux. |

### Mappage des fichiers déployés

L’approche du déploiement utilisée dans la stratégie compacte signifie que les fichiers sont hérités des thèmes de base et des paramètres régionaux. Ces relations d’héritage sont stockées dans les fichiers de mappage pour chaque combinaison de zone, de thème et de paramètre régional. Il existe des fichiers de mappage distincts pour PHP et JS :

- `map.php`
- `requirejs-map.js`

Le fichier `map.php` est utilisé par [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) pour créer des URL correctes.

Le `requirejs-map.js` est utilisé par le plug-in `baseUrlResolver` pour RequireJS.

Exemple de `map.php` :

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

Exemple de `requirejs-map.js` :

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

Pour créer des URL dans des fichiers d’affichage statiques, utilisez [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

N’utilisez pas de concaténations d’URL pour éviter tout problème en raison duquel les fichiers statiques sont introuvables et ne s’affichent pas lors du rendu de la page.
