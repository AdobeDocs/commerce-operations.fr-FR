---
title: Personnalisation des chemins d’accès aux répertoires de base
description: Utilisez la variable MAGE_DIRS pour définir un tableau de chemins absolus.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# Chemins de répertoire de base

La variable d’environnement `MAGE_DIRS` vous permet de spécifier des chemins d’accès de répertoire de base personnalisés et des fragments d’URL de base utilisés par l’application Commerce pour créer des chemins d’accès absolus vers différents fichiers ou pour générer des URL.

## Définir MAGE_DIRS

Spécifiez un tableau associatif où les clés sont des constantes de [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] et où les valeurs sont des chemins absolus de répertoires ou de leurs chemins d’URL, respectivement.

Vous pouvez définir `MAGE_DIRS` de l’une des manières suivantes :

- [Définir la valeur des paramètres de bootstrap](../bootstrap/set-parameters.md)
- Utilisez un script de point d’entrée personnalisé tel que le suivant :

  ```php
  <?php
  /**
   * Copyright © Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
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

L’exemple précédent définit les chemins pour les répertoires `[cache]` et `[media]` sur `/mnt/nfs/cache` et `/mnt/nfs/media`, respectivement.

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
