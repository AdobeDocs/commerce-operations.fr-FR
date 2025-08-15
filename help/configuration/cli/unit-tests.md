---
title: Exécuter des tests unitaires
description: Exécutez des tests unitaires définis dans la base de code d’Adobe Commerce.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Exécuter des tests unitaires

{{file-system-owner}}

Cette commande exécute un ensemble de tests définis dans la base de code Commerce 2. Vous pouvez exécuter tous les tests ou les tests que vous sélectionnez. Lorsqu’un type non pris en charge est spécifié, le programme s’arrête et répertorie tous les types disponibles. Une fois l’exécution terminée, un rapport détaillé affiche l’exécution du test et ses résultats.

## Conditions préalables

Avant d’exécuter cette commande, la valeur suivante _doit_ doit être vraie :

- Le module `Magento_Developer` doit être activé. Vous pouvez l’activer comme suit :

  ```bash
  bin/magento module:enable [--force] Magento_Developer
  ```

  N’utilisez l’option `--force` que si nécessaire.

- Votre système doit être configuré pour exécuter les tests souhaités.

Par exemple, pour exécuter des tests d’intégration, vous devez copier le `dev/tests/integration/etc/install-config-mysql.php.dist` dans `dev/tests/integration/etc/install-config-mysql.php` et le modifier en fonction de votre environnement.

## Exécution des tests

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
