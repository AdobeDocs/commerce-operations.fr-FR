---
title: Bonnes pratiques relatives à la gestion des exceptions
description: Découvrez les méthodes recommandées pour consigner les exceptions lors du développement de projets Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 94d37b6a95cae93f465daf8eb96363a198833e27
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---


# Bonnes pratiques relatives à la gestion des exceptions

Si une exception n’est pas écrite dans la variable `exception.log` avec le modèle d’exception comme contexte, il n’est pas reconnu et analysé correctement dans New Relic ou dans tout autre stockage de journaux compatible avec la monologie PSR-3. La journalisation d’une partie seulement de l’exception (ou la journalisation dans un fichier incorrect) entraîne des bogues en production lorsque les exceptions sont négligées.

## Correction de la gestion des exceptions

La liste de contrôle suivante fournit des exemples pour démontrer la gestion correcte des exceptions.

### ![correct](../../../assets/yes.svg) Écrire dans le journal des exceptions

Écrivez dans le journal des exceptions à l’aide du modèle suivant, indépendamment des autres actions, sauf s’il y a une raison irréfutable de ne pas le faire.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

Cette approche enregistre automatiquement la variable `$e->getMessage` au message du journal et au `$e` dans le contexte, en suivant la [PSR-3 context standard](https://www.php-fig.org/psr/psr-3/#13-context). Cela se fait dans `\Magento\Framework\Logger\Monolog::addRecord`.

### ![correct](../../../assets/yes.svg) Signaux muets

Mutez les signaux en ne consignant pas les exceptions qui font partie du flux d’opérations prévu. Aucune action de suivi n’est nécessaire lorsque l’exception est rencontrée. Il n’est donc pas nécessaire de la consigner et de l’analyser lorsqu’elle se produit. Ajoutez un commentaire indiquant la raison de l’arrêt des signaux et le caractère intentionnel de ce dernier. Combiner avec `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![correct](../../../assets/yes.svg) Rétrogradation des exceptions

Pour rétrograder les exceptions en suivant la [PSR-3 context standard](https://www.php-fig.org/psr/psr-3/#13-context).

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

### ![correct](../../../assets/yes.svg) Enregistrer les messages et la trace complète des exceptions

Consignez les messages et la trace complète des exceptions en suivant la [PSR-3 context standard](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## Gestion des exceptions incorrecte

Les exemples suivants montrent une gestion incorrecte des exceptions.

### ![incorrect](../../../assets/no.svg) Logique avant connexion

La logique avant la journalisation peut entraîner une autre exception ou une erreur fatale, ce qui empêche l’enregistrement de l’exception et doit être remplacé par [exemple correct](#correct-logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![incorrect](../../../assets/no.svg) Vide `catch`

Vide `catch` Les blocs peuvent être un signe d’arrêt involontaire et doivent être remplacés par le [exemple correct](#correct-mute-signals).

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

### ![incorrect](../../../assets/no.svg) Enregistrer les messages et les tracer dans différents fichiers journaux

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

Résolvez ce problème en remplaçant le code par les exemples corrects présentés dans la section [Écrire dans le journal des exceptions](#correct-write-to-the-exception-log) ou [Rétrogradation des exceptions](#correct-downgrade-exceptions).

### ![incorrect](../../../assets/no.svg) Rétrogradation des exceptions sans contexte

L’exception est dégradée en erreur, ce qui ne permet pas de transmettre un objet, mais uniquement une chaîne. Par conséquent, la variable `getMessage()`. Cela entraîne la perte de la trace et doit être remplacé par les exemples corrects présentés dans la section [Écrire dans le journal des exceptions](#correct-write-to-the-exception-log) ou [Rétrogradation des exceptions](#correct-downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![incorrect](../../../assets/no.svg) Consigne uniquement le message dans le journal des exceptions

Au lieu de transmettre l’objet `$e`, uniquement `$e->getMessage()` est transmis. Cela entraîne la perte de la trace et doit être remplacé par les exemples corrects présentés. [Écrire dans le journal des exceptions](#correct-write-to-the-exception-log) ou [Rétrogradation des exceptions](#correct-downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![incorrect](../../../assets/no.svg) Absente `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

Ignorer la variable `phpcs:ignore` déclenche un avertissement dans le PHPCS et ne doit pas transmettre votre CI. Il doit être remplacé par l’exemple correct illustré dans [Signaux muets](#correct-mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
