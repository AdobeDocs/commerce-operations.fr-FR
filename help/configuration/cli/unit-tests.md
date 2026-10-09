---
title: Exécuter des tests unitaires
description: Découvrez comment exécuter des tests unitaires définis dans la base de code Adobe Commerce. Découvrez les commandes de test, les options d’exécution et le compte rendu des performances.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%
---
# Exécuter des tests unitaires

{{file-system-owner}}

Cette commande exécute un ensemble de tests définis dans la base de code Commerce 2. Vous pouvez exécuter tous les tests ou les tests que vous sélectionnez. Lorsqu’un type non pris en charge est spécifié, le programme s’arrête et répertorie tous les types disponibles. Une fois l’exécution terminée, un rapport détaillé affiche l’exécution du test et ses résultats.

## Conditions préalables

Avant d’exécuter cette commande, la valeur suivante _doit_ doit être vraie :

- Le module `Magento_Developer` doit être activé. Vous pouvez l’activer comme suit :

  ```shell
  bin/magento module:enable [--force] Magento_Developer
  ```

  N’utilisez l’option `--force` que si nécessaire.

- Votre système doit être configuré pour exécuter les tests souhaités.

Par exemple, pour exécuter des tests d’intégration, vous devez copier le `dev/tests/integration/etc/install-config-mysql.php.dist` dans `dev/tests/integration/etc/install-config-mysql.php` et le modifier en fonction de votre environnement.

## Exécution des tests

Utilisation des commandes :

```shell
bin/magento dev:tests:run <test>
```

Pour répertorier les types de test disponibles :

```shell
bin/magento dev:tests:run --help
```

Exemple de retour :

```text
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Par exemple, pour exécuter des tests d’intégration :

```shell
bin/magento dev:tests:run integration
```
