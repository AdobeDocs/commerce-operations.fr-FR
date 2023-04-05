---
title: Affichage ou modification de l’URI d’administration
description: Suivez ces étapes pour afficher et modifier l’URI de votre application d’administration Adobe Commerce ou Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Affichage ou modification de l’URI d’administration

Avant d’exécuter cette commande, vous devez [Création ou mise à jour de la configuration du déploiement](deployment.md).

## Affichage de l’URI d’administration

Cette section explique comment utiliser la ligne de commande pour afficher l’ identifiant de ressource Uniform d’administration ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

Options de commande :

```bash
bin/magento info:adminuri
```

Voici un exemple de résultat :

```terminal
Admin Panel URI: /admin_1wgrah
```

Vous pouvez également afficher l’URI d’administration dans `<magento_root>/app/etc/env.php`. Voici un extrait de code :

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Modification de l’URL d’administration

Pour modifier l’URI d’administration, utilisez la méthode [`magento setup:config:set`](deployment.md) .
