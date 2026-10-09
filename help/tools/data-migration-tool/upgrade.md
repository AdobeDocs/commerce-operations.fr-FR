---
title: Mettre à niveau le [!DNL Data Migration Tool]
description: Découvrez comment mettre à niveau le [!DNL Data Migration Tool] pour transférer des données entre Magento 1 et Magento 2.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '235'
ht-degree: 0%
---
# Mettre à niveau le [!DNL Data Migration Tool]

Pour vous assurer que les versions de votre installation actuelle de Magento 2 et de la [!DNL Data Migration Tool] correspondent exactement, vous devrez peut-être mettre à niveau l’outil.

## Conditions préalables

Avant de mettre à niveau le [!DNL Data Migration Tool], vous devez :

* Mettez à niveau votre logiciel Magento pour obtenir la dernière version

* Sauvegarde du répertoire `vendor/magento/data-migration-tool`

* Assurez-vous que la version [!DNL Data Migration Tool] correspond à la version de l’application Magento

### Mise à niveau de votre logiciel Magento

Si vous ne l&#39;avez pas déjà fait, [mettez à niveau le logiciel Magento](../../upgrade/overview.md).

### Sauvegarde du répertoire `vendor/magento/data-migration-tool`

Avant de mettre à niveau le [!DNL Data Migration Tool], sauvegardez au moins le répertoire `vendor/magento/data-migration-tool`. Pendant la mise à niveau, il peut être supprimé et remplacé par le code mis à jour.

Vous pouvez également sauvegarder la base de code et la base de données Magento entières à l’aide de la commande suivante :

```shell
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>Le répertoire `vendor/magento/data-migration-tool` contient votre code personnalisé. Si vous ne le sauvegardez pas, vous risquez de perdre vos personnalisations lors de la mise à niveau.


### Vérifiez que les versions correspondent.

Les versions du [!DNL Data Migration Tool] et de votre logiciel Magento doivent correspondre exactement. Par exemple, Magento 2.1.2 nécessite la version 2.1.2 du [!DNL Data Migration Tool].

Voir la rubrique [Installer [!DNL Data Migration Tool]](install.md) pour savoir comment :

* [Vérifier](install.md#check-your-version) votre version de Magento 2

* [Rechercher](install.md#find-released-versions-of-data-migration-tool) versions publiées du [!DNL Data Migration Tool]

* [Vérifier](install.md#check-version-of-installed-data-migration-tool) la version [!DNL Data Migration Tool]

## Mettre à niveau le [!DNL Data Migration Tool]

1. Connectez-vous au serveur d’applications en tant que propriétaire du système de fichiers [ou passez à ce serveur](../../installation/prerequisites/file-system/overview.md).
1. Accédez au répertoire racine de l’application.
1. Saisissez la commande suivante :

   ```shell
   composer require magento/data-migration-tool:<version>
   ```

   où `<version>` doit correspondre à la version de la base de code Magento 2.

   Par exemple, pour la version 2.1.2, saisissez :

   ```shell
   composer require magento/data-migration-tool:2.1.2
   ```

1. Patientez pendant la fin de la commande.
