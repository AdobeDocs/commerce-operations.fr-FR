---
title: Mettre à niveau [!DNL Data Migration Tool]
description: Découvrez comment mettre à niveau le [!DNL Data Migration Tool] pour transférer des données entre le Magento 1 et le Magento 2.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# Mettre à niveau [!DNL Data Migration Tool]

Pour vérifier les versions de votre installation actuelle du Magento 2 et les [!DNL Data Migration Tool] correspond exactement, vous devrez peut-être mettre à niveau l’outil.

## Conditions préalables

Avant de mettre à niveau la [!DNL Data Migration Tool], vous devez :

* Mettez à niveau votre logiciel de Magento pour obtenir la dernière version.

* Sauvegardez les `vendor/magento/data-migration-tool` directory

* Assurez-vous que la variable [!DNL Data Migration Tool] version correspond à la version de l’application Magento.

### Mettre à niveau votre logiciel Magento

Si vous ne l’avez pas déjà fait, [mettre à niveau le logiciel Magento](../../upgrade/overview.md).

### Sauvegardez les `vendor/magento/data-migration-tool` directory

Avant la mise à niveau de [!DNL Data Migration Tool], sauvegardez au moins le `vendor/magento/data-migration-tool` répertoire . Au cours de la mise à niveau, il peut être supprimé et remplacé par le code mis à jour.

Vous pouvez également sauvegarder l’ensemble du code base de Magento et de la base de données à l’aide de la commande suivante :

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>Le `vendor/magento/data-migration-tool` contient votre code personnalisé. Si vous ne le sauvegardez pas, vous risquez de perdre vos personnalisations lors de la mise à niveau.


### Assurez-vous que les versions correspondent

Les versions de la variable [!DNL Data Migration Tool] et votre logiciel de Magento doit correspondre exactement. Par exemple, Magento 2.1.2 requiert la version 2.1.2 de la variable [!DNL Data Migration Tool].

Voir [Installer [!DNL Data Migration Tool]](install.md) rubrique pour savoir comment :

* [Vérifier](install.md#check-your-version) votre version de Magento 2

* [Rechercher](install.md#find-released-versions-of-data-migration-tool) versions publiées de [!DNL Data Migration Tool]

* [Vérifier](install.md#check-version-of-installed-data-migration-tool) la valeur [!DNL Data Migration Tool] version

## Mettre à niveau [!DNL Data Migration Tool]

1. Connectez-vous à votre serveur d’applications en tant que ou passez à [le propriétaire du système de fichiers ;](../../installation/prerequisites/file-system/overview.md).
1. Modifiez le répertoire racine de l’application.
1. Saisissez la commande suivante :

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   where `<version>` doit correspondre à la version du code base de Magento 2.

   Par exemple, pour la version 2.1.2, saisissez :

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Patientez pendant que la commande est terminée.
