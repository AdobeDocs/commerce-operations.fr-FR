---
title: Afficher ou modifier l’URI d’administration
description: Pour afficher et modifier l’URI de votre application Adobe Commerce Admin, procédez comme suit.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Afficher ou modifier l’URI d’administration

Avant d’exécuter cette commande, vous devez [créer ou mettre à jour la configuration de déploiement](deployment.md).

## Afficher l’URI d’administrateur

Cette section explique comment utiliser la ligne de commande pour afficher l’identifiant de ressource uniforme d’administration ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

Options de commande :

```bash
bin/magento info:adminuri
```

Voici un exemple de résultat :

```
Admin Panel URI: /admin_1wgrah
```

Vous pouvez également afficher l’URI d’administrateur dans `<magento_root>/app/etc/env.php`. Voici un extrait de code :

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Modifier l’URL d’administration

Pour modifier l’URI d’administration, utilisez la commande [`magento setup:config:set`](deployment.md) .
