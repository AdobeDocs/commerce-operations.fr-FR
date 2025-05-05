---
title: 'Alertes gérées sur Adobe Commerce : alerte d’avertissement  [!DNL Redis]  mémoire'
description: Cet article décrit les étapes de dépannage à suivre lorsque vous recevez une alerte  [!DNL Redis]  pour Adobe Commerce dans  [!DNL New Relic]. Une action immédiate est requise.
feature: Categories, Marketing Tools, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: e91ed9e95677790001fcfa3acca75a709c003c39
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---


# Alertes gérées sur Adobe Commerce : alerte d’avertissement de mémoire [!DNL Redis]

Cet article décrit les étapes de dépannage à suivre lorsque vous recevez une alerte d’avertissement [!DNL Redis] pour Adobe Commerce dans [!DNL New Relic]. Une action immédiate est nécessaire pour résoudre le problème. L’alerte se présente comme suit, selon le canal de notification d’alerte que vous avez sélectionné :

![new_relic_redis_memory_warning.png](../../assets/managed-alerts/new_relic_redis_memory_warning.png)

## Produits et versions concernés

Toutes les versions d’Adobe Commerce sur l’infrastructure cloud Planifient l’architecture.

## Problème

Vous recevrez une alerte en [!DNL New Relic] si vous vous êtes inscrit aux alertes [Gérées pour Adobe Commerce](managed-alerts-for-magento-commerce.md) et qu’un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe pour fournir aux commerçants un ensemble standard d’alertes à l’aide des informations provenant des services d’assistance et d’ingénierie.

**<u>Faites !</u>**

* Il est recommandé d’abandonner tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Si votre site ne répond plus ou ne répond plus du tout, mettez-le immédiatement en mode de maintenance. Pour connaître les étapes, reportez-vous à la section [Activation ou désactivation du mode de maintenance](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans le Guide d’installation de Commerce.
* Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées pour vous assurer que vous pouvez toujours accéder à votre site à des fins de dépannage. Pour connaître les étapes, reportez-vous à la section [Tenir à jour la liste des adresses IP exemptées](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) du Guide d’installation de Commerce.

**<u>Non !</u>**

* Lancez d’autres campagnes marketing qui peuvent apporter des pages vues supplémentaires à votre site.
* Exécutez des indexeurs ou des crons supplémentaires, ce qui peut entraîner une contrainte supplémentaire sur le CPU ou le disque.
* Effectuez toute tâche administrative majeure (c’est-à-dire, une action majeure dans l’administration Commerce, telle que des importations/exportations de données, des supports de vidage, l’enregistrement de catégories avec un grand nombre de produits attribués et des mises à jour en masse).
* Videz votre cache.

## Solution

Pour identifier et résoudre les problèmes, procédez comme suit.

1. Vérifiez si [!DNL Redis] mémoire utilisée augmente ou diminue en accédant à la page [one.newrelic.com](https://login.newrelic.com/login) > **Infrastructure** > **Services tiers**, puis sélectionnez le tableau de bord [!DNL Redis]. S’il est stable ou en augmentation, [soumettez un ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) pour que votre cluster soit mis à niveau, ou augmentez la limite de `maxmemory` au niveau suivant.
1. Si vous ne pouvez pas identifier la cause de l’augmentation de la consommation de mémoire [!DNL Redis], passez en revue les tendances récentes pour identifier les problèmes liés aux récents déploiements de code ou aux modifications de configuration (par exemple, nouveaux groupes de clients et modifications importantes du catalogue). Il est recommandé de passer en revue les sept derniers jours d’activité pour toutes les corrélations dans les déploiements ou modifications de code.
1. Recherchez les extensions tierces qui se comportent mal :
   * Essayez de trouver une corrélation avec les extensions tierces récemment installées et l’heure à laquelle le problème a commencé.
   * Consultez les extensions qui peuvent potentiellement affecter le cache d’Adobe Commerce et entraîner une croissance rapide du cache. Par exemple, les blocs de disposition personnalisés, le remplacement de la fonctionnalité de cache et le stockage de grandes quantités de données dans le cache.
1. S’il n’existe aucune preuve de mauvais comportement des extensions, [Installez les derniers correctifs pour résoudre  [!DNL Redis]  problèmes d’Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues). Si les étapes ci-dessus ne vous aident pas à identifier ou à résoudre le problème à la source, envisagez d’activer le cache L2 pour réduire le trafic réseau entre l’application et [!DNL Redis]. Pour obtenir des informations générales sur ce qu’est le cache L2, reportez-vous à la mise en cache [L2 dans l’application Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cache/level-two-cache) dans le guide de configuration de Commerce. Pour activer le cache L2 pour l’infrastructure cloud, essayez les méthodes suivantes :
   * Mettre à niveau les outils de l&#39;ECE si la version 2002.1.2 est inférieure.
   * Configurez le cache L2 en utilisant [utiliser la variable REDIS\_BACKEND](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend) et en mettant à jour `.magento.env.yaml` fichier :

   ```yaml
   stage:
      deploy:
          REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
