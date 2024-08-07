---
title: Migrer les modifications
description: Découvrez comment migrer uniquement les données qui ont changé depuis votre dernière migration de données de Magento 1 avec le  [!DNL Data Migration Tool].
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Migrer les modifications

L’outil de migration incrémentielle installe les tables de déploiement (avec le préfixe `m2_cl_*`) et les déclencheurs (pour le suivi des modifications) dans la base de données Magento 1 lors de la [migration des données](data.md). Ces tables de déploiement et déclencheurs sont essentiels pour vous assurer que vous migrez uniquement les modifications apportées dans Magento 1 depuis la dernière migration des données. Ces modifications sont les suivantes :

* Données que les clients ont ajoutées via storefront (commandes, révisions et modifications créées dans les profils client)

* Toutes les opérations avec commandes, produits et catégories dans le panneau d’administration

>[!NOTE]
>
>Toutes les autres entités nouvelles ou mises à jour entrées par le biais de l’administrateur, telles que les pages d’attributs ou de CMS, ne sont pas incluses dans la migration incrémentielle et ne sont pas migrées.


Avant de commencer, procédez comme suit pour préparer :

1. Connectez-vous au serveur d’applications en tant que [propriétaire du système de fichiers](../../../installation/prerequisites/file-system/overview.md).
1. Modifiez le répertoire `/bin` ou assurez-vous qu&#39;il est ajouté à votre système `PATH`.

Pour plus d’informations, voir la section [premières étapes](overview.md#first-steps) .

## Exécution de la commande de migration incrémentielle

Pour commencer la migration des modifications incrémentielles, exécutez :

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Où :

* `[-r|--reset]` est un argument facultatif qui lance la migration à partir du début. Vous pouvez utiliser cet argument pour tester la migration.

* `[-a|--auto]` est un argument facultatif qui empêche l’arrêt de la migration lorsqu’elle rencontre des erreurs de vérification de l’intégrité.

* `{<path to config.xml>}` est le chemin d’accès absolu au système de fichiers `config.xml` ; cet argument est obligatoire.

>[!NOTE]
>
>La migration incrémentielle est un processus continu qui redémarre automatiquement toutes les 5 secondes. Utilisez CTRL-C pour abandonner le processus de migration.


## Migration des données créées par des extensions tierces

En mode `Delta`, [!DNL Data Migration Tool] migre les données créées uniquement par les modules du Magento lui-même et n’est pas responsable du code ni des extensions effectuées par des développeurs tiers. Si ces extensions ont créé des données dans la base de données storefront et que le commerçant souhaite que ces données soient dans le Magento 2 — les fichiers de configuration de l’ [!DNL Data Migration Tool] doivent être créés et modifiés en conséquence.

Si une extension possède ses propres tables et que vous devez suivre leurs modifications pour la migration delta, procédez comme suit :

1. Ajoutez les tables à suivre au fichier `deltalog.xml`.
1. Créez une classe delta supplémentaire qui étend l’ `Migration\App\Step\AbstractDelta`
1. Ajoutez le nom de la classe nouvellement créée à la section de mode delta de `config.xml`.
