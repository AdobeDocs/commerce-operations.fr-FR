---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.52
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.52.
feature: Tools and External Services
role: Admin, Developer
exl-id: e6fc655e-0809-4b47-8be1-1fc36ae30753
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.52

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.52.

QPT v1.1.52 comprend les correctifs suivants :

1. **ACSD-59366** : corrige le problème en raison duquel une erreur se produit lors de la suppression d’une équipe qui contient des utilisateurs désactivés qui ne sont pas visibles dans la liste des équipes.
1. **ACSD-59865** : permet de résoudre le problème d’un [!UICONTROL Cart Price Rule] qui n’annule pas les règles précédemment appliquées si la quantité de produit dans le panier est insuffisante pour que les règles soient appliquées.
1. **ACSD-59925** : correction d’un problème lié au tri des éléments dans la galerie de médias par position dans GraphQL.
1. **ACSD-59952** : permet de résoudre le problème d’erreur lors de la création d’un catalogue partagé avec un ID de groupe affecté à un catalogue partagé existant.
1. **ACSD-60590** : améliore les performances de génération de *[!UICONTROL Bestsellers Aggregated Daily Reports]* pour un grand volume de commandes passées.
1. **ACSD-60673** : corrige le problème en raison duquel la [!UICONTROL Cart Price Rule] de plusieurs modes de paiement lors du passage en caisse ne s’applique pas correctement au mode de paiement spécifique.
1. **ACSD-60684** : corrige le problème en raison duquel le tri des produits GraphQL par plusieurs champs ne fonctionne pas comme prévu.
1. **ACSD-60788** : corrige le problème où les scripts personnalisés pour les [!DNL Google Tag Manager] ne sont pas exécutés en raison d’erreurs de politique de sécurité du contenu (CSP).
1. **ACSD-61322** : corrige le problème en raison duquel les produits/catégories non affectés au [!UICONTROL Shared Catalog] pour la valeur par défaut (groupe général) sont toujours inclus dans le plan de site XML.
1. **ACSD-61366** : corrige le problème où la commande `setup:static-content:deploy --jobs 4` s’exécute avec plusieurs tâches échouant avec le *Le port doit être configuré dans le paramètre host* erreur lorsque le port est spécifié pour la connexion à la base de données.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
