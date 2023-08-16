---
title: Avancé [!DNL JavaScript] Regroupement
description: Découvrez comment le bundling JavaScript peut réduire la taille et la fréquence des requêtes de serveur.
exl-id: 81a313f8-e541-4da6-801b-8bbd892d6252
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2137'
ht-degree: 0%

---

# Avancé [!DNL JavaScript] bundling

Regroupement [!DNL JavaScript] Les modules pour de meilleures performances consistent à réduire deux éléments :

1. Nombre de requêtes de serveur.
1. Taille de ces requêtes de serveur.

Dans une application modulaire, le nombre de requêtes de serveur peut atteindre des centaines. Par exemple, la capture d’écran suivante affiche uniquement le début de la liste de [!DNL JavaScript] modules chargés sur la page d’accueil d’une installation propre.

![Pas de regroupement](../assets/performance/images/noBundling.png)

## Fusion et regroupement

Prêt à l’emploi, [!DNL Commerce] propose deux manières de réduire le nombre de requêtes de serveur : la fusion et le regroupement. Ces paramètres sont désactivés par défaut. Vous pouvez les activer dans l’interface utilisateur d’administration de **[!UICONTROL Stores]** > **Paramètres** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL [!DNL JavaScript] Settings]** ou à partir de la ligne de commande.

![Regroupement](../assets/performance/images/bundlingImage.png)

### Lots de base

Pour activer le regroupement intégré à partir de la ligne de commande :

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

Il s’agit d’un [!DNL Commerce] mécanisme qui combine toutes les ressources présentes dans le système et les distribue parmi des lots de même taille (bundle_0.js, bundle_1.js ... bundle_x.js) :

![[!DNL Commerce] bundling](../assets/performance/images/magentoBundling.png)

Mieux encore, mais le navigateur charge TOUTES les [!DNL JavaScript] des lots, pas seulement ceux dont ils ont besoin.

[!DNL Commerce] Le regroupement réduit le nombre de connexions par page, mais pour chaque requête de page, il charge tous les lots, même si la page demandée peut uniquement dépendre de fichiers dans un ou deux des lots. Les performances s’améliorent une fois que le navigateur a mis les lots en cache. Cependant, comme le navigateur charge ces lots de manière synchrone, la première visite de l’utilisateur lors d’une [!DNL Commerce] storefront peut prendre un certain temps pour effectuer le rendu et nuire à l’expérience de l’utilisateur.

### Fusion de base

Pour activer la fusion intégrée à partir de la ligne de commande :

```bash
php -f bin/magento config:set dev/js/merge_files 1
```

Cette commande fusionne tous les éléments synchrones [!DNL JavaScript] dans un fichier. L’activation de la fusion sans activer le regroupement n’est pas utile, car [!DNL Commerce] utilise RequireJS. Si vous n’activez pas le regroupement, [!DNL Commerce] fusionne uniquement RequireJS et sa configuration. Lorsque vous activez le regroupement et la fusion, [!DNL Commerce] crée une seule [!DNL JavaScript] fichier :

![Fusion dans le monde réel](../assets/performance/images/magentoMergingDevWorld.png)

## Temps de rendu dans le monde réel

Les temps de chargement précédent, regroupés et fusionnés, s’affichent parfaitement dans un environnement de développement. Mais dans le monde réel, beaucoup de choses peuvent ralentir le rendu : connexions lentes, seuils de connexions élevés, réseaux limités. En outre, les périphériques mobiles ne sont pas restitués aussi rapidement que les ordinateurs de bureau.

Pour tester et préparer votre déploiement storefront pour le monde réel, nous vous recommandons de tester avec le profil de ralentissement natif de Chrome &quot;Lent 3G&quot;. Avec la 3G lente, nos heures de sortie groupées précédentes reflètent désormais les réalités de connexion de nombreux utilisateurs :

![Regroupement dans le monde réel](../assets/performance/images/magentoBundlingRealWorld.png)

Pour une connectivité 3G lente, le chargement de tous les lots prend environ 44 secondes pour la page d’accueil d’une page propre. [!DNL Commerce] installation.

Il en va de même lors de la fusion des lots dans un seul fichier. Les utilisateurs pouvaient encore attendre environ 42 secondes le chargement initial de la page, comme illustré ici :

