---
title: Étapes suivant la migration des données
description: Découvrez les étapes à suivre après avoir utilisé l’ [!DNL Data Migration Tool]  pour migrer les données de Magento 1 vers Magento 2.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# Étapes suivant la migration des données

Une fois la migration terminée et le nouveau site Magento 2 soigneusement testé, effectuez les tâches suivantes :

* Mettez Magento 1 en mode de maintenance et arrêtez définitivement toutes les activités d’administration.

* Démarrer les traitements cron de Magento 2

* [Vider tous les types de cache Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Réindexez tous les indexeurs de Magento 2.](../../../configuration/cli/manage-indexers.md#reindex)

* Modifiez le DNS et les équilibreurs de charge pour pointer vers le matériel de production Magento 2
