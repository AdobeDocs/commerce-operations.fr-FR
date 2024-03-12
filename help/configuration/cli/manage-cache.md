---
title: Gestion du cache
description: Gérez les types de cache et affichez l’état du cache.
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 6e0e7f209b265e5b924e0092fec020e0cefc165d
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 0%

---

# Gestion du cache

{{file-system-owner}}

## Types de cache

Commerce possède les types de cache suivants :

| Nom &quot;convivial&quot; du type de cache | Nom du code de type de cache | Description |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configuration | config | Commerce collecte la configuration de tous les modules, la fusionne et enregistre le résultat fusionné dans le cache. Ce cache contient également des paramètres spécifiques au magasin stockés dans le système de fichiers et la base de données. Nettoyez ou videz ce type de cache après avoir modifié les fichiers de configuration. |
| Disposition | layout | Mises en page compilées (c’est-à-dire les composants de mise en page de tous les composants). Nettoyez ou videz ce type de cache après avoir modifié les fichiers de mise en page. |
| Sortie de HTML par bloc | block_html | Fragments de page par bloc de HTML. Nettoyez ou videz ce type de cache après avoir modifié la couche d’affichage. |
| Données de collections | collections | Résultats des requêtes de base de données. Si nécessaire, Commerce nettoie automatiquement ce cache, mais les développeurs tiers peuvent placer n’importe quelle donnée dans n’importe quel segment du cache. Nettoyez ou videz ce type de cache si votre module personnalisé utilise une logique qui entraîne des entrées de cache que Commerce ne peut pas nettoyer. |
| DDL | db_ddl | Schéma de la base de données. Si nécessaire, Commerce nettoie automatiquement ce cache, mais les développeurs tiers peuvent placer n’importe quelle donnée dans n’importe quel segment du cache. Nettoyez ou videz ce type de cache après avoir apporté des modifications personnalisées au schéma de base de données. (En d’autres termes, les mises à jour que Commerce ne s’auto-fabrique pas.) Pour mettre automatiquement à jour le schéma de base de données, utilisez le `magento setup:db-schema:upgrade` . |
| Configuration compilée | compile_config | Configuration de la compilation |
| Valeur d’attribut d’entité (EAV) | eav | Métadonnées liées aux attributs EAV (par exemple, étiquettes de magasin, liens vers le code PHP associé, rendu d’attribut, paramètres de recherche, etc.). En règle générale, vous n’avez pas besoin de nettoyer ou de vider ce type de cache. |
| Cache de page | full_page | Pages de HTML générées. Si nécessaire, Commerce nettoie automatiquement ce cache, mais les développeurs tiers peuvent placer n’importe quelle donnée dans n’importe quel segment du cache. Nettoyez ou videz ce type de cache après avoir modifié le niveau de code qui affecte la sortie du HTML. Il est recommandé de conserver ce cache activé, car le HTML de mise en cache améliore considérablement les performances. |
| Réflexion | reflet | Supprime une dépendance entre le module Webapi et le module Client. |
| Traductions | translate | Après la fusion des traductions de tous les modules, le cache de fusion sera nettoyé. |
| Configuration de l’intégration | config_integration | Intégrations compilées. Nettoyez ou videz ce cache après avoir modifié ou ajouté des intégrations. |
| Configuration de l’API d’intégration | config_integration_api | Configuration des API d’intégration compilée des intégrations du magasin. |
| Résultats du résolveur de requête GraphQL [!BADGE 2.4.7-beta]{type=URL informative=&quot;/help/release/release-notes/commerce/2-4-7.md&quot; tooltip=&quot;Disponible dans la version 2.4.7-bêta uniquement&quot;} | graphql_query_resolver_result | Met en cache les résultats des programmes de résolution de requêtes GraphQL pour les entités client, page CMS, bloc CMS et galerie de médias de produits. Conservez ce cache activé pour améliorer les performances de GraphQL. |
| Configuration des services web | config_webservice | Mise en cache de la structure de l’API Web. |
| Notification client | customer_notification | Notifications temporaires qui apparaissent dans l’interface utilisateur. |

## Affichage de l’état du cache

Pour afficher l’état du cache, saisissez

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

Voici un exemple :

```terminal
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
                           eav: 1
         customer_notification: 1
                     full_page: 1
            config_integration: 1
        config_integration_api: 1
                   target_rule: 1
 graphql_query_resolver_result: 1
             config_webservice: 1
                     translate: 1
```

## Activation ou désactivation des types de cache

