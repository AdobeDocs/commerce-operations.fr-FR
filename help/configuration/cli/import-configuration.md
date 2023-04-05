---
title: Importation de données à partir de fichiers de configuration
description: Importez les paramètres de configuration Adobe Commerce à partir des fichiers de configuration.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---


# Importation des paramètres de configuration

{{file-system-owner}}

Lorsque vous configurez un système de production à l’aide de Commerce 2.2 [modèle de déploiement de pipeline](../deployment/technical-details.md), vous devez _import_ paramètres de configuration de `config.php` et `env.php` dans la base de données.
Ces paramètres comprennent les chemins et valeurs de configuration, les sites web, les magasins, les vues de magasin et les thèmes.

Après avoir importé des sites web, des magasins, des vues de magasin et des thèmes, vous pouvez créer des attributs de produit et les appliquer aux sites web, aux magasins et aux vues de magasin, sur le système de production.

>[!INFO]
>
>Le `bin/magento app:config:import` ne traite pas la configuration stockée dans les variables d’environnement.

## Importer, commande

Sur votre système de production, exécutez la commande suivante pour importer les données des fichiers de configuration (`config.php` et `env.php`) vers la base de données :

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Utilisez les options facultatives `[-n, --no-interaction]` Indicateur pour importer des données sans aucune interaction.

Si vous saisissez `bin/magento app:config:import` sans l’indicateur facultatif, vous devez confirmer les modifications.

Par exemple, si le fichier de configuration contient un nouveau site web et un nouveau magasin, le message suivant s’affiche :

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Pour poursuivre l&#39;import, saisissez `yes`.

Si les fichiers de configuration de déploiement contiennent des données à importer, un message similaire à ce qui suit s’affiche :

```terminal
Start import:
Some information about importing
```

Si les fichiers de configuration de déploiement ne contiennent pas de données à importer, un message similaire à ce qui suit s’affiche :

```terminal
Start import:
Nothing to import
```

## Éléments importés

Les sections suivantes abordent en détail les données que nous importons.

### Configuration du système

Commerce utilise directement les valeurs de la variable `system` du tableau `config.php` ou `env.php` au lieu de les importer dans la base de données, car ils nécessitent des actions de prétraitement et de post-traitement.

Par exemple, la valeur du chemin de configuration `web/secure/base_url` doit être validé avec des modèles d’arrière-plan.

#### Modèles principaux

Les modèles d’arrière-plan sont le mécanisme de traitement des modifications dans la configuration du système.
Vous définissez les modules principaux dans `<module_name>/adminhtml/system.xml`.

Tous les modèles principaux doivent étendre la variable [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) classe .

Lorsque nous importons des modèles d’arrière-plan, nous n’enregistrons pas les valeurs de configuration.

### Configuration des sites web, des magasins et des groupes de magasins

Nous importons les types de configurations suivants.
(Ces configurations se trouvent sous la propriété `scopes` tableau dans `config.php`.)

- `websites`: configuration liée aux sites web
- `groups`: stocke la configuration associée
- `stores`: configuration associée aux vues de magasin

Les paramétrages précédents peuvent être importés dans les modes suivants :

- `create`: `config.php` contient de nouvelles entités (`websites`, `groups`, `stores`) qui sont absents de l’environnement de production ;
- `update`: `config.php` contient des entités (`websites`, `groups`, `stores`) qui sont différents de l’environnement de production ;
- `delete`: `config.php` does _not_ contient des entités (`websites`, `groups`, `stores`) présents dans l’environnement de production ;

>[!INFO]
>
>Nous n’importons pas la catégorie racine associée aux magasins. Vous devez associer une catégorie racine à un magasin à l’aide de l’administrateur Commerce.

### Configuration du thème

La configuration de thème comprend tous les thèmes enregistrés dans votre système Commerce ; les données proviennent directement de la variable `theme` table de base de données. (La configuration du thème se trouve dans la variable `themes` tableau dans `config.php`.)

#### Structure des données de thème

La clé du tableau est le chemin d’accès complet au thème : `area` + `theme path`

Par exemple : `frontend/Magento/luma`.
`frontend` est une zone et `Magento/luma` est le chemin du thème.

La valeur du tableau est data about theme : code, titre, chemin, identifiant parent

Exemple complet :

```php?start_inline=1
'frontend/Magento/luma' =>
   array (
      'parent_id' => 'Magento/blank',
      'theme_path' => 'Magento/luma',
      'theme_title' => 'Magento Luma',
      'is_featured' => '0',
      'area' => 'frontend',
      'type' => '0',
      'code' => 'Magento/luma',
),
```

>[!INFO]
>
>- _Enregistrement du thème_. Si des données de thème sont définies dans `config.php` mais le code source du thème n’est pas présent dans le système de fichiers, le thème est ignoré (c’est-à-dire, il n’est pas enregistré).
>- _Suppression de thème_. Si un thème n’est pas présent dans `config.php` mais que le code source est présent sur le système de fichiers, le thème n’est pas supprimé.

