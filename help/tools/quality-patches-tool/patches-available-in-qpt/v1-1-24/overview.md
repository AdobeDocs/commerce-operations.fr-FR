---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.24'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.24.
feature: Tools and External Services
role: Admin
exl-id: 7f88a28b-f166-4c5b-8d69-239c57cc4001
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
source-wordcount: '296'
ht-degree: 0%
---
# Présentation d’[!DNL Quality Patches Tool] (QPT) v1.1.24

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.24.

QPT v1.1.24 comprend les correctifs suivants :

1. **ACSD-45168** : corrige le problème où les URL compatibles avec l’optimisation du moteur de recherche ne sont pas générées pour les produits dont les attributs *url_key* sont remplacés au niveau de la vue du magasin.
1. **ACSD-46617** : corrige le problème en grisé du bouton **[!UICONTROL Continue to Checkout]** même si le sous-total est supérieur au *Montant minimum de commande* configuré.
1. **ACSD-46770** : corrige le problème d’envoi des e-mails de commande de l’administrateur même lorsque la case *Confirmation de commande par e-mail* n’est pas cochée.
1. **ACSD-46865** : corrige le problème en raison duquel la grille de [!UICONTROL Shipment and Credit Memo] n’est pas renseignée lorsque l’indexation asynchrone est activée.
1. **ACSD-47004** : corrige le problème en raison duquel la TVA n’est pas appliquée à une adresse de facturation sans numéro de TVA.
1. **ACSD-47079** : corrige le problème en raison duquel l’état du stock des produits composites (groupés, groupés et configurables) n’est pas mis à jour lorsque l’état du stock des sous-produits change via l’API REST POST /rest/V1/inventory/source-items.
1. **ACSD-47137** : améliore la vitesse de chargement de la galerie d&#39;images lorsque le dossier pub/media est très volumineux.
1. **ACSD-47336** : correctifs *Un problème est survenu.* Erreur lors de l’ignorance des notifications dans Commerce Admin.
1. **ACSD-47559** : corrige le problème en raison duquel la zone Prévisualiser le modèle d’e-mail n’est pas entièrement visible.
1. **ACSD-47803** : correction du problème d’affichage des échantillons de produits configurables en rupture de stock.
1. **ACSD-47920** : corrige le problème où des commandes peuvent être passées via l’API REST en tant qu’utilisateur invité, même si l’option *Autoriser le passage en caisse des invités* est désactivée.
1. **ACSD-47955** : corrige le problème en raison duquel GraphQL n’affiche pas correctement la remise du panier.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
