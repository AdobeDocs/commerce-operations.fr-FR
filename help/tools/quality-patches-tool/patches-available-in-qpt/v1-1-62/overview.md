---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.62
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.62.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 9bf060c012fa1ddfd966d61792c46cee676a4ea8
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.62

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.62.

QPT v1.1.62 comprend les correctifs suivants :

1. **ACSD-63406** : corrige le problème où les guillemets persistants expirés ne sont effacés par aucune tâche cron lors de l’exécution de la tâche cron `persistent_clear_expired`.
1. **ACSD-63520** : correction du problème en raison duquel les images ajoutées par le biais de **[!UICONTROL Configurations]** dans le panneau d’administration ne respectent pas la limite de taille de chargement maximale.
1. **ACSD-64523** : corrige le problème en raison duquel de nouveaux produits pouvaient être créés sans nom via le processus d’importation (via l’administration ou l’API), ce qui entraînait une interruption de l’interface d’administration et des produits non valides.
1. **ACSD-64532** : corrige le problème en raison duquel une variable ENV définie sur *false* est traitée comme une chaîne *false* au lieu d’une valeur booléenne false.
1. **ACSD-64592** : corrige le problème en raison duquel le lien de réclamation figurant dans l’e-mail pour une carte cadeau dans des magasins non par défaut redirigeait toujours la réclamation de carte cadeau vers le site web par défaut.
1. **ACSD-65164** : corrige le problème où le message d’erreur *Certaines des options d’élément sélectionnées ne sont actuellement pas disponibles* se produit lors de la réorganisation d’un produit configurable avec une seule option personnalisée de case à cocher sélectionnée.
1. **ACSD-64732** : corrige le problème en raison duquel les contrôleurs tiers n’étaient pas correctement mis en cache avec les segments clients.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
