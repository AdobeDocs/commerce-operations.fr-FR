---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.52'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.52.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: b4b790cee847c83c3acc18fcadb75ccdc6a0898d
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.52

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.52.

QPT v1.1.52 comprend les correctifs suivants :

1. **ACSD-59366** : résolution du problème d’erreur lors de la suppression d’une équipe contenant des utilisateurs désactivés qui ne sont pas visibles dans la liste des équipes.
1. **ACSD-59865** : correction d’un problème en raison duquel [!UICONTROL Cart Price Rule] n’annulait pas les règles précédemment appliquées si la quantité du produit dans le panier n’était pas suffisante pour que les règles soient appliquées.
1. **ACSD-59925** : résolution du problème de tri des éléments dans la galerie multimédia par position dans GraphQL.
1. **ACSD-59952** : résolution du problème d’erreur lors de la création d’un catalogue partagé avec un ID de groupe affecté à un catalogue partagé existant.
1. **ACSD-60590** : améliore les performances de génération de *[!UICONTROL Bestsellers Aggregated Daily Reports]* pour un grand volume de commandes passées.
1. **ACSD-60673** : corrige le problème en raison duquel [!UICONTROL Cart Price Rule] pour plusieurs méthodes de paiement au passage en caisse ne s’applique pas correctement au mode de paiement spécifique.
1. **ACSD-60684** : résolution du problème en raison duquel le tri des produits GraphQL par plusieurs champs ne fonctionne pas comme prévu.
1. **ACSD-60788** : correction du problème en raison duquel les scripts personnalisés pour [!DNL Google Tag Manager] ne sont pas exécutés en raison d’erreurs CSP (Content Security Policy, stratégie de sécurité du contenu).
1. **ACSD-61322** : correction d’un problème en raison duquel les produits/catégories non attribués à [!UICONTROL Shared Catalog] pour la valeur par défaut (groupe général) étaient toujours inclus dans le plan de site XML.
1. **ACSD-61366** : résolution du problème où la commande `setup:static-content:deploy --jobs 4` s’exécute avec plusieurs tâches échouant avec l’erreur *Port doit être configurée dans le paramètre d’hôte* lorsque le port est spécifié pour la connexion DB.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
