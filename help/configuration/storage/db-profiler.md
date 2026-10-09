---
title: Configuration du profileur de base de données
description: Consultez un exemple de configuration de sortie pour le profileur de base de données.
feature: Configuration, Storage
badge: label="Contribution Atish Goswami" type="Informative" url="https://github.com/atishgoswami" tooltip="Atish Goswami"
exl-id: 87780db5-6e50-4ebb-9591-0cf22ab39af5
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%
---
# Configuration du profileur de base de données

Le profileur de base de données Commerce affiche toutes les requêtes implémentées sur une page, y compris l’heure de chaque requête et les paramètres appliqués.

## Étape 1 : modifier la configuration de déploiement

Modifiez `<magento_root>/app/etc/env.php` pour ajouter la référence suivante à la classe [profileur de base de données](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php) :

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

## Étape 2 : configurer la sortie

Configurez la sortie dans le fichier d’amorçage de votre application Commerce. Il peut s’agir d’un fichier `<magento_root>/pub/index.php` ou d’une configuration d’hôte virtuel de serveur web.

L’exemple suivant affiche les résultats dans un tableau à trois colonnes :

- Durée totale (affiche la durée totale nécessaire pour exécuter toutes les requêtes sur la page)
- SQL (affiche toutes les requêtes SQL ; l&#39;en-tête de ligne affiche le nombre de requêtes)
- Paramètres de requête (affiche les paramètres de chaque requête SQL)

Pour configurer la sortie, ajoutez les éléments suivants après la ligne `$bootstrap->run($app);` dans votre fichier de données d’amorçage :

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
