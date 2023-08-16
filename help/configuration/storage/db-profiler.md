---
title: Configuration du profileur de base de données
description: Consultez un exemple de configuration de la sortie pour le profileur de base de données.
feature: Configuration, Storage
badge: label="Contribution de Atish Goswami" type="Informative" url="https://github.com/atishgoswami" tooltip="Goswami d&#39;Asie"
exl-id: 87780db5-6e50-4ebb-9591-0cf22ab39af5
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# Configuration du profileur de base de données

Le profileur de base de données Commerce affiche toutes les requêtes implémentées sur une page, y compris l’heure de chaque requête et les paramètres appliqués.

## Étape 1 : modification de la configuration du déploiement

Modifier `<magento_root>/app/etc/env.php` pour ajouter la référence suivante au [classe profileur de base de données](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

Voici un exemple :

```php?start_inline=1
 'db' =>
  array (
    'table_prefix' => '',
    'connection' =>
    array (
      'default' =>
      array (
        'host' => 'localhost',
        'dbname' => 'magento',
        'username' => 'magento',
        'password' => 'magento',
        'model' => 'mysql4',
        'engine' => 'innodb',
        'initStatements' => 'SET NAMES utf8;',
        'active' => '1',
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
      ),
    ),
  ),
```

## Etape 2 : paramétrer la sortie

Configurez la sortie dans votre fichier d’amorçage de l’application Commerce. Il peut s’agir de `<magento_root>/pub/index.php` ou il peut se trouver dans une configuration d’hôte virtuel d’un serveur web.

L’exemple suivant affiche les résultats dans un tableau à trois colonnes :

- Durée totale (affiche la durée totale d’exécution de toutes les requêtes sur la page)
- SQL (affiche toutes les requêtes SQL ; l’en-tête de ligne affiche le nombre de requêtes)
- Paramètres de requête (affiche les paramètres de chaque requête SQL)

Pour configurer la sortie, ajoutez ce qui suit après la `$bootstrap->run($app);` dans votre fichier bootstrap :

```php?start_inline=1
/** @var \Magento\Framework\App\ResourceConnection $res */
$res = \Magento\Framework\App\ObjectManager::getInstance()->get('Magento\Framework\App\ResourceConnection');
/** @var Magento\Framework\DB\Profiler $profiler */
$profiler = $res->getConnection('read')->getProfiler();
echo "<table cellpadding='0' cellspacing='0' border='1'>";
echo "<tr>";
echo "<th>Time <br/>[Total Time: ".$profiler->getTotalElapsedSecs()." secs]</th>";
echo "<th>SQL [Total: ".$profiler->getTotalNumQueries()." queries]</th>";
echo "<th>Query Params</th>";
echo "</tr>";
foreach ($profiler->getQueryProfiles() as $query) {
    /** @var Zend_Db_Profiler_Query $query*/
    echo '<tr>';
    echo '<td>', number_format(1000 * $query->getElapsedSecs(), 2), 'ms', '</td>';
    echo '<td>', $query->getQuery(), '</td>';
    echo '<td>', json_encode($query->getQueryParams()), '</td>';
    echo '</tr>';
}
echo "</table>";
```

## Etape 3 : Visualiser les résultats

Accédez à n’importe quelle page de votre storefront ou de votre administrateur pour afficher les résultats. Voici un exemple :

![Exemples de résultats du profileur de base de données](../../assets/configuration/db-profiler-results.png)
