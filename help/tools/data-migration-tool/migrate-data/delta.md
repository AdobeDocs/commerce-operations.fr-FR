---
title: Migrer les modifications
description: Découvrez comment migrer uniquement les données qui ont changé depuis votre dernière migration de données de Magento 1 avec le [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# Migrer les modifications

L’outil de migration incrémentale installe les tables de déploiement (avec préfixe). `m2_cl_*`) et déclencheurs (pour le suivi des modifications) dans la base de données Magento 1 au cours de la [migration des données](data.md). Ces tables de déploiement et déclencheurs sont essentiels pour vous assurer que vous migrez uniquement les modifications apportées dans Magento 1 depuis la dernière migration des données. Ces modifications sont les suivantes :

* Données ajoutées par les clients via [storefront](https://glossary.magento.com/storefront) (création de commandes, de révisions et de modifications dans les profils client)

* Toutes les opérations avec des commandes, des produits et des catégories dans la variable [Administration](https://glossary.magento.com/magento-admin) panel

>[!NOTE]
>
>Toutes les autres entités nouvelles ou mises à jour entrées par le biais de l’administrateur, telles que les pages d’attributs ou de CMS, ne sont pas incluses dans la migration incrémentielle et ne sont pas migrées.


Avant de commencer, procédez comme suit pour préparer :

1. Connectez-vous au serveur d’applications en tant que [le propriétaire du système de fichiers ;](../../../installation/prerequisites/file-system/overview.md).
1. Changement de la variable `/bin` ou assurez-vous qu’il est ajouté à votre système. `PATH`.

Voir [premières étapes](overview.md#first-steps) pour plus d’informations.

## Exécution de la commande de migration incrémentielle

Pour commencer la migration des modifications incrémentielles, exécutez :

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Où :

* `[-r|--reset]` est un argument facultatif qui lance la migration à partir du début. Vous pouvez utiliser cet argument pour tester la migration.

* `[-a|--auto]` est un argument facultatif qui empêche l’arrêt de la migration lorsqu’elle rencontre des erreurs de vérification d’intégrité.

* `{<path to config.xml>}` est le chemin d’accès absolu au système de fichiers vers `config.xml`; cet argument est obligatoire.

>[!NOTE]
>
>La migration incrémentale est un processus continu ; il redémarre automatiquement toutes les 5 secondes. Utilisez CTRL-C pour abandonner le processus de migration.


## Migration de données créées par des extensions tierces

Dans le `Delta` , [!DNL Data Migration Tool] migre les données créées uniquement par les modules du Magento lui-même et n’est pas responsable du code ni des extensions effectuées par des développeurs tiers. Si ces extensions ont créé des données dans la base de données storefront et que le commerçant souhaite que ces données soient dans le Magento 2 — fichiers de configuration de la variable [!DNL Data Migration Tool] doivent être créés et modifiés en conséquence.

Si [extension](https://glossary.magento.com/extension) possède ses propres tables. Vous devez suivre leurs modifications pour la migration delta. Procédez comme suit :

1. Ajoutez les tables à tracker dans le `deltalog.xml` fichier
1. Créez une classe delta supplémentaire qui étend la variable `Migration\App\Step\AbstractDelta`
1. Ajoutez le nom de la classe nouvellement créée à la section de mode delta de `config.xml`