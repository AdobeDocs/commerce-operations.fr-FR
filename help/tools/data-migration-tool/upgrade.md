---
title: Mettre à niveau le  [!DNL Data Migration Tool]
description: Découvrez comment mettre à niveau  [!DNL Data Migration Tool]  pour transférer des données entre Magento 1 et Magento 2.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Mettre à niveau le [!DNL Data Migration Tool]

Pour vous assurer que les versions de votre installation actuelle de Magento 2 et de [!DNL Data Migration Tool] correspondent exactement, vous devrez peut-être mettre à niveau l’outil.

## Conditions préalables

Avant de mettre à niveau le [!DNL Data Migration Tool], vous devez :

* Mettez à niveau votre logiciel de Magento pour obtenir la dernière version.

* Sauvegarde du répertoire `vendor/magento/data-migration-tool`

* Assurez-vous que la version [!DNL Data Migration Tool] correspond à la version de l’application Magento.

### Mettre à niveau votre logiciel Magento

Si vous ne l&#39;avez pas déjà fait, [mettez à niveau le logiciel de Magento](../../upgrade/overview.md).

### Sauvegarde du répertoire `vendor/magento/data-migration-tool`

Avant de mettre à niveau [!DNL Data Migration Tool], sauvegardez au moins le répertoire `vendor/magento/data-migration-tool`. Au cours de la mise à niveau, il peut être supprimé et remplacé par le code mis à jour.

Vous pouvez également sauvegarder l’ensemble du code base de Magento et de la base de données à l’aide de la commande suivante :

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>Le répertoire `vendor/magento/data-migration-tool` contient votre code personnalisé. Si vous ne le sauvegardez pas, vous risquez de perdre vos personnalisations lors de la mise à niveau.


### Assurez-vous que les versions correspondent.

Les versions de [!DNL Data Migration Tool] et de votre logiciel de Magento doivent correspondre exactement. Par exemple, Magento 2.1.2 nécessite la version 2.1.2 de [!DNL Data Migration Tool].

Consultez la rubrique [Installer [!DNL Data Migration Tool]](install.md) pour savoir comment :

* [Vérifiez](install.md#check-your-version) votre version 2 de Magento

* [Rechercher](install.md#find-released-versions-of-data-migration-tool) versions publiées de [!DNL Data Migration Tool]

* [Vérifiez](install.md#check-version-of-installed-data-migration-tool) la version [!DNL Data Migration Tool]

## Mettre à niveau le [!DNL Data Migration Tool]

1. Connectez-vous à votre serveur d’applications en tant que [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) ou basculez-vous vers cette fonction.
1. Modifiez le répertoire racine de l’application.
1. Saisissez la commande suivante :

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   où `<version>` doit correspondre à la version du code base de Magento 2.

   Par exemple, pour la version 2.1.2, saisissez :

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Patientez pendant que la commande est terminée.
