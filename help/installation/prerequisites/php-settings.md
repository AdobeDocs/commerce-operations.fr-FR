---
title: Paramètres PHP
description: Suivez ces étapes pour installer les extensions PHP requises et configurer les paramètres PHP requis pour les installations sur site d’Adobe Commerce.
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 0%

---


# Paramètres PHP

Cette rubrique explique comment définir les options PHP requises.

>[!NOTE]
>
>La dernière version d&#39;Adobe Commerce requiert au minimum PHP 8.1. Voir [configuration requise](../system-requirements.md) pour toutes les versions supportées de PHP.

Pour obtenir des conseils sur la configuration du cloud, consultez [Paramètres PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html?lang=fr) dans le guide _Commerce sur les infrastructures cloud_.

## Contrôle de processus PHP

{{php-process-control}}

## Vérifier que PHP est installé

PHP est installé par défaut sur la plupart des distributions Linux. Cette rubrique suppose que vous avez déjà installé PHP. Pour vérifier si PHP est installé, saisissez la ligne de commande suivante :

```bash
php -v
```

Si PHP est installé, un message similaire à celui-ci s&#39;affiche :

```
PHP 8.1.2-1ubuntu2.14 (cli) (built: Aug 18 2023 11:41:11) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.14, Copyright (c), by Zend Technologies
```

Si PHP n&#39;est pas installé (ou nécessite une mise à niveau), installez-le en suivant les instructions de votre distribution Linux.

## Vérification des extensions installées

Adobe Commerce requiert certaines extensions PHP. Les listes suivantes spécifient les extensions requises pour chaque édition de Commerce. Les listes sont générées automatiquement à partir d’un déploiement exécutant la dernière version de chaque édition.

{{$include /help/_includes/templated/php-extensions.md}}

Pour vérifier les extensions installées :

1. Liste des modules installés.

   ```bash
   php -m
   ```

1. Vérifiez que toutes les extensions requises sont installées.
1. Ajoutez les modules manquants en utilisant le même workflow que celui utilisé pour installer PHP.

## Vérifier les paramètres PHP

