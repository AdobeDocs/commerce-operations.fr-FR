---
title: paramètres PHP
description: Suivez ces étapes pour installer les extensions PHP requises et configurer les paramètres PHP requis pour les installations sur site d’Adobe Commerce et de Magento Open Source.
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: 87e3109518fc06c655a3fc9446e2ecd648775da1
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---


# paramètres PHP

Cette rubrique explique comment définir les options PHP requises.

>[!NOTE]
>
>La dernière version d’Adobe Commerce et de Magento Open Source requiert au minimum PHP 8.1. Voir [configuration requise](../system-requirements.md) pour toutes les versions prises en charge de PHP.

Pour obtenir des conseils sur la configuration du cloud, voir [paramètres PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) dans le _Commerce sur l’infrastructure cloud_ guide.

## Contrôle de processus PHP

{{php-process-control}}

## Vérifier que PHP est installé

PHP est installé par défaut sur la plupart des distributions Linux. Cette rubrique suppose que vous avez déjà installé PHP. Pour vérifier si PHP est installé, saisissez ce qui suit sur la ligne de commande :

```bash
php -v
```

Si PHP est installé, un message similaire à celui-ci s’affiche :

```terminal
PHP 8.1.2-1ubuntu2.14 (cli) (built: Aug 18 2023 11:41:11) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.14, Copyright (c), by Zend Technologies
```

Si PHP n&#39;est pas installé (ou nécessite une mise à niveau), installez-le en suivant les instructions de votre distribution Linux.

## Vérification des extensions installées

Adobe Commerce et Magento Open Source nécessitent certaines extensions PHP. Les listes suivantes spécifient les extensions requises pour chaque édition de Commerce. Les listes sont générées automatiquement à partir d’un déploiement exécutant la dernière version de chaque édition.

{{$include /help/_includes/templated/php-extensions.md}}

Pour vérifier les extensions installées :

1. Liste des modules installés.

   ```bash
   php -m
   ```

1. Vérifiez que toutes les extensions requises sont installées.
1. Ajoutez tous les modules manquants en utilisant le même workflow utilisé pour l&#39;installation de PHP.

## Vérifier les paramètres PHP

