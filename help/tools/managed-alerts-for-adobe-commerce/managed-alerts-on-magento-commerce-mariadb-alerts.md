---
title: 'Alertes gérées sur Adobe Commerce : alertes MariaDB'
description: Cet article décrit les étapes de dépannage à suivre lorsque vous recevez des alertes MariaDB pour Adobe Commerce dans  [!DNL New Relic]. Les alertes MariaDB surveillent une charge de requête élevée ainsi que des requêtes DML (Data Manipulation Language) excessives. Ces deux éléments peuvent dégrader l’expérience utilisateur, voire entraîner des temps d’arrêt. Vous pouvez recevoir deux types d’alertes.
feature: Cache, Observability, Support, Tools and External Services
role: Admin
exl-id: d85af2e1-090c-4ad7-a898-3a3c4a5efe3b
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Alertes gérées sur Adobe Commerce : alertes MariaDB

Cet article décrit les étapes de dépannage à suivre lorsque vous recevez des alertes MariaDB pour Adobe Commerce dans [!DNL New Relic]. Les alertes MariaDB surveillent une charge de requête élevée ainsi que des requêtes DML (Data Manipulation Language) excessives. Ces deux éléments peuvent dégrader l’expérience utilisateur, voire entraîner des temps d’arrêt. Vous pouvez recevoir deux types d’alertes :

* Avertissement relatif aux requêtes DML
* Requêtes DML critiques

## Produits et versions concernés

Architecture de plan Pro d’Adobe Commerce sur les infrastructures cloud

## Problème

Vous recevrez une alerte gérée en [!DNL New Relic] si vous vous êtes inscrit aux [alertes gérées pour Adobe Commerce](managed-alerts-for-magento-commerce.md) et qu’un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe pour fournir aux clients un ensemble de normes à l’aide des informations provenant des services d’assistance et d’ingénierie.

**Faites !**

* Abandonner tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Mettez immédiatement votre site en mode de maintenance s’il ne répond plus du tout. Pour connaître les étapes, reportez-vous à la section [Activation ou désactivation du mode de maintenance](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans le Guide d’installation de Commerce. Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées pour vous assurer que vous pouvez toujours accéder à votre site à des fins de dépannage. Pour connaître les étapes, voir [Tenir à jour la liste des adresses IP exemptées](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses).
* Arrêtez tous les scripts tels que les imports qui peuvent être à l’origine de l’alerte en cas d’impact sur les performances du site.

**Non !**

* Exécutez des indexeurs ou des crons supplémentaires qui peuvent entraîner une contrainte supplémentaire sur MariaDB.
* Effectuez toutes les tâches administratives majeures (c’est-à-dire Administration de Commerce, importations/exportations de données).
* Videz votre cache.

## Solution

**Requêtes DML (requêtes qui modifient la base de données à l&#39;aide de UPDATE, INSERT et DELETE)**

Si vous recevez une alerte critique de requêtes DML, commencez à l’étape 1. Si vous recevez une alerte d’avertissement de requêtes DML, commencez à l’étape 2.

1. Vérifiez si un ticket d’assistance Adobe Commerce existe. Pour connaître les étapes à suivre, consultez notre base de connaissances [Suivre vos tickets d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case). L’assistance peut avoir reçu une alerte de seuil [!DNL New Relic], créé un ticket et commencé à travailler sur le problème. S’il n’existe aucun ticket, créez-en un. Le ticket doit contenir les informations suivantes :
   * Motif du contact : sélectionnez **[!UICONTROL New Relic MariaDB alert received]**.
   * Description de l’alerte.
   * [[!DNL New Relic] Lien de l’incident](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Cela est inclus dans vos [alertes gérées pour Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Pour identifier la source du problème, essayez d’identifier les requêtes XML :
   1. Examinez les opérations de base de données à l’aide des étapes de la page New Relic [Bases de données](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time).
   1. Triez par **[!UICONTROL CALL COUNT]**, puis par **[!UICONTROL OPERATION]**. Examinez les opérations `INSERT`, `DELETE` et `UPDATE`.
   1. Recherchez un MOY élevé.
   1. Cliquez sur pour rechercher les appelants des opérations de base de données. Cette opération identifie les transactions à l’aide de cette requête par heure.
   1. Recherchez des optimisations de code ou des optimisations opérationnelles :
      * Optimisations du code : cherchez à optimiser les requêtes avec des insertions/mises à jour en bloc, en réduisant l’utilisation de l’index ou en limitant le code.
      * Optimisations opérationnelles : déchargez les modifications de données gourmandes en ressources pour réduire les temps de trafic.
      * Optimisations supplémentaires : Assurez-vous d&#39;utiliser la dernière version des outils ECE. Pour connaître les étapes, reportez-vous à la section [Mise à jour de la version des outils](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) dans le guide Commerce sur le cloud .
