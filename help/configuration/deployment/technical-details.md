---
title: Détails techniques
description: Découvrez les détails techniques du déploiement du pipeline, les types de configurations et les workflows recommandés.
exl-id: a396d241-f895-4414-92af-3abf3511e62a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 0%

---

# Détails techniques

Cette rubrique aborde les détails techniques de mise en oeuvre du déploiement du pipeline dans Commerce 2.2 et versions ultérieures. Les améliorations peuvent être réparties dans les domaines suivants :

- [Gestion des configurations](#configuration-management)
- [Changements dans l’administration](#changes-in-the-admin)
- [Installation et suppression de cron](#install-and-remove-cron)

Cette rubrique traite également du [workflow recommandé](#recommended-workflow) pour le déploiement du pipeline et fournit quelques exemples pour vous aider à comprendre son fonctionnement.

Avant de commencer, consultez les [Conditions préalables requises pour votre développement, création et systèmes de production](../deployment/prerequisites.md).

## Gestion des configurations

Pour vous permettre de synchroniser et de gérer la configuration de vos systèmes de développement et de production, utilisez le modèle de remplacement suivant.

![ Méthode de détermination des valeurs de variable de configuration](../../assets/configuration/override-flow-diagram.png)

Comme le montre le diagramme, les valeurs de configuration sont utilisées dans l&#39;ordre suivant :

1. Si elles existent, les variables d’environnement remplacent toutes les autres valeurs.
1. À partir des fichiers de configuration partagés `env.php` et `config.php`. Les valeurs de `env.php` remplacent les valeurs de `config.php`.
1. Valeurs stockées en base.
1. Si aucune valeur n’existe dans l’une de ces sources, la valeur par défaut ou la valeur NULL est utilisée.

### Gestion de la configuration partagée

La configuration partagée est stockée dans `app/etc/config.php`, qui doit être dans le contrôle de code source.

Définissez la configuration partagée dans le système Admin de votre développement (ou Adobe Commerce sur l’infrastructure cloud _integration_) et écrivez la configuration sur `config.php` à l’aide de la commande [`magento app:config:dump`](../cli/export-configuration.md).

### Gestion de la configuration spécifique au système

La configuration spécifique au système est stockée dans `app/etc/env.php`, qui doit _et non_ être dans le contrôle source.

Définissez la configuration spécifique au système dans l’administrateur de votre système de développement (ou d’intégration d’Adobe Commerce sur l’infrastructure cloud) et écrivez la configuration sur `env.php` à l’aide de la commande [`magento app:config:dump`](../cli/export-configuration.md).

Cette commande écrit également des paramètres sensibles sur `env.php`.

### Gestion de la configuration sensible

La configuration sensible est également stockée dans `app/etc/env.php`.

Vous pouvez gérer la configuration sensible de l&#39;une des manières suivantes :

- Variables d’environnement
- Enregistrez la configuration sensible dans `env.php` sur votre système de production à l’aide de la commande [`magento config:set:sensitive`](../cli/set-configuration-values.md)

### Paramètres de configuration verrouillés dans l’administrateur

Tous les paramètres de configuration de `config.php` ou `env.php` sont verrouillés dans l’administrateur ; c’est-à-dire que ces paramètres ne peuvent pas être modifiés dans l’administrateur.
Utilisez la commande [`magento config:set` ou `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) pour modifier les paramètres des fichiers `config.php` ou `env.php`.

## L’administrateur Commerce

L’administrateur présente le comportement suivant en mode de production :

- Vous ne pouvez pas activer ou désactiver les types de cache dans l’administrateur.
- Les paramètres de développement ne sont pas disponibles (**Magasins** > Paramètres > **Configuration** > Avancé > **Développeur**), notamment :

   - Minimisation de CSS, JavaScript et HTML
   - Fusion CSS et JavaScript
   - compilation LESS côté serveur ou côté client
   - Traductions en ligne
   - Comme nous l&#39;avons mentionné précédemment, tout paramètre de configuration dans `config.php` ou `env.php` est verrouillé et ne peut pas être modifié dans l&#39;administrateur.
   - Vous pouvez modifier la langue d’administration uniquement pour les langues utilisées par les thèmes déployés.

     La figure suivante illustre un exemple de la liste **Paramètre de compte** > **Paramètre régional de l’interface** dans l’Admin affichant seulement deux paramètres régionaux déployés :

     ![Vous pouvez modifier les paramètres régionaux d’administration uniquement pour les paramètres régionaux déployés](../../assets/configuration/split-deploy-admin-locale.png)

- Vous ne pouvez pas modifier les paramètres régionaux d’une portée à l’aide de l’option Admin.

  Nous vous recommandons d’effectuer ces modifications avant de passer en mode Production.

  Vous pouvez toujours configurer les paramètres régionaux à l’aide de variables d’environnement ou de la commande d’interface de ligne de commande `config:set` avec le chemin `general/locale/code`.

## Installation et suppression de cron

Dans la version 2.2 pour la première fois, nous vous aidons à configurer votre tâche cron en fournissant la commande [`magento cron:install`](../cli/configure-cron-jobs.md). Cette commande configure un crontab en tant qu’utilisateur exécutant la commande.

Vous pouvez également supprimer crontab à l’aide de la commande `magento cron:remove`.

## Workflow de déploiement de pipeline recommandé

Le diagramme suivant montre comment nous vous recommandons d’utiliser le déploiement du pipeline pour gérer la configuration.

![Workflow de déploiement de pipeline recommandé](../../assets/configuration/split-deploy-workflow.png)

### Système de développement

Sur votre système de développement, vous effectuez des modifications de configuration dans l’administrateur et générez la configuration partagée, `app/etc/config.php` et la configuration spécifique au système, `app/etc/env.php`. Vérifiez le code Commerce et la configuration partagée dans le contrôle de code source et poussez-le vers le serveur de génération.

Vous devez également installer des extensions et personnaliser le code Commerce sur le système de développement.

Sur votre système de développement :

1. Définissez la configuration dans Admin.

1. Utilisez la commande `magento app:config:dump` pour écrire la configuration dans le système de fichiers.

   - `app/etc/config.php` est la configuration partagée, qui contient tous les paramètres _à l&#39;exception de_ des paramètres sensibles et spécifiques au système. Ce fichier doit être dans le contrôle de code source.
   - `app/etc/env.php` est la configuration spécifique au système, qui contient des paramètres propres à un système particulier (par exemple, les noms d’hôtes et les numéros de port). Ce fichier doit _et non_ être dans le contrôle de code source.

1. Ajoutez le code modifié et la configuration partagée au contrôle de code source.

1. Pour supprimer le code php généré et les fichiers de ressources statiques en cours de développement, exécutez les commandes suivantes :

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

Après avoir exécuté les commandes pour effacer les ressources, Commerce génère des fichiers de travail.

>[!WARNING]
>
>Soyez prudent avec l’approche ci-dessus. La suppression du fichier `.htacces`s dans le dossier `generated` ou `pub` peut entraîner des problèmes.

### Système de création

Le système de génération compile le code et génère des fichiers d’affichage statiques pour les thèmes enregistrés dans Commerce. Il n’a pas besoin d’une connexion à la base de données Commerce ; il n’a besoin que du code base Commerce.

Sur votre système de génération :

1. Extrayez le fichier de configuration partagé du contrôle source.
1. Utilisez la commande `magento setup:di:compile` pour compiler le code.
1. Utilisez la commande `magento setup:static-content:deploy -f` pour mettre à jour les fichiers statiques d’affichage de fichier.
1. Vérifiez les mises à jour dans le contrôle de code source.

>[!INFO]
>
>Voir [Stratégies de déploiement pour les fichiers d’affichage statique](../cli/static-view-file-strategy.md).

### Système de production

Sur votre système de production (c’est-à-dire votre boutique en ligne), vous extrayez les ressources générées et les mises à jour de code du contrôle source, et définissez des paramètres de configuration spécifiques au système et sensibles à l’aide de la ligne de commande ou des variables d’environnement.

Sur votre système de production :

1. Démarrer le mode de maintenance.
1. Récupérez le code et les mises à jour de configuration à partir du contrôle source.
1. Si vous utilisez Adobe Commerce, arrêtez les programmes de travail en file d’attente.
1. Utilisez la commande `magento app:config:import` pour importer les modifications de configuration dans le système de production.
1. Si vous avez installé des composants qui ont modifié le schéma de base de données, exécutez `magento setup:upgrade --keep-generated` pour mettre à jour le schéma et les données de la base de données, en préservant les fichiers statiques générés.
1. Pour définir des paramètres spécifiques au système, utilisez la commande `magento config:set` ou les variables d&#39;environnement.
1. Pour définir des paramètres sensibles, utilisez la commande `magento config:sensitive:set` ou les variables d&#39;environnement.
1. Nettoyez le cache (également appelé _vidage_).
1. Mode de maintenance de fin.

## Commandes de gestion des configurations

Nous fournissons les commandes suivantes pour vous aider à gérer la configuration :

- [`magento app:config:dump`](../cli/export-configuration.md) pour écrire les paramètres de configuration de l’administrateur sur `config.php` et `env.php` (à l’exception des paramètres sensibles)
- [`magento config:set`](../cli/set-configuration-values.md) pour définir les valeurs des paramètres spécifiques au système sur le système de production.

  Utilisez l’option facultative `--lock` pour verrouiller l’option dans l’administrateur (c’est-à-dire rendre le paramètre non modifiable). Si un paramètre est déjà verrouillé, utilisez l’option `--lock` pour le modifier.

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) pour définir les valeurs des paramètres sensibles sur le système de production.
- [`magento app:config:import`](../cli/import-configuration.md) pour importer les modifications de configuration de `config.php` et `env.php` dans le système de production.

## Exemples de gestion de configuration

Cette section présente des exemples de gestion de la configuration afin que vous puissiez voir comment les modifications sont apportées à `config.php` et `env.php`.

### Modification des paramètres régionaux par défaut

Cette section présente la modification apportée à `config.php` lorsque vous modifiez l’unité de poids par défaut à l’aide de l’option Admin (**Magasins** > Paramètres > **Configuration** > Général > **Général** > **Options de paramètres régionaux**).

Après avoir apporté la modification à l’administrateur, exécutez `bin/magento app:config:dump` pour écrire la valeur sur `config.php`. La valeur est écrite dans le tableau `general` sous `locale` comme le montre le fragment de code suivant de `config.php` :

```php
'general' =>
    array (
        'locale' =>
        array (
            'code' => 'en_US',
            'timezone' => 'America/Chicago',
            'weight_unit' => 'kgs'
        )
    )
```

### Modification de plusieurs paramètres de configuration

Cette section explique comment effectuer les modifications de configuration suivantes :

- Ajout d’une vue de site web, de magasin et de magasin (**Magasins** > Paramètres > **Toutes les boutiques**)
- Modification du domaine de messagerie par défaut (**Magasins** > Paramètres > **Configuration** > Clients > **Configuration client**)
- Définition du nom d’utilisateur et du mot de passe de l’API PayPal (**Magasins** > Paramètres > **Configuration** > Ventes > **Méthodes de paiement** > **PayPal** > **Paramètres PayPal requis**)

Après avoir apporté la modification à l’administrateur, exécutez `bin/magento app:config:dump` sur votre système de développement. Cette fois-ci, toutes vos modifications ne sont pas écrites sur `config.php` ; en fait, seules la vue de site web, de magasin et de magasin sont écrites dans ce fichier comme le montrent les fragments suivants.

### config.php

`config.php` contient :

- Modifications de la vue du site web, du magasin et du magasin.
- Paramètres du moteur de recherche non spécifique au système
- Paramètres PayPal non sensibles
- Commentaires qui vous informent des paramètres sensibles qui ont été omis de `config.php`

`websites` array :

```php
      'new' =>
      array (
        'website_id' => '2',
        'code' => 'new',
        'name' => 'New website',
        'sort_order' => '0',
        'default_group_id' => '2',
        'is_default' => '0',
      ),
```

`groups` array :

```php
      2 =>
      array (
        'group_id' => '2',
        'website_id' => '2',
        'code' => 'newstore',
        'name' => 'New store',
        'root_category_id' => '2',
        'default_store_id' => '2',
      ),
```

`stores` array :

```php
     'newview' =>
      array (
        'store_id' => '2',
        'code' => 'newview',
        'website_id' => '2',
        'group_id' => '2',
        'name' => 'New store view',
        'sort_order' => '0',
        'is_active' => '1',
      ),
```

`payment` array :

```php
      'payment' =>
      array (
        'paypal_express' =>
        array (
          'active' => '0',
          'in_context' => '0',
          'title' => 'PayPal Express Checkout',
          'sort_order' => NULL,
          'payment_action' => 'Authorization',
          'visible_on_product' => '1',
          'visible_on_cart' => '1',
          'allowspecific' => '0',
          'verify_peer' => '1',
          'line_items_enabled' => '1',
          'transfer_shipping_options' => '0',
          'solution_type' => 'Mark',
          'require_billing_address' => '0',
          'allow_ba_signup' => 'never',
          'skip_order_review_step' => '1',
        ),
```

### env.php

Le paramètre de configuration par défaut spécifique au système du domaine de messagerie est écrit sur `app/etc/env.php`.

Les paramètres PayPal ne sont écrits dans aucun fichier, car la commande `bin/magento app:config:dump` n’écrit pas de paramètres sensibles. Vous devez définir les paramètres PayPal sur le système de production à l’aide des commandes suivantes :

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
