---
title: Exécution de tests unitaires
description: Exécutez des tests unitaires définis dans la base de code Adobe Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Exécution de tests unitaires

{{file-system-owner}}

Cette commande exécute un ensemble de tests définis dans la base de code Commerce 2. Vous pouvez exécuter tous les tests ou tests que vous avez sélectionnés. Chaque fois qu’un type non pris en charge est spécifié, le programme s’arrête et répertorie tous les types disponibles. Après l’exécution, un rapport détaillé affiche l’exécution et les résultats du test.

## Conditions préalables

Avant d’exécuter cette commande, procédez comme suit : _must_ être vrai :

- Le `Magento_Developer` doit être activé. Vous pouvez l’activer comme suit :

   ```bash
   bin/magento module:enable [--force] Magento_Developer
   ```

   Utilisez la variable `--force` uniquement si nécessaire.

- Votre système doit être configuré pour exécuter les tests souhaités.

Par exemple, pour exécuter des tests d’intégration, vous devez copier `dev/tests/integration/etc/install-config-mysql.php.dist` to `dev/tests/integration/etc/install-config-mysql.php` et modifiez-la pour l’adapter à votre environnement.

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

```terminal
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Par exemple, pour exécuter des tests d’intégration :

```bash
bin/magento dev:tests:run integration
```
