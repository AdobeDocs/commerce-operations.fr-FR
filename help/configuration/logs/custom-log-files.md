---
title: Écriture dans le fichier journal personnalisé
description: Découvrez comment configurer des fichiers journaux personnalisés.
feature: Configuration, Logs
badge: label="Contribué par Atwix" type="Informative" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Écriture dans un fichier journal personnalisé

Le `Magento\Framework\Logger` module contient les classes de gestionnaire suivantes :

| Classe | Fichier journal |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

Vous pouvez les trouver dans la variable `lib/internal/Magento/Framework/Logger/Handler` répertoire .

Vous pouvez utiliser l’une des méthodes suivantes pour vous connecter à un fichier personnalisé :

- Configurez un fichier journal personnalisé dans le `di.xml`
- Configuration d’un fichier personnalisé dans la classe de gestionnaire de journalisation personnalisée

## Configurez un fichier journal personnalisé dans le `di.xml`

Cet exemple montre comment utiliser [types virtuels](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) to log `debug` messages dans un fichier journal personnalisé au lieu d’un fichier journal standard `/var/log/debug.log`.

1. Dans le `di.xml` de votre module, définissez un fichier journal personnalisé en tant que [type virtuel](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   Le `name` valeur de `Magento\Payment\Model\Method\MyCustomDebug` doit être unique.

1. Définir le gestionnaire dans un autre [type virtuel](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) avec un `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. Injectez le `MyCustomLogger` [type virtuel](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) dans le `Magento\Payment\Model\Method\Logger` objet :

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. Classe virtuelle `Magento\Payment\Model\Method\MyCustomDebug` est injecté dans la variable `debug` du gestionnaire `$logger` dans la propriété `Magento\Payment\Model\Method\Logger` classe .

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

Les messages d’exception sont consignés dans la variable `/var/log/payment.log` fichier .

## Configuration d’un fichier journal personnalisé dans la classe du gestionnaire de journalisation

Cet exemple montre comment utiliser une classe de gestionnaire de journalisation personnalisée pour consigner des données `error` messages dans un fichier journal spécifique.

1. Créez une classe qui consigne les données. Dans cet exemple, la classe est définie dans `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`.

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   namespace Vendor\ModuleName\Logger\Handler;
   
   use Magento\Framework\Logger\Handler\Base as BaseHandler;
   use Monolog\Logger as MonologLogger;
   
   /**
    * Class ErrorHandler
    */
   class ErrorHandler extends BaseHandler
   {
       /**
        * Logging level
        *
        * @var int
        */
       protected $loggerType = MonologLogger::ERROR;
   
       /**
        * File name
        *
        * @var string
        */
       protected $fileName = '/var/log/my_custom_logger/error.log';
   }
   ```

1. Définissez le gestionnaire pour cette classe en tant que [type virtuel](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) dans le de `di.xml` fichier .

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger` est un identifiant unique.

1. Dans le `type` définition, spécifiez le nom de classe où le gestionnaire personnalisé de journalisation est injecté. Utilisez le nom de type virtuel de l’étape précédente comme argument pour ce type.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   Code source de `Vendor\ModuleName\Observer\MyObserver` Classe :

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   declare(strict_types=1);
   
   namespace Vendor\ModuleName\Observer;
   
   use Psr\Log\LoggerInterface as PsrLoggerInterface;
   use Exception;
   use Magento\Framework\Event\ObserverInterface;
   use Magento\Framework\Event\Observer;
   
   /**
    * Class MyObserver
    */
   class MyObserver implements ObserverInterface
   {
       /**
        * @var PsrLoggerInterface
        */
       private $logger;
   
       /**
        * MyObserver constructor.
        *
        * @param PsrLoggerInterface $logger
        */
       public function __construct(
           PsrLoggerInterface $logger
       ) {
           $this->logger = $logger;
       }
   
       /**
        * @param Observer $observer
        */
       public function execute(Observer $observer)
       {
           try {
               // some code goes here
           } catch (Exception $e) {
               $this->logger->error($e->getMessage());
           }
       }
   }
   ```

1. La classe `Vendor\ModuleName\Logger\Handler\ErrorHandler` est injecté dans la variable `error` du gestionnaire `$logger` dans la propriété `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

Les messages d’exception sont consignés dans la variable `/var/log/my_custom_logger/error.log` fichier .

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
