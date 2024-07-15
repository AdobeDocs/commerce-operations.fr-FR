---
title: Bonnes pratiques relatives à la gestion des exceptions
description: Découvrez les méthodes recommandées pour consigner les exceptions lors du développement de projets Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# Bonnes pratiques relatives à la gestion des exceptions

Si une exception n’est pas écrite dans le fichier `exception.log` avec le modèle d’exception comme contexte, elle n’est pas reconnue et analysée correctement dans New Relic ou dans un autre stockage de journal compatible avec le format PSR-3. La journalisation d’une partie seulement de l’exception (ou la journalisation dans un fichier incorrect) entraîne des bogues en production lorsque les exceptions sont négligées.

## Correction de la gestion des exceptions

La liste de contrôle suivante fournit des exemples pour démontrer la gestion correcte des exceptions.

### ![correct](../../../assets/yes.svg) Écriture dans le journal des exceptions

Écrivez dans le journal des exceptions à l’aide du modèle suivant, indépendamment des autres actions, sauf s’il y a une raison irréfutable de ne pas le faire.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

Cette approche enregistre automatiquement le `$e->getMessage` dans le message du journal et l’objet `$e` dans le contexte, en suivant la [norme contextuelle PSR-3](https://www.php-fig.org/psr/psr-3/#13-context). Cette opération est effectuée dans `\Magento\Framework\Logger\Monolog::addRecord`.

### ![correct](../../../assets/yes.svg) Signaux muets

Mutez les signaux en ne consignant pas les exceptions qui font partie du flux d’opérations prévu. Aucune action de suivi n’est nécessaire lorsque l’exception est rencontrée. Il n’est donc pas nécessaire de la consigner et de l’analyser lorsqu’elle se produit. Ajoutez un commentaire indiquant la raison de l’arrêt des signaux et le caractère intentionnel de ce dernier. Combinez avec `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![correct](../../../assets/yes.svg) Exceptions de rétrogradation

Réduisez les exceptions en suivant la [norme contextuelle PSR-3](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![correct](../../../assets/yes.svg) La journalisation est toujours la première

La journalisation est une bonne pratique qui s’affiche toujours en premier dans le code afin d’éviter les cas où une autre exception ou erreur fatale est générée avant d’écrire dans le journal.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![correct](../../../assets/yes.svg) Enregistrer les messages et toute la trace de l&#39;exception

Consignez les messages et la trace complète des exceptions en suivant la [norme contextuelle PSR-3](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## Gestion des exceptions incorrecte

Les exemples suivants montrent une gestion incorrecte des exceptions.

### ![incorrect](../../../assets/no.svg) Logique avant journalisation

La logique avant la journalisation peut entraîner une autre exception ou une erreur fatale, qui empêche l’enregistrement de l’exception et doit être remplacée par [exemple correct](#logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![incorrect](../../../assets/no.svg) vide `catch`

Les blocs `catch` vides peuvent être un signe d’arrêt involontaire et doivent être remplacés par l’ [exemple correct](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![incorrect](../../../assets/no.svg) Double localisation

Si l’exception localisée capturée n’est pas encore traduite, résolvez le problème à l’emplacement où l’exception est générée la première fois.

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![incorrect](../../../assets/no.svg) Messages du journal et trace dans différents fichiers journaux

Le code suivant consigne incorrectement la trace de la pile pour une exception en tant que chaîne à un fichier journal.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

Cette approche introduit des sauts de ligne dans le message, qui n’est pas conforme au PSR-3. L’exception, y compris la trace de la pile, doit faire partie du contexte du message pour s’assurer qu’il est enregistré correctement avec le message dans New Relic ou dans un autre stockage de journal compatible avec le format PSR-3.

Réparez ce problème en remplaçant le code en suivant les exemples corrects présentés dans la section [Écrire dans le journal des exceptions](#write-to-the-exception-log) ou [Rétrograder les exceptions](#downgrade-exceptions).

### ![incorrect](../../../assets/no.svg) Rétrogradation des exceptions sans contexte

L’exception est dégradée en erreur, ce qui ne permet pas de transmettre un objet, mais seulement une chaîne, d’où l’ `getMessage()`. Cela entraîne la perte de la trace et doit être remplacé par les exemples corrects présentés dans la section [Écrire au journal des exceptions](#write-to-the-exception-log) ou [Rétrograder les exceptions](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![incorrect](../../../assets/no.svg) Consigne uniquement le message dans le journal des exceptions

Au lieu de transmettre l’objet `$e`, seul `$e->getMessage()` est transmis. Cela entraîne la perte de la trace et doit être remplacé par les exemples corrects affichés [Écrire dans le journal des exceptions](#write-to-the-exception-log) ou [Rétrograder les exceptions](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![incorrect](../../../assets/no.svg) Absente `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

Si vous omettez la ligne `phpcs:ignore`, un avertissement s’affiche dans le PHPCS et vous ne devriez pas transmettre votre CI. Ceci doit être remplacé par l’exemple correct illustré dans [Signaux muets](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
