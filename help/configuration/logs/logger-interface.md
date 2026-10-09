---
title: Interface de l’enregistreur
description: Découvrez comment utiliser l’interface de l’enregistreur dans Adobe Commerce pour la journalisation personnalisée. Découvrez l’implémentation de PSR-3 et les fonctions de journalisation.
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
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
source-wordcount: '210'
ht-degree: 0%
---
# Interface de l’enregistreur

Pour commencer à utiliser un enregistreur, vous devez créer une instance de `\Psr\Log\LoggerInterface`. Avec cette interface, vous pouvez appeler les fonctions suivantes pour écrire des données dans des fichiers journaux :

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critique()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [urgence()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [avis()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [avertissement()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Une méthode pour ce faire est expliquée dans l’exemple d’activité de base de données [Log](../logs/database-activity.md).

Voici un autre moyen :

```php
class SomeModel
 {
     private $logger;

     public function __construct(\Psr\Log\LoggerInterface $logger)
     {
         $this->logger = $logger;
     }

     public function doSomething()
     {
         try {
             //do something
         } catch (\Exception $e) {
             $this->logger->critical('Error message', ['exception' => $e]);
         }
     }
 }
```

L&#39;exemple précédent montre que `SomeModel` reçoit un objet `\Psr\Log\LoggerInterface` par injection de constructeur. Dans un `doSomething` de méthode, si une erreur s’est produite, elle est consignée dans un `critical` de méthode (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) définit huit niveaux de journal (débogage, information, avertissement, erreur, critique, alerte et urgence).
