---
title: Activité Log database
description: Configurez Commerce pour consigner l’activité de la base de données à l’aide de l’interface Enregistreur.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# Activité Log database

L’exemple suivant montre comment consigner une activité de base de données à l’aide de la variable [`Magento\Framework\DB\LoggerInterface`][interface], qui comporte deux implémentations :

- Ne consigne rien (par défaut) : [`Magento\Framework\DB\Logger\Quiet`][quiet]
- Journaux de la `var/log` directory: [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>Vous pouvez utiliser l’interface de ligne de commande de Commerce pour [activation et désactivation de la journalisation de la base de données](../cli/enable-logging.md#database-logging).

Pour modifier la configuration par défaut de `\Magento\Framework\DB\Logger\LoggerProxy`, modifiez vos `app/etc/di.xml`.

Tout d’abord, modifiez les valeurs par défaut de `loggerAlias` et `logCallStack` arguments pour :

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

Ensuite, indiquez le chemin d’accès au fichier pour `Magento\Framework\DB\Logger\File`:

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

Et effacez le cache avec :

```bash
bin/magento cache:clean
```

<!-- link definitions -->

[file]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/File.php
[interface]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/LoggerInterface.php
[quiet]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/Quiet.php
