---
title: Paramètres de migration des données
description: Découvrez comment commencer la migration des paramètres du Magento 1 vers le Magento 2 avec le  [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Paramètres de migration des données

Le mode `Settings` migre les magasins, les sites web et la configuration du système comme les paramètres d’expédition, de paiement et de taxe. Selon notre [order](overview.md#migration-order) de migration de données, vous devez d’abord migrer les paramètres.

Avant de commencer, procédez comme suit pour préparer :

1. Connectez-vous au serveur d’applications en tant que [ propriétaire du système de fichiers](../../../installation/prerequisites/file-system/overview.md).

1. Modifiez le répertoire `/bin` ou assurez-vous qu&#39;il est ajouté à votre système `PATH`.

>[!NOTE]
>
>Assurez-vous que Magento 2 est déployé en mode `default`. Le mode Développeur peut entraîner des erreurs de validation dans l’outil de migration.


Pour plus d’informations, voir la section [premières étapes](overview.md#first-steps) .

## Exécution de la commande de migration des paramètres

Pour commencer la migration des paramètres, exécutez :

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Où :

* `[-r|--reset]` est un argument facultatif qui lance la migration à partir du début. Vous pouvez utiliser cet argument pour tester la migration

* `[-a|--auto]` est un argument facultatif qui empêche l’arrêt de la migration lorsqu’elle rencontre des erreurs de vérification de l’intégrité.

* `{<path to config.xml>}` est le chemin d’accès absolu au fichier [`config.xml`](../configure.md#configure-migration-in-vendor-folder) de l’outil de migration ; cet argument est obligatoire.

>[!NOTE]
>
>Cette commande ne migre pas tous les paramètres de configuration. Vérifiez tous les paramètres de l’administrateur Magento 2 avant de continuer.


Le message `Migration completed` s’affiche une fois les paramètres transférés avec succès.

## Configuration des règles de migration personnalisées

Vous pouvez ignorer, renommer ou modifier les configurations système lors de la migration des paramètres. Pour ce faire, spécifiez vos règles personnalisées dans le fichier `settings.xml`.

1. Connectez-vous au serveur d’applications en tant que [propriétaire du système de fichiers](../../../installation/prerequisites/file-system/overview.md) ou passez à cette fonction.

1. Accédez au répertoire suivant :

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Par exemple, si l’application est installée dans `/var/www/html`, le fichier `settings.xml.dist` se trouve dans l’un des répertoires suivants :

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Pour créer un fichier `settings.xml` à partir de l’exemple fourni, exécutez :

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Effectuez vos modifications dans `settings.xml`.

1. Pour spécifier le nouveau nom du fichier de paramètres pour le mappage, modifiez la balise `<settings_map_file>` dans le fichier `path/to/config.xml`.

Pour plus d’informations, voir la section [Mode de migration des paramètres](../technical-specification.md#settings-migration-mode) de la [spécification](../technical-specification.md) de l’outil.

## Étape suivante de migration

* [Migration des données](data.md)
