---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.54'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.54.
feature: Tools and External Services
role: Admin, Developer
exl-id: 1496d15e-edf9-4be0-8e14-ebb2de6f12fe
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
source-wordcount: '300'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.54

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.54.

QPT v1.1.54 comprend les correctifs suivants :

1. **ACSD-60267** : corrige le problème en raison duquel la Taxe fixe sur les produits (FPT) s’applique correctement lors de l’ajout de produits simples avec FPT directement au panier, mais échoue lors de la sélection de ces produits par le biais d’options de produits configurables.
1. **ACSD-61103** : corrige le problème où le nombre d’échecs dans la table `customer_entity` n’est pas réinitialisé à zéro après qu’un client s’est connecté avec succès via les points d’entrée de l’API.
1. **ACSD-61134** : corrige le problème en raison duquel le mode de paiement [!DNL Braintree Vault] est automatiquement désélectionné dans le workflow de passage en caisse lorsqu’un acheteur met à jour son adresse de facturation en décochant la case *[!UICONTROL My billing and shipping address are the same]*.
1. **ACSD-61199** : correction d’un problème en raison duquel l’onglet de hiérarchie de page CMS n’affichait pas une arborescence appropriée lors de la modification d’une page CMS avec une hiérarchie existante.
1. **ACSD-61200** : corrige le problème en raison duquel les *[!UICONTROL Discount Tax Compensation Amount]* et les *[!UICONTROL Shipping Discount Tax Compensation Amount]* des calculs pour les *[!UICONTROL Total Amount]* et les *[!UICONTROL Total Amount Actual]* dans les ventes n&#39;apparaissent pas, ce qui entraîne des incohérences dans les données des commandes client.
1. **ACSD-61522** : corrige le problème en raison duquel il est possible de saisir des adresses e-mail dans les champs *[!UICONTROL First Name]* et *[!UICONTROL Last Name]* du client invité et d’envoyer des e-mails de confirmation de commande non valides.
1. **ACSD-61756** : améliore les performances des filtres `AdvancedSalesRule`.
1. **ACSD-61799** : correction d’un problème en raison duquel la remise totale n’est pas correctement calculée lorsque plusieurs règles de panier avec des remises fixes sont appliquées au devis.
1. **ACSD-61845** : corrige l’erreur qui se produit lorsqu’une requête est envoyée avec uniquement un en-tête *text/html* accept.
1. **ACSD-62056** : corrige le problème d’échec du chargement des images d’un produit configurable si MSI est installé.
1. **ACSD-62485** : corrige le problème où `async.operations.all` consommateur cesse de fonctionner lorsqu’une entreprise est créée.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