>[!WARNING]
>
>Si vous utilisez PHP 7.4.20, définissez `pcre.jit=0` dans votre `php.ini` fichier . Cela contourne le PHP [bug](https://bugs.php.net/bug.php?id=81101) qui empêche le chargement de CSS.

- Définissez le fuseau horaire du système pour PHP. Dans le cas contraire, des erreurs telles que l’affichage suivant lors de l’installation et des opérations liées à l’heure telles que cron risquent de ne pas fonctionner :

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Définissez la limite de mémoire PHP.

  Adobe recommande ce qui suit :

   - Compilation du code ou déploiement de ressources statiques, `1G`
   - Débogage, `2G`
   - Tests, `~3-4G`

- Augmenter les valeurs du PHP `realpath_cache_size` et `realpath_cache_ttl` aux paramètres recommandés :

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  Ces paramètres permettent aux processus PHP de mettre en cache les chemins d’accès aux fichiers au lieu de les rechercher au chargement de la page. Voir [Optimisation des performances](https://www.php.net/manual/en/ini.core.php) dans la documentation PHP.

- Activer [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments), qui est requis pour Adobe Commerce et Magento Open Source 2.1 et versions ultérieures.

  Adobe recommande d’activer la fonction [OPcache PHP](https://www.php.net/manual/en/book.opcache.php) pour des raisons de performances. Le OPcache est activé dans de nombreuses distributions PHP.

  Adobe Commerce et Magento Open Source 2.1 et versions ultérieures utilisent des commentaires de code PHP pour la génération de code.

>[!NOTE]
>
>Pour éviter tout problème lors de l’installation et de la mise à niveau, Adobe recommande vivement d’appliquer les mêmes paramètres PHP à la configuration de la ligne de commande PHP et à la configuration du module externe de serveur Web PHP. Pour plus d’informations, voir la section suivante.

## Recherche de fichiers de configuration PHP

Cette section explique comment trouver les fichiers de configuration nécessaires pour mettre à jour les paramètres requis.

### Rechercher `php.ini` fichier de configuration

Pour trouver la configuration du serveur web, exécutez un [`phpinfo.php` fichier](optional-software.md#create-phpinfophp) dans votre navigateur web et recherchez les `Loaded Configuration File` comme suit :

![page d’informations PHP](../../assets/installation/config_phpini-webserver.png)

Pour localiser la configuration de ligne de commande PHP, saisissez

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Si vous en avez un seul `php.ini` modifiez ce fichier. Si vous avez deux `php.ini` fichiers, modifier *both* fichiers . Si vous ne le faites pas, les performances risquent d’être imprévisibles.

### Recherche des paramètres de configuration OPcache

Les paramètres du OPcache PHP sont généralement situés dans la variable `php.ini` ou `opcache.ini`. L’emplacement peut dépendre de votre système d’exploitation et de la version PHP. Le fichier de configuration OPcache peut comporter une `opcache` ou des paramètres tels que `opcache.enable`.

Suivez les instructions ci-dessous pour le trouver :

- Serveur web Apache :

  Pour Ubuntu avec Apache, les paramètres OPcache se trouvent généralement dans la variable `php.ini` fichier .

  Pour CentOS avec Apache ou nginx, les paramètres OPcache se trouvent généralement dans `/etc/php.d/opcache.ini`

  Dans le cas contraire, utilisez la commande suivante pour la localiser :

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- Serveur web nginx avec PHP-FPM : `/etc/php/8.1/fpm/php.ini`

Si vous en avez plusieurs `opcache.ini`, modifiez-les tous.

## Comment définir les options PHP

Pour définir les options PHP :

1. Ouvrez une `php.ini` dans un éditeur de texte.
1. Localisez le fuseau horaire de votre serveur dans la [paramètres de fuseau horaire](https://www.php.net/manual/en/timezones.php)
1. Recherchez le paramètre suivant et annulez sa mise en commentaire si nécessaire :

   ```conf
   date.timezone =
   ```

1. Ajoutez le paramètre de fuseau horaire trouvé à l’étape 2.

1. Modifier la valeur de `memory_limit` à l’une des valeurs recommandées au début de cette section.

   Par exemple,

   ```conf
   memory_limit=2G
   ```

1. Ajoutez ou mettez à jour la variable `realpath_cache` configuration pour correspondre aux valeurs suivantes :

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

1. Ouvrez l’autre `php.ini` (s’ils sont différents) et apportez les mêmes modifications.

## Définition des options OPcache

Pour définir `opcache.ini` options :

1. Ouvrez votre fichier de configuration OPcache dans un éditeur de texte :

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/8.1/fpm/php.ini` (serveur web nginx (CentOS ou Ubuntu)

1. Localiser `opcache.save_comments` et décommentez-le si nécessaire.
1. Assurez-vous que sa valeur est définie sur `1`.
1. Enregistrez vos modifications et quittez l’éditeur de texte.
1. Redémarrez votre serveur web :

   - Apache, Ubuntu : `service apache2 restart`
   - Apache, CentOS : `service httpd restart`
   - nginx, Ubuntu et CentOS : `service nginx restart`

## Dépannage

Pour obtenir de l’aide sur la résolution des problèmes liés à PHP, reportez-vous aux articles suivants du support Adobe Commerce :

- [Erreur de version PHP ou erreur 404 lors de l’accès à Adobe Commerce dans un navigateur.](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [erreurs de paramètres PHP](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [L’extension de chiffrement PHP n’est pas installée correctement](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [Problèmes de vérification de l’état de préparation des versions PHP](https://support.magento.com/hc/en-us/articles/360033546411)
- [Erreurs et solutions fatales PHP courantes](https://support.magento.com/hc/en-us/articles/360030568432)
