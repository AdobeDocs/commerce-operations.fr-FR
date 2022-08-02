---
title: Interface de journalisation
description: Prise en main de l’interface de journalisation.
source-git-commit: f489c3e68c91c6f2e16bff233cf59472ed684b5c
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# Interface de journalisation

Pour commencer à utiliser un journal, vous devez créer une instance de `\Psr\Log\LoggerInterface`. Avec cette interface, vous pouvez appeler les fonctions suivantes pour écrire des données dans des fichiers journaux :

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [Emergency()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Pour ce faire, une méthode est expliquée dans la section [Activité Log database](../logs/database-activity.md) par exemple.

Une autre méthode est la suivante :

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

L’exemple précédent montre que `SomeModel` reçoit une `\Psr\Log\LoggerInterface` à l’aide de l’injection de constructeur. Dans une méthode `doSomething`, si une erreur s’est produite, elle est consignée dans une méthode . `critical` (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) définit huit niveaux de journal (débogage, informations, avis, avertissement, erreur, critique, alerte et urgence).
