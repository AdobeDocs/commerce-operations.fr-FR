---
title: Gestion du cache
description: Gestion des types de cache et affichage de l’état du cache à partir de la ligne de commande à l’aide de l’interface de ligne de commande Commerce
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Gestion du cache

{{file-system-owner}}

## Types de cache

Vous pouvez utiliser le système de gestion du cache d’Adobe Commerce pour améliorer les performances de votre site. Cette rubrique explique comment les administrateurs système ou les développeurs ayant accès au serveur d’applications Commerce peuvent gérer les caches à partir de la ligne de commande.

>[!NOTE]
>
>
>Les administrateurs de site de commerce peuvent gérer le cache à partir de l’administrateur à l’aide de l’outil Système de gestion du cache. Voir [Gestion du cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) dans le _Guide des systèmes d’administration_.


## Affichage de l’état du cache

Dans la ligne de commande du serveur applicatif Commerce, affichez l’état du cache à l’aide de la fonction `cache:status` Commande de l’interface de ligne de commande Commerce.

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
>Pour une description détaillée des types de cache par défaut pris en charge par Adobe Commerce, voir [Caches](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#caches) dans le _Guide des systèmes d’administration_.


## Activation ou désactivation des types de cache

Cette commande permet d’activer ou de désactiver tous les types de cache ou uniquement ceux que vous spécifiez. La désactivation des types de cache est utile lors du développement, car vous voyez les résultats de vos modifications sans avoir à vider le cache. Toutefois, la désactivation des types de cache a un effet négatif sur les performances.

>[!INFO]
>
>À partir de la version 2.2, vous pouvez uniquement activer ou désactiver les types de cache à l’aide de la ligne de commande lors de l’exécution de Commerce en mode de production. Si vous exécutez Commerce en mode développeur, vous pouvez activer ou désactiver les types de cache à l’aide de la ligne de commande ou manuellement. Avant cela, vous devez effectuer manuellement les opérations suivantes : `<magento_root>/app/etc/env.php` modifiable par la fonction [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md).

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
  >Nettoyez toujours le cache après la mise à niveau des versions d’Adobe Commerce, la mise à niveau de Magento Open Source vers Adobe Commerce ou l’installation de B2B pour Adobe Commerce ou tout autre module.

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
