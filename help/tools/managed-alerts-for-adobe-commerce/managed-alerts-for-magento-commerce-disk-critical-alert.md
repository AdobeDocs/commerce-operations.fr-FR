---
title: 'Alertes gérées pour Adobe Commerce : alerte critique de disque'
description: Cet article décrit les étapes de dépannage à suivre lorsque vous recevez une alerte de disque critique pour Adobe Commerce dans [!DNL New Relic]. Une action immédiate est nécessaire pour remédier au problème.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 1378dcfd-cf7c-4234-82bb-6697e23d54ca
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: a59f76dc-e003-5617-951e-dffa5bd3de81
    internal-label: Support
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%
---
# Alertes gérées pour Adobe Commerce : alerte critique de disque

Cet article décrit les étapes de dépannage à suivre lorsque vous recevez une alerte de disque critique pour Adobe Commerce dans [!DNL New Relic]. Une action immédiate est nécessaire pour remédier au problème. L’alerte se présente comme suit, selon le canal de notification d’alerte que vous avez sélectionné.

![alerte critique de disque](../../assets/managed-alerts/disk-critical-magento-managed.png){width="500"}

## Produits et versions concernés

Infrastructure cloud Adobe Commerce sur l’architecture ProPlan

## Problème

Vous recevrez une alerte en [!DNL New Relic] si vous vous êtes inscrit aux alertes [Gérées pour Adobe Commerce](managed-alerts-for-magento-commerce.md) et qu’un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe pour fournir aux clients un ensemble de normes à l’aide des informations provenant des services d’assistance et d’ingénierie.

<u> **Do!** </u>

* Abandonner tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Mettez immédiatement votre site en mode de maintenance s’il ne répond plus du tout. Pour connaître les étapes, reportez-vous à la section [&#x200B; Activer ou désactiver le mode de maintenance](/help/installation/tutorials/maintenance-mode.md). Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées pour vous assurer que vous pouvez toujours accéder à votre site à des fins de dépannage. Pour connaître les étapes, voir [Tenir à jour la liste des adresses IP exemptées](/help/installation/tutorials/maintenance-mode.md#maintain-the-list-of-exempt-ip-addresses).

**Non !**

* Lancez d’autres campagnes marketing qui peuvent apporter des pages vues supplémentaires à votre site.
* Exécutez des indexeurs ou des crons supplémentaires, ce qui peut entraîner une contrainte supplémentaire sur le CPU ou le disque.
* Effectuez toutes les tâches administratives majeures (c’est-à-dire Administration de Commerce, importations/exportations de données).
* Videz votre cache.

Votre site peut ne plus répondre (si vous ne rencontrez pas déjà de panne) si vous effectuez l’une des actions « Ne pas » avant d’avoir enquêté et résolu la cause de l’alerte.

## Solution

Pour identifier et résoudre les problèmes, procédez comme suit.

>[!WARNING]
>
>Comme il s’agit d’une alerte critique, il est vivement recommandé d’effectuer l’**étape 1** avant d’essayer de résoudre le problème (étape 2 et suivantes).

1. Vérifiez si un ticket d’assistance Adobe Commerce existe. Pour connaître les étapes à suivre, reportez-vous à la section [Tracker vos tickets d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#track-support-case) dans la base de connaissances de l’assistance Commerce. L’assistance peut avoir reçu une alerte de seuil [!DNL New Relic], créé un ticket et commencé à travailler sur le problème. S’il n’existe aucun ticket, créez-en un. Le ticket doit contenir les informations suivantes :
   * Motif du contact : sélectionnez **[!UICONTROL New Relic CRITICAL alert received]**.
   * Description de l’alerte.
   * [[!DNL New Relic] Lien de l’incident](https://docs.newrelic.com/docs/alerts/incident-management/view-event-details-incidents/). Cela est inclus dans vos [alertes gérées pour Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Dans [!DNL New Relic], passez en revue les disques pour une utilisation optimale. Pour connaître les étapes, reportez-vous à **[!UICONTROL Storage]** onglet sur la page Hôtes de surveillance des infrastructures [[!DNL New Relic]  : [!UICONTROL Storage] onglet &#x200B;](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage) :
   * Si dans [!DNL New Relic] vous constatez une augmentation lente de l’utilisation du disque, essayez les options suivantes :
     * Optimisation de l’espace disque en ajustant l’allocation de l’espace. Pour connaître les étapes, reportez-vous à la section [Gérer l’espace disque](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space) dans le guide Commerce sur le cloud . Vous devrez peut-être également demander de l’espace disque supplémentaire (contactez l’équipe chargée de votre compte Adobe).
     * Libérez de l’espace disque pour MySQL. Pour connaître la procédure à suivre, reportez-vous à la section [Espace disque MySQL faible](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27806) de la base de connaissances de la prise en charge de Commerce.
     * Si [!DNL New Relic] indique une augmentation rapide de l’utilisation du disque, cela peut indiquer qu’un problème a provoqué une augmentation très rapide d’un fichier dans un répertoire. Effectuez les vérifications suivantes :
       1. Vérifiez l’espace disque global pour identifier le problème en exécutant la commande suivante dans l’interface de ligne de commande/terminal : `df -h`
       1. Après avoir identifié un répertoire dont l’utilisation du disque est inattendue et croissante, vous devez vérifier le système de fichiers concerné. L&#39;exemple suivant montre comment vérifier le répertoire de fichiers `pub/media/`. Il s’agit du répertoire utilisé par Commerce pour stocker les journaux et les fichiers multimédias volumineux. Toutefois, vous devez exécuter cette commande pour tout répertoire affichant une utilisation inattendue du disque : `du -sch ~/pub/media/*`

Si la sortie du terminal affiche un fichier dans l’un de ces répertoires, ce qui augmente rapidement l’utilisation du disque et que vous savez que le contenu du fichier n’est pas nécessaire, envisagez de supprimer le fichier. Si vous n’êtes pas à l’aise avec cette action, [envoyez un ticket d’assistance Adobe Commerce](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case).