![Fusion dans le monde réel](../assets/performance/images/magentoMergingRealWorld.png)

Avec une approche plus avancée de [!DNL JavaScript] Nous pouvons améliorer ces temps de chargement.

## Lots avancés

N’oubliez pas que l’objectif de [!DNL JavaScript] Le regroupement permet de réduire le nombre et la taille des ressources demandées pour chaque page chargée dans le navigateur. Pour ce faire, nous voulons créer nos lots afin que chaque page de notre magasin n’ait besoin que de télécharger un lot commun et un lot spécifique à chaque page consultée.

Pour ce faire, définissez vos lots par types de page. Vous pouvez classer les [!DNL Commerce]Pages de dans plusieurs types de page, y compris Catégorie, Produit, CMS, Client, Panier et Passage en caisse. Chaque page classée dans l’un de ces types de page comporte un ensemble différent de dépendances du module RequireJS. Lorsque vous groupez vos modules RequireJS par type de page, vous obtenez uniquement une poignée de lots qui couvrent les dépendances de n’importe quelle page de votre magasin.

Par exemple, vous pouvez obtenir un lot pour les dépendances communes à toutes les pages, un lot pour les pages CMS uniquement, un lot pour les pages Catalogue uniquement, un autre lot pour les pages Recherche seule et un lot pour les pages Passage en caisse.

Vous pouvez également créer des lots par objectif : pour les fonctionnalités courantes, les fonctionnalités liées aux produits, les fonctionnalités d’expédition, les fonctionnalités de passage en caisse, les taxes et les validations de formulaire. La définition de vos lots dépend de vous et de la structure de votre magasin. Il se peut que certaines stratégies de regroupement fonctionnent mieux que d’autres.

Un nettoyage [!DNL Commerce] L’installation permet d’atteindre des performances suffisantes en divisant les lots par types de page, mais certaines personnalisations peuvent nécessiter une analyse plus approfondie et d’autres distributions de ressources.

### Outils requis

Les étapes suivantes nécessitent l’installation des outils suivants et une bonne connaissance de ces outils :