>[!WARNING]
>
>Si vous utilisez PHP 7.4.20, `pcre.jit=0` dans votre fichier `php.ini`. Cela évite un bug PHP [bug](https://bugs.php.net/bug.php?id=81101) qui empêche le chargement de CSS.

- Réglez le fuseau horaire système pour PHP ; sinon, les erreurs comme celle-ci s&#39;affichent pendant l&#39;installation et les opérations liées à l&#39;heure comme cron risquent de ne pas fonctionner :

```
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Définissez la limite de mémoire PHP.

  Adobe recommande ce qui suit :

   - Compilation du code pour déployer des ressources statiques, `1G`
   - Débogage, `2G`
   - Test, `~3-4G`

- Augmentez les valeurs des `realpath_cache_size` PHP et `realpath_cache_ttl` aux paramètres recommandés :

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  Ces paramètres permettent aux processus PHP de mettre en cache les chemins vers les fichiers au lieu de les rechercher au chargement de la page. Voir [Réglage des performances](https://www.php.net/manual/en/ini.core.php) dans la documentation PHP.

- Activez [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments), qui est obligatoire pour Adobe Commerce 2.1 et les versions ultérieures.

  Adobe recommande d’activer le [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) pour des raisons de performances. Le cache OP est activé dans de nombreuses distributions PHP.

  Adobe Commerce 2.1 et versions ultérieures utilisent les commentaires de code PHP pour la génération de code.

>[!NOTE]
>
>Pour éviter tout problème lors de l&#39;installation et de la mise à niveau, Adobe recommande vivement d&#39;appliquer les mêmes paramètres PHP à la fois à la configuration de ligne de commande PHP et à la configuration du plug-in du serveur web PHP. Pour plus d’informations, voir la section suivante.

## Rechercher les fichiers de configuration PHP

Cette section explique comment trouver les fichiers de configuration nécessaires pour mettre à jour les paramètres requis.

### Rechercher `php.ini` fichier de configuration

Pour trouver la configuration du serveur web, exécutez un fichier [`phpinfo.php`](optional-software.md#create-phpinfophp) dans votre navigateur web, puis recherchez le `Loaded Configuration File` comme suit :

![Page d’informations PHP](../../assets/installation/config_phpini-webserver.png)

Pour localiser la configuration de ligne de commande PHP, saisissez

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Si vous ne disposez que d’un seul fichier `php.ini`, modifiez-le. Si vous disposez de deux fichiers `php.ini`, modifiez *les deux*. Sinon, les performances peuvent être imprévisibles.

### Rechercher les paramètres de configuration OPcache

Les paramètres PHP OPcache sont généralement situés dans `php.ini` ou `opcache.ini`. L&#39;emplacement peut dépendre de votre système d&#39;exploitation et de la version PHP. Le fichier de configuration OPcache peut avoir une section `opcache` ou des paramètres comme `opcache.enable`.

Suivez les instructions suivantes pour le trouver :

- Serveur web Apache :

  Pour Ubuntu avec Apache, les paramètres OPcache se trouvent généralement dans le fichier `php.ini`.

  Pour CentOS avec Apache ou nginx, les paramètres OPcache sont généralement situés dans `/etc/php.d/opcache.ini`

  Dans le cas contraire, la commande suivante permet de le localiser :

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- Serveur web nginx avec PHP-FPM : `/etc/php/8.1/fpm/php.ini`

Si vous disposez de plusieurs `opcache.ini`, modifiez-les toutes.

## Comment définir les options PHP

Pour définir les options PHP :

1. Ouvrez un `php.ini` dans un éditeur de texte.
1. Localisez le fuseau horaire de votre serveur dans les [paramètres de fuseau horaire](https://www.php.net/manual/en/timezones.php) disponibles
1. Recherchez le paramètre suivant et supprimez ses commentaires si nécessaire :

   ```conf
   date.timezone =
   ```

1. Ajoutez le paramètre de fuseau horaire trouvé à l’étape 2.

1. Remplacez la valeur de `memory_limit` par l’une des valeurs recommandées au début de cette section.

   Par exemple,

   ```conf
   memory_limit=2G
   ```

1. Ajoutez ou mettez à jour la configuration `realpath_cache` pour qu’elle corresponde aux valeurs suivantes :

   ```conf
   ;
   ; Increase realpath cache size
   ;
   realpath_cache_size = 10M
   
   ;
   ; Increase realpath cache ttl
   ;
   realpath_cache_ttl = 7200
   ```

1. Enregistrez vos modifications et quittez l’éditeur de texte.

1. Ouvrez les autres `php.ini` (s’ils sont différents) et apportez-y les mêmes modifications.

## Définir les options du cache OP

Pour définir `opcache.ini` options :

1. Ouvrez votre fichier de configuration OPcache dans un éditeur de texte :

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/8.1/fpm/php.ini` (serveur web nginx (CentOS ou Ubuntu))

1. Recherchez `opcache.save_comments` et supprimez les commentaires si nécessaire.
1. Assurez-vous que sa valeur est définie sur `1`.
1. Enregistrez vos modifications et quittez l’éditeur de texte.
1. Redémarrez votre serveur web :

   - Apache, Ubuntu : `service apache2 restart`
   - Apache, CentOS : `service httpd restart`
   - nginx, Ubuntu et CentOS : `service nginx restart`

## Dépannage

Consultez les articles suivants de l’assistance Adobe Commerce pour obtenir de l’aide sur la résolution des problèmes PHP :

- [Erreur de version PHP ou erreur 404 lors de l’accès à Adobe Commerce dans un navigateur](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [Erreurs de paramètres PHP](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [L&#39;extension PHP mcrypt n&#39;est pas installée correctement](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [Problèmes de vérification du niveau de préparation pour les versions PHP](https://support.magento.com/hc/en-us/articles/360033546411)
- [Erreurs et solutions PHP fatales courantes](https://support.magento.com/hc/en-us/articles/360030568432)
