---
title: Etapes de migration post-données
description: Découvrez les étapes à suivre après avoir utilisé la méthode [!DNL Data Migration Tool] pour migrer les données de Magento 1 vers Magento 2.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# Etapes de migration post-données

Une fois la migration terminée et le nouveau site Magento 2 entièrement testé, effectuez les tâches suivantes :

* Placez le Magento 1 en mode de maintenance et arrêtez définitivement toutes les activités d’administration

* Démarrage des tâches Magento 2 cron

* [Purge de tous les types de cache du Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Réindexation de tous les indexeurs Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Modifier les équilibreurs DNS et de charge pour qu’ils pointent vers le matériel de production Magento 2
