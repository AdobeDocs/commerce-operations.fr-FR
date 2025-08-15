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

Cette rubrique présente les détails techniques d’implémentation du déploiement de pipeline dans Commerce 2.2 et versions ultérieures. Les améliorations peuvent être divisées en plusieurs domaines :

- [Gestion de la configuration](#configuration-management)
- [Modifications dans l’administrateur](#changes-in-the-admin)
- [Installation et suppression de cron](#install-and-remove-cron)

Cette rubrique présente également le [workflow recommandé](#recommended-workflow) pour le déploiement de pipeline et fournit quelques exemples pour vous aider à comprendre son fonctionnement.

Avant de commencer, passez en revue les [ Conditions préalables pour les systèmes de développement, de version et de production](../deployment/prerequisites.md).

## Gestion de la configuration

Pour vous permettre de synchroniser et de gérer la configuration de vos systèmes de développement et de production, utilisez le schéma de remplacement suivant.

![Comment les valeurs des variables de configuration sont déterminées ](../../assets/configuration/override-flow-diagram.png)

Comme le montre le diagramme, les valeurs de configuration sont utilisées dans l&#39;ordre suivant :

1. Les variables d’environnement, si elles existent, remplacent toutes les autres valeurs.
1. À partir des fichiers de configuration partagés `env.php` et `config.php`. Les valeurs de `env.php` remplacent celles de `config.php`.
1. À partir des valeurs stockées dans la base.
1. Si aucune valeur n&#39;existe dans l&#39;une de ces sources, la valeur par défaut ou NULL est utilisée.

### Gestion de la configuration partagée

La configuration partagée est stockée dans `app/etc/config.php`, qui doit se trouver dans le contrôle de code source.

Définissez la configuration partagée dans Admin sur votre système de développement (ou Adobe Commerce sur l’infrastructure cloud _intégration_) et écrivez la configuration dans `config.php` à l’aide de la commande [`magento app:config:dump`](../cli/export-configuration.md).

### Gestion de la configuration spécifique au système

La configuration spécifique au système est stockée dans `app/etc/env.php`, qui ne doit _pas_ se trouver dans le contrôle de code source.

Définissez la configuration spécifique au système dans l’Admin de votre système de développement (ou Adobe Commerce sur l’intégration d’infrastructure cloud) et écrivez la configuration dans `env.php` à l’aide de la commande [`magento app:config:dump`](../cli/export-configuration.md).

Cette commande écrit également les paramètres sensibles dans `env.php`.

### Gestion de la configuration sensible

La configuration sensible est également stockée dans `app/etc/env.php`.

Vous pouvez gérer la configuration sensible de l’une des manières suivantes :

- Variables d’environnement
- Enregistrez la configuration sensible dans `env.php` sur votre système d’exploitation à l’aide de la commande [`magento config:set:sensitive`](../cli/set-configuration-values.md)

### Paramètres de configuration verrouillés dans l’administrateur

Tous les paramètres de configuration de `config.php` ou `env.php` sont verrouillés dans l’administration. En d’autres termes, ces paramètres ne peuvent pas être modifiés dans l’administration.
Utilisez la commande [`magento config:set` ou `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) pour modifier les paramètres des fichiers `config.php` ou `env.php`.

## Administrateur Commerce

L’administrateur présente le comportement suivant en mode de production :

- Vous ne pouvez pas activer ni désactiver les types de cache dans l’Administration
- Les paramètres du développeur ne sont pas disponibles (**Magasins** > Paramètres > **Configuration** > Avancé > **Développeur**), notamment :

   - Minimiser CSS, JavaScript et HTML
   - Fusion de CSS et JavaScript
   - Compilation LESS côté serveur ou côté client
   - Traductions intégrées
   - Comme nous l’avons vu précédemment, tout paramètre de configuration dans `config.php` ou `env.php` est verrouillé et ne peut pas être modifié dans Admin.
   - Vous pouvez modifier les paramètres régionaux d’administration uniquement pour les langues utilisées par les thèmes déployés

     La figure suivante présente un exemple de la liste **Paramètres du compte** > **Paramètres régionaux de l’interface** dans l’interface d’administration, qui n’affiche que deux paramètres régionaux déployés :

     ![Vous pouvez modifier les paramètres régionaux d’administration uniquement pour les paramètres régionaux déployés](../../assets/configuration/split-deploy-admin-locale.png)

- Vous ne pouvez pas modifier les configurations des paramètres régionaux pour une étendue à l’aide de l’administrateur.

  Nous vous recommandons d’apporter ces modifications avant de passer en mode Production.

  Vous pouvez toujours configurer le paramètre régional à l’aide de variables d’environnement ou de la commande d’interface de ligne de commande `config:set` avec le chemin `general/locale/code`.

## Installation et suppression de cron

Dans la version 2.2, pour la première fois, nous vous aidons à configurer votre tâche cron en fournissant la commande [`magento cron:install`](../cli/configure-cron-jobs.md). Cette commande configure un crontab en tant qu’utilisateur exécutant la commande.

Vous pouvez également supprimer crontab à l’aide de la commande `magento cron:remove`.

## Workflow de déploiement de pipeline recommandé

Le diagramme suivant montre comment nous vous recommandons d’utiliser le déploiement de pipeline pour gérer la configuration.

![Workflow de déploiement de pipeline recommandé](../../assets/configuration/split-deploy-workflow.png)

### Système de développement

Sur votre système de développement, vous apportez des modifications à la configuration dans l’Administration et générez la configuration partagée, `app/etc/config.php` et la configuration spécifique au système, `app/etc/env.php`. Vérifiez le code Commerce et la configuration partagée dans le contrôle de code source et envoyez-le au serveur de génération.

Vous devez également installer des extensions et personnaliser le code Commerce sur le système de développement.

Sur votre système de développement :

1. Définissez la configuration dans Admin.

1. Utilisez la commande `magento app:config:dump` pour écrire la configuration dans le système de fichiers.

   - `app/etc/config.php` est la configuration partagée, qui contient tous les paramètres _à l’exception_ paramètres sensibles et spécifiques au système. Ce fichier doit se trouver dans le contrôle de code source.
   - `app/etc/env.php` est la configuration spécifique au système, qui contient des paramètres propres à un système particulier (par exemple, les noms d’hôtes et les numéros de port). Ce fichier ne doit _pas_ se trouver dans le contrôle de code source.

1. Ajoutez le code modifié et la configuration partagée au contrôle de code source.

1. Pour supprimer le code php généré et les fichiers de ressources statiques lors du développement, exécutez les commandes suivantes :

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

Après avoir exécuté les commandes pour effacer les ressources, Commerce génère des fichiers de travail.

>[!WARNING]
>
>Faites attention avec l’approche ci-dessus. La suppression du fichier `.htacces` dans le dossier `generated` ou `pub` peut entraîner des problèmes.

### Créer un système

Le système de build compile le code et génère des fichiers d’affichage statiques pour les thèmes enregistrés dans Commerce. Il n’a pas besoin d’une connexion à la base de données Commerce ; seule la base de code Commerce est nécessaire.

Sur votre système de génération :

1. Extrayez le fichier de configuration partagé du contrôle de code source.
1. Utilisez la commande `magento setup:di:compile` pour compiler le code.
1. Utilisez la commande `magento setup:static-content:deploy -f` pour mettre à jour les fichiers d’affichage de fichiers statiques.
1. Vérifiez les mises à jour dans le contrôle de code source.

>[!INFO]
>
>Voir [Stratégies de déploiement pour les fichiers d’affichage statiques](../cli/static-view-file-strategy.md).

### Système de production

Sur votre système de production (c’est-à-dire votre boutique en ligne), vous extrayez les ressources générées et les mises à jour de code du contrôle de code source et définissez des paramètres de configuration sensibles et spécifiques au système à l’aide de la ligne de commande ou des variables d’environnement.

Sur votre système de production :

1. Démarrez le mode de maintenance.
1. Extrayez le code et les mises à jour de configuration du contrôle de code source.
1. Si vous utilisez Adobe Commerce, arrêtez les programmes de travail en file d’attente.
1. Utilisez la commande `magento app:config:import` pour importer les modifications de configuration dans le système d’exploitation.
1. Si vous avez installé des composants qui ont modifié le schéma de la base de données, exécutez `magento setup:upgrade --keep-generated` pour mettre à jour le schéma et les données de la base de données, en préservant les fichiers statiques générés.
1. Pour définir des paramètres spécifiques au système, utilisez la commande `magento config:set` ou des variables d’environnement.
1. Pour définir des paramètres sensibles, utilisez la commande `magento config:sensitive:set` ou des variables d’environnement.
1. Nettoyez le cache (opération également appelée _vidage_).
1. Terminez le mode de maintenance.

## Commandes de gestion de la configuration

Nous fournissons les commandes suivantes pour vous aider à gérer la configuration :

- [`magento app:config:dump`](../cli/export-configuration.md) d’écrire les paramètres de configuration d’administration dans `config.php` et `env.php` (sauf pour les paramètres sensibles)
- [`magento config:set`](../cli/set-configuration-values.md) pour définir les valeurs des paramètres spécifiques au système sur le système d’exploitation.

  Utilisez l’option `--lock` facultative pour verrouiller l’option dans l’Administration (c’est-à-dire rendre le paramètre non modifiable). Si un paramètre est déjà verrouillé, utilisez l’option `--lock` pour le modifier.

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) de définir les valeurs des paramètres sensibles sur le système d’exploitation.
- [`magento app:config:import`](../cli/import-configuration.md) d’importer les modifications de configuration de `config.php` et `env.php` dans le système d’exploitation.

## Exemples de gestion de la configuration

Cette section présente des exemples de gestion de la configuration afin que vous puissiez voir comment les modifications sont apportées à `config.php` et `env.php`.

### Modifier le paramètre régional par défaut

Cette section affiche la modification apportée à `config.php` lorsque vous modifiez l’unité de poids par défaut à l’aide de l’Administration (**Magasins** > Paramètres > **Configuration** > Général > **Général** > **Options des paramètres régionaux**).

Après avoir effectué la modification dans l’administrateur, exécutez `bin/magento app:config:dump` pour écrire la valeur dans `config.php`. La valeur est écrite dans le tableau `general` sous `locale`, comme le montre le fragment de code suivant d’`config.php` :

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

Cette section aborde la modification des configurations suivantes :

- Ajout d’une vue de site web, de magasin et de magasin (**Magasins** > Paramètres > **Tous les magasins**)
- Modification du domaine d’e-mail par défaut (**Magasins** > Paramètres > **Configuration** > Clients > **Configuration client**)
- Définition du nom d&#39;utilisateur et du mot de passe de l&#39;API PayPal (**Magasins** > Paramètres > **Configuration** > Ventes > **Modes de paiement** > **PayPal** > **Paramètres PayPal obligatoires**)

Une fois la modification effectuée dans l’administration, exécutez `bin/magento app:config:dump` sur votre système de développement. Cette fois, toutes vos modifications ne sont pas écrites dans `config.php` ; en fait, seuls le site web, le magasin et la vue du magasin sont écrits dans ce fichier, comme le montrent les fragments de code ci-dessous.

### config.php

`config.php` contient :

- Modifications apportées à la vue du site web, du magasin et du magasin.
- Paramètres de moteur de recherche non spécifiques au système
- Paramètres PayPal non sensibles
- Commentaires qui vous informent des paramètres sensibles omis dans `config.php`

Tableau `websites` :

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

Tableau `groups` :

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

Tableau `stores` :

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

Tableau `payment` :

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

Le paramètre de configuration par défaut spécifique au système de domaine d’e-mail est écrit dans `app/etc/env.php`.

Les paramètres PayPal ne sont écrits dans aucun fichier car la commande `bin/magento app:config:dump` n&#39;écrit pas de paramètres sensibles. Vous devez définir les paramètres PayPal sur le système d’exploitation à l’aide des commandes suivantes :

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
