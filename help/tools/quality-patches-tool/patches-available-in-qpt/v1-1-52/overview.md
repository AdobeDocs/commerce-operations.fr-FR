---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.52'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.52.
feature: Tools and External Services
role: Admin, Developer
exl-id: e6fc655e-0809-4b47-8be1-1fc36ae30753
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
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
source-wordcount: '284'
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
