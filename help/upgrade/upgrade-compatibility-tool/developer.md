---
title: '[!DNL Upgrade Compatibility Tool] Informations sur les développeurs'
description: Personnalisez le [!DNL Upgrade Compatibility Tool] à l’aide de l’intégration de l’index d’API.
source-git-commit: 3d9a721e33621b78f03f16b932a1ba2904ae4010
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] informations sur les développeurs

Cette rubrique contient des informations destinées aux développeurs qui travaillent en étroite collaboration avec le code Adobe Commerce et souhaitent en savoir plus sur les [!DNL Upgrade Compatibility Tool]. Vous pouvez utiliser ces connaissances pour personnaliser les composants de l’outil.

## Intégration de l’index d’API Adobe Commerce

L’intégration de l’index d’API Adobe Commerce est une solution d’intégration interne qui comprend un ensemble d’outils permettant d’explorer les extensions Adobe Commerce développées par Adobe, les partenaires Adobe Commerce et les fournisseurs tiers sur la base d’une analyse de code statique.

L’intégration à l’index de l’API Adobe Commerce se fait par :

`sut\Domain\MRay\MRayInterface`

Elle est mise en oeuvre par le biais de la variable `config/services.yaml` fichier . Sa valeur détermine où la réponse des méthodes `api()` et `modules()` vient de .

Modifiez ce fichier pour personnaliser la réponse en fonction de votre installation. Remplacer la valeur affectée à `sut\Domain\MRay\MRayInterface`:

### Exemple de valeur personnalisée

`sut\Domain\MRay\MRayInterface : "@sut_mray_mock"`

Dans l’exemple précédent, la variable [!DNL Upgrade Compatibility Tool] uses `@sut_mray_mock` comme la propriété `MRayInterface` implémentation. Les réponses des `api()` et `modules()` Les méthodes proviennent des fichiers suivants :

- `dev/mray_mock_files/api.json`
- `dev/mray_mock_files/modules.json`

>[!NOTE]
>
>Lorsque vous modifiez la variable `services.yaml` , supprimez le fichier `var/cache/` pour appliquer correctement les modifications.

## Test unitaire

Pour exécuter les tests unitaires, exécutez l’une des commandes suivantes :

- `vendor/bin/phpunit tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist --testsuite=unit-tests`

## Test d’intégration

Pour exécuter les tests d’intégration, exécutez l’une des commandes suivantes :

- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist tests/integration`
- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist --testsuite=integration-tests`

## Test d’acceptation

1. Avant d’exécuter des tests d’acceptation, vous devez définir l’URL Adobe Commerce dans la variable `phpunit` fichier de configuration.
1. Copier la valeur par défaut `tests/acceptance/phpunit.xml` (sans le suffixe .dist).
1. Modifiez la variable `TESTS_BASE_URL` pour pointer vers l’URL Adobe Commerce que vous souhaitez tester.
1. Pour exécuter les tests d’acceptation, exécutez l’une des commandes suivantes :

   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml tests/acceptance`
   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml --testsuite=acceptance-tests`

## Test unitaire GraphQL et analyse du code ESLint

### Conditions

>[!NOTE]
>
>Vous devez disposer de Node.js sur votre système, voir [Documentation Node.js](https://nodejs.dev/learn/how-to-install-nodejs).

Les instructions suivantes concernent les systèmes MacOS :

1. Ouvrez un terminal et accédez au répertoire racine du projet.
1. Installer les dépendances de projet :

   ```bash
   npm install
   ```

### Test unitaire GraphQL

Le [Jest](https://jestjs.io/docs/getting-started) a été utilisé pour créer les tests unitaires JS suivants :

Les tests sont à l’intérieur `dev/tests/Js`.

Les schémas de chaîne à tester se trouvent à l’intérieur. `dev/tests/Acceptance/_files/graphql_schemas`.

Exécution de tests unitaires ; `jest` comme suit :

```bash
./node_modules/.bin/jest --verbose --rootDir=dev/tests/Js/
```

### Analyse du code ESLint

[ESLint](https://eslint.org/docs/user-guide/getting-started) est un outil d’analyse de code statique permettant d’identifier les schémas problématiques trouvés dans le code JavaScript, dans le but de rendre le code plus cohérent et d’éviter les bogues.

Exécuter `eslint` analyse du code comme suit :

```bash
./node_modules/.bin/eslint -c dev/tests/Static/.eslintrc --rulesdir vendor/magento/magento-coding-standard/eslint/rules path/to/analyse
```

## Score de complexité

Le **score de complexité** est une figure qui indique la difficulté d’une mise à niveau de la version actuelle vers la nouvelle version. Les nombres inférieurs indiquent des mises à niveau plus faciles.

>[!NOTE]
>
>Les scores de complexité sont compris entre 0 et ∞.

Ce score est basé sur les résultats extraits de l&#39;analyse :

- Nombre de problèmes identifiés
- Gravité des problèmes identifiés

Le [!DNL Upgrade Compatibility Tool] calcule ce score en fonction de la formule de score de complexité ci-dessous.

### Formule de score de complexité

`Complexity Score = (Critical issues * 3) + (Errors *2) + Warnings`

>[!WARNING]
>
>Il s’agit de valeurs absolues.
