---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.25'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.25.
feature: Tools and External Services
role: Admin
exl-id: a9953394-b2dd-4e07-a280-378bef2b9b0f
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%
---
# Présentation d’[!DNL Quality Patches Tool] (QPT) v1.1.25

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.25.

QPT v1.1.25 comprend les correctifs suivants :

1. **ACSD-47292** : corrige le problème en raison duquel les produits en rupture de stock ne sont pas disponibles dans la réponse GraphQL si l’option *Afficher les produits en rupture de stock* est définie sur *Oui*.
1. **ACSD-47520** : corrige le problème en raison duquel les clients perdent des points de récompense lors de la création d’un avoir.
1. **ACSD-47910** : corrige le problème des commandes, factures, expéditions et avoirs manquants dans les grilles d&#39;entités respectives.
1. **ACSD-48044** : corrige le problème en raison duquel l’application de plusieurs cartes-cadeaux à une seule commande avec expédition multiple empêche le passage de commandes.
1. **ACSD-48058** : corrige le problème en raison duquel la réindexation du prix du produit ne fonctionne pas si le produit groupé n’est affecté à aucun site web.
1. **ACSD-48234** : corrige le problème en raison duquel le résultat de la recherche catalogue affiche un nombre d’éléments de catégorie incorrect lorsque l’option *Afficher en rupture de stock* est activée.
1. **ACSD-48262** : corrige le problème en raison duquel les produits ne sont pas visibles sur le front-end lorsque *[!UICONTROL Allow All Products Per Page]* paramètre est défini sur *Oui*.
1. **ACSD-48293** : corrige le problème de rupture de stock des produits composites lorsque les produits enfants qui ont été vendus sont remis en stock.
1. **ACSD-48300** : corrige le problème en raison duquel un retour ne peut pas être créé si le produit configurable est supprimé.
1. **ACSD-48313** : corrige le problème en raison duquel la colonne *configurable_variations* n’est pas analysée si la valeur de l’attribut contient une virgule. Le même algorithme d’analyse est utilisé pour *additional_attributes*.
1. **ACSD-48627** : corrige le problème en raison duquel le produit configurable en rupture de stock provoque une erreur lors de l’envoi d’une requête GraphQL pour obtenir les détails du panier.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
