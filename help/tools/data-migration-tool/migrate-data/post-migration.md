---
title: Étapes suivant la migration des données
description: Découvrez les étapes à suivre après avoir utilisé l’[!DNL Data Migration Tool] pour migrer les données de Magento 1 vers Magento 2.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
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
source-wordcount: '84'
ht-degree: 0%
---
# Étapes suivant la migration des données

Une fois la migration terminée et le nouveau site Magento 2 soigneusement testé, effectuez les tâches suivantes :

* Mettez Magento 1 en mode de maintenance et arrêtez définitivement toutes les activités d’administration.

* Démarrer les traitements Magento 2 cron

* [Videz tous les types de cache Magento 2.](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Réindexez tous les indexeurs Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Modifiez le DNS et les équilibreurs de charge pour pointer vers le matériel de production Magento 2
