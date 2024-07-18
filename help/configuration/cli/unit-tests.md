---
title: Exécution de tests unitaires
description: Exécutez des tests unitaires définis dans la base de code Adobe Commerce.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Exécution de tests unitaires

{{file-system-owner}}

Cette commande exécute un ensemble de tests définis dans la base de code Commerce 2. Vous pouvez exécuter tous les tests ou tests que vous avez sélectionnés. Chaque fois qu’un type non pris en charge est spécifié, le programme s’arrête et répertorie tous les types disponibles. Après l’exécution, un rapport détaillé affiche l’exécution et les résultats du test.

## Conditions préalables

Avant d’exécuter cette commande, les _must_ suivants doivent être vrais :

- Le module `Magento_Developer` doit être activé. Vous pouvez l’activer comme suit :

  ```bash
  bin/magento module:enable [--force] Magento_Developer
  ```

  Utilisez l’option `--force` uniquement si nécessaire.

- Votre système doit être configuré pour exécuter les tests souhaités.

Par exemple, pour exécuter des tests d’intégration, vous devez copier `dev/tests/integration/etc/install-config-mysql.php.dist` vers `dev/tests/integration/etc/install-config-mysql.php` et le modifier pour l’adapter à votre environnement.

## Exécution de tests

Utilisation des commandes :

```bash
bin/magento dev:tests:run <test>
```

Pour répertorier les types de test disponibles :

```bash
bin/magento dev:tests:run --help
```

Exemple de retour :

```
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Par exemple, pour exécuter des tests d’intégration :

```bash
bin/magento dev:tests:run integration
```
