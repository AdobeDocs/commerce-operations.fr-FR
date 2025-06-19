---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.55
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.55.
feature: Tools and External Services
role: Admin, Developer
exl-id: a4895d1b-e8d0-458e-81c8-4b892c116de6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.55

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.55.

QPT v1.1.55 comprend les correctifs suivants :

1. **ACSD-58383** : corrige le problème en raison duquel l’émission d’un remboursement via le [!DNL REST API] avec deux demandes identiques exécutées simultanément crée des avoirs en double.
1. **ACSD-58471** : corrige le problème en raison duquel le contenu dynamique ne se charge pas sur la page des détails du produit lorsque les règles de prix de catalogue associées sont planifiées.
1. **ACSD-58566** : corrige le problème où [!DNL GraphQL] renvoie une erreur de serveur interne lors de l’interrogation du champ `created_at` dans la mutation `addPurchaseOrderComment`.
1. **ACSD-58685** : corrige le problème où les e-mails de vente déclenchés alors que la communication par e-mail est désactivée sont toujours envoyés une fois que la communication par e-mail est réactivée.
1. **ACSD-58735** : corrige le problème en raison duquel un administrateur restreint ne peut pas afficher les paniers abandonnés sur la page du compte client dans la [!UICONTROL Admin] d’un site web associé.
1. **ACSD-58828** : corrige le problème en raison duquel le message de validation côté serveur *address est obligatoire* s’affiche si un champ obligatoire reste vide, à côté du message de validation côté client. La validation côté serveur n’affiche pas le message pour les champs obligatoires vides, et la validation côté client gère la notification d’erreur, en indiquant *Ceci est un champ obligatoire*.
1. **ACSD-60344** : correction du problème d’envoi des e-mails de confirmation de commande en double lors de l’utilisation d’un **[!UICONTROL Purchase Order]** avec approbation automatique.
1. **ACSD-61348** : corrige le problème où les éléments de liste de souhaits sont visibles via [!DNL GraphQL], mais pas sur le storefront dans un environnement multi-sites web.
1. **ACSD-61534** : corrige le problème en raison duquel la configuration de conception ne peut pas être définie à l’aide de la commande `bin/magento config:set` et les valeurs verrouillées peuvent être modifiées par la manipulation du formulaire. Désormais, les valeurs verrouillées définies à partir du [!DNL CLI] avec `--lock-env` ou `--lock-conf` ne peuvent pas être mises à jour.
1. **ACSD-61785** : corrige le problème en raison duquel la mise à jour de l’attribut `reward_warning_notification` n’est pas possible via [!DNL GraphQL] mutation et les appels de [!DNL REST API], ce qui permet d’aligner son comportement avec les `reward_update_notification`.
1. **ACSD-62591** : correction d’un problème en raison duquel le thème ne change pas correctement lors de la configuration des **[!UICONTROL User Agent Rules]**.
1. **ACSD-62793** : corrige le problème en raison duquel les attributs de `datetime` dans les données exportées n’incluent pas le composant Heure. De plus, si *[!UICONTROL Fields Enclosure]* est *activé*, les valeurs d’attribut de la colonne `additional_attributes` sont placées entre guillemets doubles.
1. **ACSD-62332** : corrige le problème en raison duquel la requête de [!DNL GraphQL] de liste de produits est limitée à un `total_count` de 10 000 produits. Correction également du problème en raison duquel [!DNL Live Search] définit la page active sur *1* au lieu de la page *2* dans les critères de recherche lors de l’interrogation via [!DNL GraphQL].

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
