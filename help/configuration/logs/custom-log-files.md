---
title: Écrire dans un fichier journal personnalisé
description: Découvrez comment créer et configurer des fichiers journaux personnalisés dans Adobe Commerce. Découvrez les gestionnaires de journalisation et l’implémentation de la journalisation personnalisée.
feature: Configuration, Logs
badge: label="Contribution Atwix" type="Informative" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Écrire dans un fichier journal personnalisé

Le module `Magento\Framework\Logger` contient les classes de gestionnaire suivantes :

| Classe | Fichier journal |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php) | - |
| [Magento\Framework\Logger\Handler\Debug](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php) | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php) | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php) | - |
| [Magento\Framework\Logger\Handler\System](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php) | `/var/log/system.log` |

Vous pouvez les trouver dans le répertoire `lib/internal/Magento/Framework/Logger/Handler`.

Vous pouvez utiliser l’une des méthodes suivantes pour vous connecter à un fichier personnalisé :

- Configurer un fichier journal personnalisé dans le `di.xml`
- Configurer un fichier personnalisé dans la classe de gestionnaire d’enregistreur personnalisé

## Configurer un fichier journal personnalisé dans le `di.xml`

Cet exemple montre comment utiliser [les types virtuels](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) pour consigner des messages `debug` dans un fichier journal personnalisé au lieu d&#39;un `/var/log/debug.log` standard.

1. Dans le fichier `di.xml` de votre module, définissez un fichier journal personnalisé en tant que [type virtuel](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   La valeur `name` de `Magento\Payment\Model\Method\MyCustomDebug` doit être unique.

1. Définissez le gestionnaire dans un autre [type virtuel](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) avec un `name` unique :

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. Insérez le `MyCustomLogger` [type virtuel](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) dans l’objet `Magento\Payment\Model\Method\Logger` :

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. Le `Magento\Payment\Model\Method\MyCustomDebug` de classe virtuel est injecté dans le gestionnaire de `debug` de la propriété `$logger` dans la classe `Magento\Payment\Model\Method\Logger`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

Les messages d’exception sont consignés dans le fichier `/var/log/payment.log`.

## Configurez un fichier journal personnalisé dans la classe de gestionnaire d’enregistreur

Cet exemple montre comment utiliser une classe de gestionnaire d’enregistreur personnalisée pour consigner les messages `error` dans un fichier journal spécifique.

1. Créez une classe qui enregistre les données. Dans cet exemple, la classe est définie dans `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`.

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

1. Définissez le gestionnaire de cette classe en tant que [type virtuel](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) dans le fichier `di.xml` du module.

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

1. Dans la définition de `type`, spécifiez le nom de la classe dans laquelle le gestionnaire d’enregistreur personnalisé est injecté. Utilisez le nom du type virtuel de l’étape précédente comme argument pour ce type.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   Code Source de la classe `Vendor\ModuleName\Observer\MyObserver` :

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

1. Le `Vendor\ModuleName\Logger\Handler\ErrorHandler` de classe est injecté dans le gestionnaire de `error` de la propriété `$logger` dans le `Vendor\ModuleName\Observer\MyObserver` .

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

Les messages d’exception sont consignés dans le fichier `/var/log/my_custom_logger/error.log`.

