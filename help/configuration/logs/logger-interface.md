---
title: Interface de l’enregistreur
description: Prise en main de l’interface de l’enregistreur.
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '111'
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
- [notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
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
