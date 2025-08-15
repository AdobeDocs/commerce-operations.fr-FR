---
title: Bonnes pratiques en matière de gestion des exceptions
description: Découvrez les méthodes recommandées pour la journalisation des exceptions lors du développement de projets Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# Bonnes pratiques en matière de gestion des exceptions

Si une exception n’est pas écrite dans le fichier `exception.log` avec le modèle d’exception comme contexte, elle n’est pas reconnue et analysée correctement dans New Relic ou tout autre stockage de journal compatible avec un monologue PSR-3. La journalisation d’une partie seulement de l’exception (ou de l’enregistrer dans le mauvais fichier) entraîne des bogues en production lorsque les exceptions sont ignorées.

## Gestion correcte des exceptions

La liste de contrôle suivante fournit des exemples illustrant la gestion correcte des exceptions.

### ![correct](../../../assets/yes.svg) Écrire dans le journal des exceptions

Écrivez dans le journal des exceptions selon le modèle suivant, quelles que soient les autres actions, sauf s’il y a une bonne raison de ne pas le faire.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

Cette approche enregistre automatiquement le `$e->getMessage` dans le message du journal et l’objet `$e` dans le contexte, conformément à la norme de contexte [PSR-3](https://www.php-fig.org/psr/psr-3/#13-context). Cette opération s’effectue en `\Magento\Framework\Logger\Monolog::addRecord`.

### ![correct](../../../assets/yes.svg) Désactiver le son des signaux

Désactivez le son des signaux en ne consignant pas les exceptions qui font partie du flux d’opérations prévu. Aucune action de suivi n’est nécessaire lorsque l’exception est rencontrée. Il n’est donc pas nécessaire de la consigner et de l’analyser lorsqu’elle se produit. Ajoutez un commentaire indiquant la raison pour laquelle les signaux sont désactivés et que cela est intentionnel. Combiner avec `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![correct](../../../assets/yes.svg) rétrograder des exceptions

Rétrogradez les exceptions en suivant la norme contextuelle [PSR-3](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![correct](../../../assets/yes.svg) La journalisation vient toujours en premier

En règle générale, la journalisation est toujours prioritaire dans le code afin d’éviter les cas où une autre exception ou une erreur fatale est générée avant d’écrire dans le journal.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![correct](../../../assets/yes.svg) Consigner les messages et la trace complète des exceptions

Enregistrez les messages et l’ensemble de la trace des exceptions en suivant la norme contextuelle [PSR-3](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## Gestion des exceptions incorrecte

Les exemples suivants montrent une gestion incorrecte des exceptions.

### ![incorrect](../../../assets/no.svg) Logique avant la journalisation

La logique avant la journalisation peut entraîner une autre exception ou une erreur irrécupérable, ce qui empêche la journalisation de l’exception et doit être remplacé par [exemple correct](#logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![incorrect](../../../assets/no.svg) `catch` vide

Les blocs de `catch` vides peuvent être un signe de désactivation involontaire et doivent être remplacés par l’exemple [ correct](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![incorrect](../../../assets/no.svg) localisation double

Si l’exception localisée capturée n’est pas encore traduite, résolvez le problème à l’endroit où l’exception est renvoyée la première fois.

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![incorrect](../../../assets/no.svg) consigne les messages et trace dans différents fichiers journaux

Le code suivant consigne incorrectement la trace de pile pour une exception sous la forme d’une chaîne dans un fichier journal.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

Cette approche introduit des sauts de ligne dans le message, qui n’est pas conforme au RSP-3. L’exception , y compris la trace de la pile, doit faire partie du contexte du message pour s’assurer qu’il est correctement enregistré avec le message dans New Relic ou un autre stockage de journaux compatible avec les monologues PSR-3.

Corrigez ce problème en remplaçant le code par les exemples appropriés indiqués dans [Écrire dans le journal des exceptions](#write-to-the-exception-log) ou [Rétrograder des exceptions](#downgrade-exceptions).

### ![incorrect](../../../assets/no.svg) rétrograder des exceptions sans contexte

L’exception est rétrogradée vers une erreur, qui ne permet pas de transmettre un objet, mais uniquement une chaîne, d’où la `getMessage()`. Cela entraîne la perte de la trace et doit être remplacé par les exemples corrects affichés dans [Écrire dans le journal des exceptions](#write-to-the-exception-log) ou [Rétrograder des exceptions](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![incorrect](../../../assets/no.svg) consignez uniquement le message dans le journal des exceptions

Au lieu de transmettre l’objet `$e`, seul `$e->getMessage()` est transmis. Cela entraîne la perte de la trace et doit être remplacé par les exemples corrects affichés [Écrire dans le journal des exceptions](#write-to-the-exception-log) ou [Rétrograder des exceptions](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![incorrect](../../../assets/no.svg) `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch` manquant

L’omission de la ligne `phpcs:ignore` déclenche un avertissement dans PHPCS et ne doit pas transmettre votre CI. Cette valeur doit être remplacée par l’exemple correct illustré dans [Désactiver le son](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
