---
title: Personnalisation des chemins d’accès aux répertoires de base
description: Utilisez la variable MAGE_DIRS pour définir un tableau de chemins absolus.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 4116d0983edc797ce42d24e711fb5ecdbf8fdec9
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# Chemins d’accès aux répertoires de base

La variable d’environnement `MAGE_DIRS` vous permet de spécifier des chemins d’accès aux répertoires de base personnalisés ainsi que des fragments d’URL de base utilisés par l’application Commerce pour créer des chemins absolus vers divers fichiers ou pour générer des URL.

## Définir MAGE_DIRS

Spécifiez un tableau associatif où les clés sont des constantes de [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] et les valeurs sont des chemins absolus d’accès aux répertoires ou à leurs chemins d’accès aux URL, respectivement.

Vous pouvez définir `MAGE_DIRS` de l’une des manières suivantes :

- [Définir la valeur des paramètres d’amorçage](../bootstrap/set-parameters.md)
- Utilisez un script de point d’entrée personnalisé tel que :

  ```php
  <?php
  /**
   * Copyright [first year code created] Adobe
   * All Rights Reserved.
   */
  
  use Magento\Framework\App\Bootstrap;
  use Magento\Framework\App\Filesystem\DirectoryList;
  use Magento\Framework\App\Http;
  
  require __DIR__ . '/app/bootstrap.php';
  $params = $_SERVER;
  $params[Bootstrap::INIT_PARAM_FILESYSTEM_DIR_PATHS] = [
       DirectoryList::PUB => [DirectoryList::URL_PATH => ''],
       DirectoryList::MEDIA => [DirectoryList::PATH => '/mnt/nfs/media', DirectoryList::URL_PATH => ''],
       DirectoryList::STATIC_VIEW => [DirectoryList::URL_PATH => 'static'],
       DirectoryList::UPLOAD => [DirectoryList::URL_PATH => '/mnt/nfs/media/upload'],
       DirectoryList::CACHE => [DirectoryList::PATH => '/mnt/nfs/cache'],
  ];
  $bootstrap = Bootstrap::create(BP, $params);
  /** @var Http $app */
  $app = $bootstrap->createApplication(Http::class);
  $bootstrap->run($app);
  ```

L’exemple précédent définit les chemins d’accès pour les répertoires `[cache]` et `[media]` sur `/mnt/nfs/cache` et `/mnt/nfs/media`, respectivement.

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
