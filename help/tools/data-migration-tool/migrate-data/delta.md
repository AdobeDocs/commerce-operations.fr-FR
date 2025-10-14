---
title: Migrer les modifications
description: Découvrez comment migrer uniquement les données qui ont été modifiées depuis votre dernière migration de données Magento 1 avec  [!DNL Data Migration Tool].
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Migrer les modifications

L’outil de migration incrémentielle installe les tables deltalog (avec le préfixe `m2_cl_*`) et les déclencheurs (pour le suivi des modifications) dans la base de données Magento 1 lors de la [&#x200B; migration des données &#x200B;](data.md). Ces tables et triggers deltalog sont essentiels pour vous assurer de ne migrer que les modifications apportées dans Magento 1 depuis la dernière migration des données. Ces modifications sont les suivantes :

* Données ajoutées par les clients via storefront (commandes, révisions et modifications créées dans les profils de clients)

* Toutes les opérations avec des commandes, des produits et des catégories dans le panneau d’administration

>[!NOTE]
>
>Toutes les autres entités nouvelles ou mises à jour saisies par l’intermédiaire de l’administrateur, telles que les pages d’attributs ou de CMS, ne sont pas incluses dans la migration incrémentielle et ne sont pas migrées.


Avant de commencer, effectuez les étapes de préparation suivantes :

1. Connectez-vous au serveur d’applications en tant que [&#x200B; propriétaire du système de fichiers &#x200B;](../../../installation/prerequisites/file-system/overview.md).
1. Accédez au répertoire `/bin` ou assurez-vous qu’il est ajouté à votre `PATH` système.

Voir la section [premières étapes](overview.md#first-steps) pour plus d’informations.

## Exécutez la commande de migration incrémentielle

Pour démarrer la migration des modifications incrémentielles, exécutez :

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Où :

* `[-r|--reset]` est un argument facultatif qui lance la migration depuis le début. Vous pouvez utiliser cet argument pour tester la migration.

* `[-a|--auto]` est un argument facultatif qui empêche l’arrêt de la migration lorsqu’elle rencontre des erreurs de contrôle d’intégrité.

* `{<path to config.xml>}` est le chemin d’accès absolu au système de fichiers à `config.xml` ; cet argument est obligatoire.

>[!NOTE]
>
>La migration incrémentielle est un processus continu qui redémarre automatiquement toutes les 5 secondes. Utilisez Ctrl-C pour abandonner le processus de migration.


## Migration des données créées par des extensions tierces

En mode `Delta`, le [!DNL Data Migration Tool] migre les données créées uniquement par les modules Magento qui lui sont propres et n’est pas responsable du code ou des extensions créés par les développeurs tiers. Si ces extensions ont créé des données dans la base de données du storefront et que le commerçant souhaite avoir ces données dans Magento 2, les fichiers de configuration du [!DNL Data Migration Tool] doivent être créés et modifiés en conséquence.

Si une extension possède ses propres tables et que vous devez effectuer le suivi de leurs modifications pour la migration delta, procédez comme suit :

1. Ajoutez les tables à tracker dans le fichier `deltalog.xml`
1. Créez une classe delta supplémentaire qui étend le `Migration\App\Step\AbstractDelta`
1. Ajoutez le nom de la classe nouvellement créée à la section de mode delta de `config.xml`
