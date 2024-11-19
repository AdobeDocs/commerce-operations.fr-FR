---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.55'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.55.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 97b52220f3b254ee17705a22137693abc6008c72
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.55

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.5.

QPT v1.1.55 comprend les correctifs suivants :

1. **ACSD-58383** : résolution du problème d’émission d’un remboursement via l’ [!DNL REST API] avec deux demandes identiques exécutées simultanément, créant des notes de crédit en double.
1. **ACSD-58471** : résolution du problème de l’échec du chargement du contenu dynamique sur la page des détails du produit lorsque les règles de prix du catalogue associées sont planifiées.
1. **ACSD-58566** : résolution du problème en raison duquel [!DNL GraphQL] renvoie une erreur de serveur interne lors de l’interrogation du champ `created_at` dans la mutation `addPurchaseOrderComment`.
1. **ACSD-58685** : correction du problème en raison duquel les courriers électroniques de vente démarrés alors que la communication par courrier électronique est désactivée étaient toujours envoyés une fois la communication par courrier électronique réactivée.
1. **ACSD-58735** : correction d’un problème en raison duquel un administrateur restreint ne pouvait pas afficher les paniers abandonnés sur la page du compte client dans [!UICONTROL Admin] pour un site Web associé.
1. **ACSD-58828** : résolution du problème de l’affichage du message de validation côté serveur *address is required* si un champ obligatoire est vide, avec le message de validation côté client. La validation côté serveur n’affiche pas le message pour les champs obligatoires vides, et la validation côté client gère la notification d’erreur, indiquant *C’est un champ obligatoire.*
1. **ACSD-60344** : résolution du problème d’envoi d’emails de confirmation de commande en double lors de l’utilisation d’un **[!UICONTROL Purchase Order]** avec approbation automatique.
1. **ACSD-61348** : correction d’un problème en raison duquel les éléments de liste bloquée étaient visibles via [!DNL GraphQL], mais pas sur le storefront dans un environnement multi-site.
1. **ACSD-61534** : corrige le problème en raison duquel la configuration de conception ne peut pas être définie à l’aide de la commande `bin/magento config:set` et les valeurs verrouillées peuvent être modifiées par la manipulation de formulaire. Désormais, les valeurs verrouillées définies à partir de [!DNL CLI] avec `--lock-env` ou `--lock-conf` ne peuvent pas être mises à jour.
1. **ACSD-61785** : corrige le problème en raison duquel la mise à jour de l’attribut `reward_warning_notification` n’est pas possible par le biais d’appels [!DNL GraphQL] et de mutation, alignant son comportement sur `reward_update_notification`.[!DNL REST API]
1. **ACSD-62591** : corrige le problème en raison duquel le thème ne bascule pas correctement lorsque **[!UICONTROL User Agent Rules]** est configuré.
1. **ACSD-62793** : résolution du problème en raison duquel les attributs `datetime` dans les données exportées n’incluent pas le composant de temps. En outre, si *[!UICONTROL Fields Enclosure]* est *activé*, les valeurs d’attribut dans la colonne `additional_attributes` sont incluses dans des guillemets doubles.
1. **ACSD-62332** : résolution du problème en raison duquel la requête [!DNL GraphQL] de la liste de produits est limitée à `total_count` sur 10 000 produits. Correction également du problème en raison duquel [!DNL Live Search] définit la page active sur *1* au lieu de la page *2* dans les critères de recherche lors d’une requête via [!DNL GraphQL].

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
