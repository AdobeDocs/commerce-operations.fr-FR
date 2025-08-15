---
title: Gérer le cache
description: Gérez les types de cache et affichez l’état du cache à partir de la ligne de commande à l’aide de l’interface de ligne de commande Commerce
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Gérer le cache

{{file-system-owner}}

## Types de cache

Vous pouvez utiliser le système de gestion du cache d’Adobe Commerce pour améliorer les performances de votre site. Cette rubrique explique comment les administrateurs système ou les développeurs ayant accès au serveur d’applications Commerce peuvent gérer les caches à partir de la ligne de commande.

>[!NOTE]
>
>
>Les administrateurs de site Commerce peuvent gérer le cache à partir de l’Administration à l’aide de l’outil Système de gestion du cache. Voir [ Gestion du cache ](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/tools/cache-management) dans le _Guide des systèmes d’administration_.


## Affichage de l’état du cache

À partir de la ligne de commande du serveur d’applications Commerce, affichez l’état du cache à l’aide de la commande `cache:status` de l’interface de ligne de commande Commerce.

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

Voici un exemple :

```
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
             webhooks_response: 1
                           eav: 1
         customer_notification: 1
 graphql_query_resolver_result: 1
            config_integration: 1
        config_integration_api: 1
                  admin_ui_sdk: 1
                     full_page: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

>[!TIP]
>
>Pour obtenir une description détaillée des types de cache par défaut pris en charge par Adobe Commerce, reportez-vous à la section [Caches](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/tools/cache-management#caches) du _Guide des systèmes d’administration_.


## Activation ou désactivation des types de cache

Cette commande permet d’activer ou de désactiver tous les types de cache ou uniquement ceux que vous spécifiez. La désactivation des types de cache est utile pendant le développement, car vous pouvez voir les résultats de vos modifications sans avoir à vider le cache. Cependant, la désactivation des types de cache a un effet négatif sur les performances.

>[!INFO]
>
>À partir de la version 2.2, vous pouvez uniquement activer ou désactiver les types de cache à l’aide de la ligne de commande lors de l’exécution de Commerce en mode production. Si vous exécutez Commerce en mode développeur, vous pouvez activer ou désactiver les types de cache à l’aide de la ligne de commande ou manuellement. Avant cela, vous devez rendre les `<magento_root>/app/etc/env.php` modifiables manuellement par le [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).

Vous pouvez nettoyer les types de cache (également appelés _vidage_ ou _actualisation_) à l’aide de la ligne de commande ou de l’interface d’administration.

Options de commande :

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Lorsque l’omission de `[type]` active ou désactive tous les types de cache en même temps. L’option `type` est une liste de types de cache séparés par des espaces.

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

Pour répertorier les types de cache et leur statut :

```bash
bin/magento cache:status
```

Par exemple, pour désactiver le cache de page complet et le cache DDL :

```bash
bin/magento cache:disable db_ddl full_page
```

Exemple de résultat :

```
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>L’activation d’un type de cache efface automatiquement ce type de cache.

>[!INFO]
>
>Depuis la version 2.3.4, Commerce met en cache tous les attributs EAV du système lors de leur récupération. La mise en cache des attributs EAV de cette manière améliore les performances, car elle réduit la quantité de requêtes d’insertion/sélection vers la base de données. Toutefois, cela augmente également la taille du réseau de cache. Les développeurs peuvent mettre en cache des attributs EAV personnalisés en exécutant la commande `bin/magento config:set dev/caching/cache_user_defined_attributes 1` . Vous pouvez également effectuer cette opération à partir de l’Administration en [mode Développeur](../bootstrap/application-modes.md) en définissant **Magasins** > Paramètres **Configuration** > **Avancé** > **Développeur** > **Paramètres de mise en cache** > **Cache Attributs définis par l’utilisateur** à **Yes**.

## Nettoyer et vider les types de cache

>[!NOTE]
>
>Le cache de plusieurs pages peut être invalidé simultanément et automatiquement **_sans que_** ces entités ne soient modifiées). Par exemple, lorsqu’un produit du catalogue est affecté à une catégorie ou lorsqu’un [!UICONTROL related product rule] est modifié.

Pour purger les éléments obsolètes du cache, vous pouvez _nettoyer_ ou _vider_ les types de cache suivants :

- Le nettoyage d’un type de cache supprime uniquement tous les éléments des types de cache Commerce activés. En d’autres termes, cette option n’affecte pas d’autres processus ou applications, car elle nettoie uniquement le cache utilisé par Commerce.

  Les types de cache désactivés ne sont pas nettoyés.

  >[!TIP]
  >
  >Nettoyez toujours le cache après la mise à niveau des versions d’Adobe Commerce, la mise à niveau de Magento Open Source vers Adobe Commerce ou l’installation du B2B pour Adobe Commerce ou tout module.

- Le vidage d’un type de cache purge le stockage en cache, ce qui peut avoir une incidence sur les autres processus et applications qui utilisent le même stockage.

Videz les types de cache si vous avez déjà essayé de nettoyer le cache et que vous rencontrez toujours des problèmes que vous ne pouvez pas isoler.

Utilisation des commandes :

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Où `[type]` est une liste de types de cache séparés par des espaces. L’omission de `[type]` nettoie ou vide tous les types de cache en même temps. Par exemple, pour vider tous les types de cache, saisissez

```bash
   bin/magento cache:flush
```

Exemple de résultat :

```
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
>Vous pouvez également nettoyer et vider les types de cache dans l’Administration. Accédez à **Système** > **Outils** > **Gestion du cache**. **Vidage du stockage du cache** équivaut à `bin/magento cache:flush`. **Vider le cache Magento** équivaut à `bin/magento cache:clean`.