- [nodejs](https://nodejs.org/en/download/)
- [r.js](http://requirejs.org/docs/optimization.html#download)
- [[!DNL PhantomJS]](https://phantomjs.org/) (facultatif)

### Exemple de code

Des versions complètes de l’exemple de code utilisé dans cet article sont disponibles ici :

- [build.js](../assets/performance/code-samples/build.js)
- [deps.js](../assets/performance/code-samples/deps.js)
- [deps-map.sh](../assets/performance/code-samples/deps-map.sh.txt)

### Partie 1 : Création d’une configuration de regroupement

#### 1\. Ajout d’un fichier build.js

Créez un `build.js` dans le fichier [!DNL Commerce] répertoire racine. Ce fichier contiendra la configuration complète de la version pour vos lots.

```javascript
({
    optimize: 'none',
    inlineText: true
})
```

Plus tard, nous changerons la variable `optimize:` de_ `none` to `uglify2` pour réduire la sortie du lot. Mais pour l&#39;instant, pendant le développement, vous pouvez le laisser défini sur `none` pour garantir des versions plus rapides.

#### 2\. Ajout de dépendances RequireJS, de schémas, de chemins et de mappages

Ajoutez les noeuds de configuration de version RequireJS suivants, `deps`, `shim`, `paths`, et `map`, dans votre fichier de version :

```javascript
({
    optimize: 'none',
    inlineText: true,

    deps: [],
    shim: {},
    paths: {},
    map: { "*": {} },
})
```

#### 3\. Agrégez les valeurs d’instance requirejs-config.js .

Au cours de cette étape, vous devrez regrouper tous les `deps`, `shim`, `paths`, et `map` noeuds de configuration de votre magasin `requirejs-config.js` dans les noeuds correspondants de votre `build.js` fichier . Pour ce faire, vous pouvez ouvrir le **[!UICONTROL Network]** dans le panneau Outils de développement de votre navigateur et accédez à n’importe quelle page de votre magasin, telle que la page d’accueil. Dans l’onglet Réseau, l’instance de la boutique du `requirejs-config.js` fichier situé près du haut, en surbrillance ici :

![Configuration RequireJS](../assets/performance/images/RequireJSConfig.png)

Ce fichier contient plusieurs entrées pour chacun des noeuds de configuration (`deps`, `shim`, `paths`, `map`). Vous devez regrouper ces valeurs de noeud multiples dans le noeud de configuration unique de votre fichier build.js. Par exemple, si la variable `requirejs-config.js` instance comporte des entrées pour 15 entrées distinctes `map` , vous devez fusionner les entrées des 15 noeuds en une seule `map` dans votre `build.js` fichier . Il en sera de même pour la variable `deps`, `shim`, et `paths` noeuds. Sans un script pour automatiser ce processus, cela peut prendre du temps.

Vous devez modifier le chemin. `mage/requirejs/text` to `requirejs/text` in `paths` noeud de configuration comme suit :

```javascript
({
    //...
    paths: {
        //...
        "text": "requirejs/text"
    },
})
```

#### 4\. Ajouter un noeud de modules

À la fin du `build.js` , ajouter les modules[] comme espace réservé pour les lots que vous définirez ultérieurement pour votre storefront.

```javascript
({
    optimize: 'none',
    inlineText: true,

    deps: [],
    shim: {},
    paths: {},
    map: { "*": {} },

    modules: [],
})
```

#### 5\. Récupération des dépendances RequireJS

Vous pouvez récupérer tous les [!DNL RequireJS] dépendances des modules des types de page de votre magasin en utilisant :

1. [!DNL PhantomJS] à partir de la ligne de commande (en supposant que [!DNL PhantomJS] installé).
1. RequireJS dans la console de votre navigateur.

#### Pour utiliser [!DNL PhantomJS]:

Dans le [!DNL Commerce] répertoire racine, créez un fichier appelé `deps.js` et copiez dans le code ci-dessous. Ce code utilise [!DNL [!DNL PhantomJS]] pour ouvrir une page et attendre que le navigateur charge toutes les ressources de page. Il génère ensuite tous les [!DNL RequireJS] dépendances d’une page donnée.

```javascript
"use strict";
var page = require('webpage').create(),
    system = require('system'),
    address;

if (system.args.length === 1) {
    console.log('Usage: $phantomjs deps.js url');
    phantom.exit(1);
} else {
    address = system.args[1];
    page.open(address, function (status) {
        if (status !== 'success') {
            console.log('FAIL to load the address');
        } else {
            setTimeout(function () {
                console.log(page.evaluate(function () {
                    return Object.keys(window.require.s.contexts._.defined);
                }));
                phantom.exit();
            }, 5000);
        }
    });
}
```

Ouvrez un terminal à l’intérieur de la fonction [!DNL Commerce] répertoire racine et exécutez le script sur chaque page de votre magasin qui représente un type de page spécifique :

<pre>
phantomjs deps.js <i>url-to-specific-page</i> &gt; <i>text-file-presents-pagetype-dependencies</i>
</pre>

Par exemple, voici quatre pages de l’exemple de magasin à thème Luma qui représentent les quatre types de pages que nous utiliserons pour créer nos quatre lots (page d’accueil, catégorie, produit, panier) :

```terminal
phantomjs deps.js http://m2.loc/ > bundle/homepage.txt
phantomjs deps.js http://m2.loc/women/tops-women/jackets-women.html > bundle/category.txt
phantomjs deps.js http://m2.loc/beaumont-summit-kit.html > bundle/product.txt
phantomjs deps.js http://m2.loc/checkout/cart/?SID=m2tjdt7ipvep9g0h8pmsgie975 > bundle/cart.txt (prepare a shopping cart)
..............
```

#### Pour utiliser la console du navigateur :

Si vous ne souhaitez pas utiliser [!DNL PhantomJS], vous pouvez exécuter la commande suivante à partir de la console de votre navigateur lors de l’affichage de chaque type de page dans votre storefront :

```shell
Object.keys(window.require.s.contexts._.defined)
```

Cette commande (utilisée dans la variable [!DNL PhantomJS] (script) crée la même liste de [!DNL RequireJS] et les affiche dans la console du navigateur. L’inconvénient de cette approche est que vous devrez créer vos propres fichiers texte de type lot/page.

#### 6\. Mise en forme et filtrage de la sortie

Après avoir fusionné la variable [!DNL RequireJS] dépendances dans les fichiers texte de type page, vous pouvez utiliser la commande suivante sur chaque fichier de dépendance de type page pour remplacer les virgules de vos fichiers par des lignes supplémentaires :

```terminal
sed -i -e $'s/,/\\\n/g' bundle/category.txt
sed -i -e $'s/,/\\\n/g' bundle/homepage.txt
sed -i -e $'s/,/\\\n/g' bundle/product.txt
....
```

Vous devez également supprimer tous les mixins de chaque fichier, car les mixins dupliquent les dépendances. Utilisez la commande suivante sur chaque fichier de dépendance :

```terminal
sed -i -e 's/mixins\!.*$//g' bundle/homepage.txt
sed -i -e 's/mixins\!.*$//g' bundle/category.txt
sed -i -e 's/mixins\!.*$//g' bundle/product.txt
...
```

#### 7\. Identification des lots uniques et communs

L’objectif est de créer un lot commun de [!DNL JavaScript] fichiers requis par toutes les pages. Ainsi, le navigateur ne doit charger que le lot commun avec un ou plusieurs types de page spécifiques.

Ouvrez un terminal dans le [!DNL Commerce] Répertoire racine et utilisez la commande suivante pour vérifier que vous disposez de dépendances que vous pouvez diviser en lots distincts :

```bash
sort bundle/*.txt |uniq -c |sort -n
```

Cette commande fusionne et trie les dépendances trouvées dans la variable `bundle/*.txt` fichiers .  La sortie indique également le nombre de fichiers contenant chaque dépendance :

```terminal
1 buildTools,
1 jquery/jquery.parsequery,
1 jsbuild,
2 jquery/jquery.metadata,
2 jquery/validate,
2 mage/bootstrap,
3 jquery
3 jquery/ui
3 knockoutjs/knockout
...
```

Ce résultat indique que : `buildTools` est une dépendance dans un seul des fichiers bundle/*.txt . La variable `jquery/jquery.metadata` La dépendance se trouve dans deux (2) fichiers et `es6-collections` se trouve dans trois (3) fichiers.

Notre sortie n’affiche que trois types de page (page d’accueil, catégorie et produit), ce qui nous indique :

- Trois dépendances sont propres à un seul type de page (indiqué par le nombre 1).
- Trois autres dépendances se produisent sur deux types de page (indiqué par le nombre 2).
- Les trois dernières dépendances sont communes aux trois types de pages (illustrées par le nombre 3).

Cela nous indique que nous pouvons probablement améliorer la vitesse de chargement des pages de notre magasin en divisant nos dépendances en différents lots, une fois que nous savons quels types de page ont besoin de quelles dépendances.

#### 8\. Créer un fichier de distribution des dépendances

Pour identifier les types de page qui nécessitent les dépendances, créez un fichier dans le [!DNL Commerce] Répertoire racine appelé `deps-map.sh` et copiez dans le code ci-dessous :

```shell
awk 'END {
 for (R in rec) {
   n = split(rec[R], t, "/")
   if (n > 1)
     dup[n] = dup[n] ? dup[n] RS sprintf("\t%-20s -->\t%s", rec[R], R) : \
       sprintf("\t%-20s -->\t%s", rec[R], R)
   }
 for (D in dup) {
   printf "records found in %d files:\n\n", D
   printf "%s\n\n", dup[D]
   }
 }
{
 rec[$0] = rec[$0] ? rec[$0] "/" FILENAME : FILENAME
}' bundle/*.txt
```

Vous pouvez également trouver le script à l’adresse [https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html](https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html)

Ouvrez un terminal dans le [!DNL Commerce] répertoire racine et exécutez le fichier :

```bash
bash deps-map.sh
```

La sortie de ce script, appliquée à nos trois exemples de types de page, doit ressembler à ceci (mais beaucoup plus longtemps) :

```terminal
bundle/product.txt   -->   buildTools,
bundle/category.txt  -->   jquery/jquery.parsequery,
bundle/product.txt   -->   jsbuild,

bundle/category.txt/bundle/homepage.txt -->    jquery/jquery.metadata,
bundle/category.txt/bundle/homepage.txt -->    jquery/validate,
bundle/category.txt/bundle/homepage.txt -->    mage/bootstrap,

bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> jquery,
bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> jquery/ui,
bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> knockoutjs/knockout,
```

Il s’agit d’informations suffisantes pour créer une configuration de lots.

#### 9\. Création de lots dans le fichier build.js

Ouvrez le `build.js` fichier de configuration et ajoutez vos lots à la `modules` noeud . Chaque lot doit définir les propriétés suivantes :

- `name`— le nom du lot. Par exemple, un nom de `bundles/cart` génère une `cart.js` dans un `bundles` sous-répertoire .

- `create`— un indicateur booléen pour créer le lot (valeurs : `true` ou `false`).

- `include`— un tableau de ressources (chaînes) inclus en tant que dépendances pour la page. RequireJS trace toutes les dépendances et les inclut dans le lot, sauf si exclu.

- `exclude`— un tableau de lots ou de ressources à exclure du lot.

```javascript
{
    name: 'bundles/catalog',
    create: true,
    include: [
        'addToWishlist',
        'priceBundle',
        'priceUtils',
        'priceOptions',
        'sticky',
        'productSummary',
        'slide'
    ],
    exclude: [
        'requirejs/require',
        'bundles/default',
        'mage/bootstrap'
    ],
}
```

Cet exemple réutilise `mage/bootstrap` et `requirejs/require` ressources, en accordant une priorité plus élevée à leurs composants et composants les plus importants qui doivent être chargés de manière synchrone. Les lots présents sont les suivants :

- `requirejs/require`: seul lot chargé de manière synchrone
- `mage/bootstrap`: lot d’amorçage avec composants de l’interface utilisateur
- `bundles/default`: lot par défaut requis pour toutes les pages
- `bundles/cart`: lot requis pour la page de panier
- `bundles/shipping`: lot courant pour le panier et la page de passage en caisse (en supposant que le passage en caisse ne soit jamais ouvert directement, la page de passage en caisse se charge encore plus rapidement si la page de panier a été ouverte précédemment et que le lot d’expédition a déjà été chargé)
- `bundles/checkout`: tout pour le passage en caisse
- `bundles/catalog`: tout pour les pages de produits et de catégories

### Partie 2 : Génération de lots

Les étapes ci-dessous décrivent le processus de base pour générer plus efficacement [!DNL Commerce] des lots. Vous pouvez automatiser ce processus comme vous le souhaitez, mais vous devrez tout de même utiliser `nodejs` et `r.js` pour générer vos lots. Et si vos thèmes ont [!DNL JavaScript]personnalisations liées et ne peuvent pas réutiliser les mêmes `build.js` , vous devrez peut-être créer plusieurs `build.js` configurations par thème.

#### 1. Génération de sites de magasin statiques

Avant de générer des lots, exécutez la commande de déploiement statique :

```bash
php -f bin/magento setup:static-content:deploy -f -a frontend
```

Cette commande génère des déploiements de magasin statiques pour chaque thème et paramètre régional que vous avez configuré. Par exemple, si vous utilisez le thème Luma et un thème personnalisé avec des paramètres régionaux en anglais et en français, vous générez quatre déploiements statiques :

- ...luma/fr_FR
- ...luma/fr_FR
- ...custom/en_US
- ...custom/fr_FR

Pour générer des lots pour tous les thèmes et paramètres régionaux de magasin, répétez les étapes ci-dessous pour chaque thème et paramètre régional de magasin.

#### 2. Déplacez le contenu statique du magasin vers un répertoire temporaire.

Tout d’abord, vous devez déplacer le contenu statique du répertoire cible vers un répertoire temporaire, car RequireJS remplace tout le contenu du répertoire cible.

```bash
mv pub/static/frontend/Magento/{theme}/{locale} pub/static/frontend/Magento/{theme}/{locale}_tmp
```

Par exemple :

```bash
mv pub/static/frontend/Magento/luma/en_US pub/static/frontend/Magento/luma/en_US_tmp
```

#### 3. Exécutez l’optimiseur r.js

Exécutez ensuite l’optimiseur r.js sur la page `build.js` fichier à partir de [!DNL Commerce]Répertoire racine de . Les chemins d’accès à tous les répertoires et fichiers sont relatifs au répertoire de travail.

```bash
r.js -o build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Cette commande génère des lots dans une `bundles` sous-répertoire du répertoire cible, qui dans ce cas entraîne `pub/static/frontend/Magento/luma/en_US/bundles`.

La liste du contenu du nouveau répertoire de bundle peut se présenter comme suit :

```bash
ll pub/static/frontend/Magento/luma/en_US/bundles
```

```terminal
total 1900
drwxr-xr-x  2 root root    4096 Mar 28 11:24 ./
drwxr-xr-x 70 root root    4096 Mar 28 11:24 ../
-rw-r--r--  1 root root  116417 Mar 28 11:24 cart.js
-rw-r--r--  1 root root  187090 Mar 28 11:24 catalog.js
-rw-r--r--  1 root root  307619 Mar 28 11:24 checkout.js
-rw-r--r--  1 root root 1240608 Mar 28 11:24 default.js
-rw-r--r--  1 root root   74233 Mar 28 11:24 shipping.js
```

#### 4. Configuration de RequireJS pour utiliser des lots

Pour obtenir que RequireJS utilise vos lots, ajoutez une `onModuleBundleComplete` rappel après l’événement `modules` dans le noeud `build.js` fichier :

```javascript
[
    {
       //...
       exclude: [
           'requirejs/require',
           'bundles/default',
           'bundles/checkout',
           'bundles/cart',
           'bundles/shipping',
           'mage/bootstrap'
       ],
   },
],
bundlesConfigOutFile: `${config.dir}/requirejs-config.js`,
onModuleBundleComplete: function(data) {
    if (this.bundleConfigAppended) {
        return;
    }
    this.bundleConfigAppended = true;

    // bundlesConfigOutFile requires a simple require.config call in order to modify the configuration
    const bundleConfigPlaceholder = `
(function (require) {
require.config({});
})(require);
    `;

    fs.appendFileSync(this.bundlesConfigOutFile, bundleConfigPlaceholder);
}
```

#### 5. Réexécuter la commande de déploiement

Exécutez la commande suivante à déployer :

```bash
r.js -o app/design/frontend/Magento/luma/build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Ouvrir `requirejs-config.js` dans le `pub/static/frontend/Magento/luma/en_US` pour vérifier que RequireJS a ajouté le fichier avec les appels de configuration de regroupement :

```javascript
require.config({
    bundles: {
        "bundles/default": ["mage/template", "mage/apply/scripts", "mage/apply/main", "mage/mage", "mage/translate", "mage/loader"],
        "bundles/cart": ["Magento_Ui/js/lib/validation/utils", "Magento_Ui/js/lib/validation/rules", "Magento_Ui/js/lib/validation/validation"]
    }
}
```

>[!NOTE]
>
>Lors de la configuration des lots, veillez à placer la variable `requirejs.config()` les appels dans l’ordre dans lequel vous souhaitez les exécuter, car les appels sont exécutés dans l’ordre dans lequel ils apparaissent.

#### 6. Tester les résultats

Une fois la page chargée, le navigateur charge différents lots et dépendances. Par exemple, voici les résultats du profil &quot;3G lent&quot; :

![Deux fois plus rapide](../assets/performance/images/TwiceAsFast.png)

Le temps de chargement d’une page d’accueil vide est désormais deux fois plus rapide que l’utilisation d’une page native [!DNL Commerce] regroupement. Mais nous pouvons faire encore mieux.

#### 7. Optimisation des lots

Même en cas de gzip, la variable [!DNL JavaScript] Les fichiers sont toujours volumineux. Minifiez-les avec RequireJS, qui utilise uglifier pour la minification [!DNL JavaScript] à un bon résultat.

Pour activer l’optimiseur dans votre `build.js` fichier, ajouter `uglify2` comme valeur de la propriété optimize située en haut de l’objet `build.js` fichier :

```javascript
({
    optimize: 'uglify2',
    inlineText: true
})
```

Les résultats peuvent être significatifs :
![Trois fois plus rapide](../assets/performance/images/ThreeTimesFaster.png)

Les temps de chargement sont désormais trois fois plus rapides qu’avec natif [!DNL Commerce] regroupement.
