---
title: Consigner l'activité de la base de données
description: Configurez Commerce pour consigner l’activité de la base de données à l’aide de l’interface du journal.
feature: Configuration, Logs, Storage
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# Consigner l&#39;activité de la base de données

L’exemple suivant montre comment consigner l’activité de la base de données à l’aide du [`Magento\Framework\DB\LoggerInterface`][interface], qui comporte deux implémentations :

- N’enregistre rien (par défaut) : [`Magento\Framework\DB\Logger\Quiet`][quiet]
- Connecte-toi au répertoire `var/log` : [`Magento\Framework\DB\Logger\File`][file]

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

```bash
bin/magento setup:di:compile
```

Et nettoyez le cache avec :

```bash
bin/magento cache:clean
```

<!-- link definitions -->

[file]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/File.php
[interface]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/LoggerInterface.php
[quiet]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/Quiet.php