Cette commande permet d’activer ou de désactiver tous les types de cache ou uniquement ceux que vous spécifiez. La désactivation des types de cache est utile lors du développement, car vous voyez les résultats de vos modifications sans avoir à vider le cache. Toutefois, la désactivation des types de cache a un effet négatif sur les performances.

>[!INFO]
>
>À partir de la version 2.2, vous pouvez uniquement activer ou désactiver les types de cache à l’aide de la ligne de commande lors de l’exécution de Commerce en mode de production. Si vous exécutez Commerce en mode Développeur, vous pouvez activer ou désactiver les types de cache à l’aide de la ligne de commande ou manuellement. Avant cela, vous devez effectuer manuellement les opérations suivantes : `<magento_root>/app/etc/env.php` modifiable par la fonction [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).

Vous pouvez effectuer un nettoyage (également appelé _purge_ ou _actualiser_) les types de cache à l’aide de la ligne de commande ou de l’administrateur.

Options de commande :

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Où omettre `[type]` active ou désactive tous les types de cache en même temps. La variable `type` est une liste de types de cache séparés par des espaces.

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

Pour répertorier les types de cache et leur état :

```bash
bin/magento cache:status
```

Par exemple, pour désactiver le cache de page complet et le cache DDL :

```bash
bin/magento cache:disable db_ddl full_page
```

Exemple de résultat :

```terminal
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>L’activation d’un type de cache efface automatiquement ce type de cache.

>[!INFO]
>
>À compter de la version 2.3.4, Commerce met en cache tous les attributs EAV système lors de leur récupération. La mise en cache des attributs EAV de cette manière améliore les performances, car elle réduit le nombre de requêtes d’insertion/sélection dans la base de données. Cependant, elle augmente également la taille du réseau du cache. Les développeurs peuvent mettre en cache des attributs de fichier EAV personnalisés en exécutant la fonction `bin/magento config:set dev/caching/cache_user_defined_attributes 1` . Vous pouvez également le faire à partir de l’administrateur lors de l’ [Mode Développeur](../bootstrap/application-modes.md) en définissant **Magasins** > Paramètres **Configuration** > **Avancé** > **Développeur** > **Paramètres de mise en cache** > **Attributs définis par l’utilisateur du cache** to **Oui**.

## Nettoyer et vider les types de cache

>[!NOTE]
>
>Le cache de plusieurs pages peut être invalidé simultanément et automatiquement. **_without_** ces entités sont en train de les modifier. Par exemple, lorsqu’un produit du catalogue est affecté à une catégorie, ou lorsqu’une catégorie [!UICONTROL related product rule] est modifié.

Pour purger les éléments obsolètes du cache, vous pouvez _clean_ ou _purge_ types de cache :

- Le nettoyage d’un type de cache supprime uniquement tous les éléments des types de cache Commerce activés. En d’autres termes, cette option n’affecte pas les autres processus ou applications, car elle nettoie uniquement le cache utilisé par Commerce.

  Les types de cache désactivés ne sont pas nettoyés.

  >[!TIP]
  >
  >Nettoyez toujours le cache après la mise à niveau des versions de Magento Open Source ou Adobe Commerce, la mise à niveau de Magento Open Source vers Adobe Commerce ou l’installation B2B pour Adobe Commerce ou tout autre module.

- Le vidage d’un type de cache purge le stockage du cache, ce qui peut affecter d’autres processus et applications qui utilisent le même stockage.

Purge des types de cache si vous avez déjà essayé de nettoyer le cache et que vous rencontrez toujours des problèmes que vous ne pouvez pas isoler.

Utilisation des commandes :

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Où `[type]` est une liste de types de cache séparés par des espaces. Omission `[type]` nettoie ou vide tous les types de cache en même temps. Par exemple, pour vider tous les types de cache, saisissez

```bash
   bin/magento cache:flush
```

Exemple de résultat :

```terminal
   Flushed cache types:
   config
   layout
   block_html
   collections
   reflection
   db_ddl
   compiled_config
   eav
   customer_notification
   config_integration
   config_integration_api
   full_page
   graphql_query_resolver_results
   config_webservice
   translate
```

>[!TIP]
>
>Vous pouvez également nettoyer et vider les types de cache dans l’Admin. Accédez à **Système** > **Outils** > **Gestion du cache**. **Stockage du cache de vidage** équivaut à `bin/magento cache:flush`. **Vider le cache du Magento** équivaut à `bin/magento cache:clean`.
