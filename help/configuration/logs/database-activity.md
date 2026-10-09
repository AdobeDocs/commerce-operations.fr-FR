---
title: Consigner l'activité de la base de données
description: Configurez Commerce pour consigner l’activité de la base de données à l’aide de l’interface du journal.
feature: Configuration, Logs, Storage
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
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
source-wordcount: '110'
ht-degree: 0%
---
# Consigner l&#39;activité de la base de données

L’exemple suivant montre comment consigner l’activité de la base de données à l’aide du `[Magento\Framework\DB\LoggerInterface](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/LoggerInterface.php)`, qui comporte deux implémentations :

- N’enregistre rien (par défaut) : [`Magento\Framework\DB\Logger\Quiet`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/Logger/Quiet.php)
- Connecte-toi au répertoire `var/log` : [`Magento\Framework\DB\Logger\File`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/Logger/File.php)

>[!TIP]
>
>Vous pouvez utiliser l’interface de ligne de commande Commerce pour [activer et désactiver la journalisation de la base de données](../cli/enable-logging.md#database-logging).

Pour modifier la configuration par défaut d’`\Magento\Framework\DB\Logger\LoggerProxy`, modifiez votre `app/etc/di.xml`.

Tout d’abord, modifiez les valeurs par défaut des arguments `loggerAlias` et `logCallStack` en :

```xml
<type name="Magento\Framework\DB\Logger\LoggerProxy">
    <arguments>
        <argument name="loggerAlias" xsi:type="const">Magento\Framework\DB\Logger\LoggerProxy::LOGGER_ALIAS_FILE</argument>
        <argument name="logAllQueries" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_LOG_EVERYTHING</argument>
        <argument name="logQueryTime" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_QUERY_TIME_THRESHOLD</argument>
        <argument name="logCallStack" xsi:type="boolean">false</argument>
    </arguments>
</type>
```

Ensuite, indiquez le chemin d’accès au fichier pour `Magento\Framework\DB\Logger\File` :

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

Enfin, compilez le code avec :

```shell
bin/magento setup:di:compile
```

Et nettoyez le cache avec :

```shell
bin/magento cache:clean
```

