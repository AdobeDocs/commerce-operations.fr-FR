---
title: Paramètres de migration des données
description: Découvrez comment commencer la migration des paramètres de Magento 1 vers Magento 2 avec le [!DNL Data Migration Tool].
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# Paramètres de migration des données

Le `Settings` migre les magasins, les sites web et la configuration du système, comme les paramètres d’expédition, de paiement et de taxe. Selon notre migration de données [order](overview.md#migration-order), vous devez d’abord migrer les paramètres.

Avant de commencer, procédez comme suit pour préparer :

1. Connectez-vous au serveur avec votre instance Magento 2 en tant que [le propriétaire du système de fichiers ;](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. Modification apportée au Magento 2 `/bin` ou assurez-vous qu’il est ajouté à votre PATH système.

>[!NOTE]
>
>Assurez-vous que Magento 2 est déployé dans `default` mode . Le mode Développeur peut entraîner des erreurs de validation dans l’outil de migration.


Voir [premières étapes](overview.md#first-steps) pour plus d’informations.

## Exécution de la commande de migration des paramètres

Pour commencer la migration des paramètres, exécutez :

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Où :

* `[-r|--reset]` est un argument facultatif qui lance la migration à partir du début. Vous pouvez utiliser cet argument pour tester la migration.

* `[-a|--auto]` est un argument facultatif qui empêche l’arrêt de la migration lorsqu’elle rencontre des erreurs de vérification d’intégrité.

* `{<path to config.xml>}` est le chemin d’accès absolu au système de fichiers de l’outil de migration. [`config.xml`](../configure.md#configure-migration-in-vendor-folder) fichier; cet argument est obligatoire.

>[!NOTE]
>
>Cette commande ne migre pas tous les paramètres de configuration. Vérification de tous les paramètres du Magento 2 [Administration](https://glossary.magento.com/admin) avant de poursuivre.


Le `Migration completed` s’affiche une fois les paramètres transférés.

## Configuration des règles de migration personnalisées

Vous pouvez ignorer, renommer ou modifier les configurations système lors de la migration des paramètres. Pour ce faire, spécifiez vos règles personnalisées dans la variable `settings.xml` fichier .

1. Connectez-vous au serveur avec votre instance de Magento 2 en tant que ou passez au serveur [propriétaire du système de fichiers](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. Accédez au répertoire suivant :

   ```bash
   cd <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Par exemple, si Magento 2 est installé dans `/var/www/html`, la variable `settings.xml.dist` se trouve dans l’un des répertoires suivants :

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Pour créer une `settings.xml` à partir de l’exemple fourni, exécutez :

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Apportez vos modifications dans `settings.xml`.

1. Pour spécifier le nouveau nom du fichier de paramètres pour le mappage, modifiez la variable `<settings_map_file>` dans la balise `path/to/config.xml` fichier .

Pour plus d’informations, voir [Mode de migration des paramètres](../technical-specification.md#settings-migration-mode) de l’outil [spécification](../technical-specification.md).

## Étape suivante de migration

* [Migration des données](data.md)
