---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.33'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.33.
feature: Tools and External Services
role: Admin
exl-id: 31812668-1d24-4da6-992f-981c259e00da
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
source-wordcount: '453'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.33

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.33.

QPT v1.1.33 comprend les correctifs suivants :

1. **ACSD-50478** : corrige la commande de restauration de la base de données dans le cas où l’image mémoire de la base de données contient des déclencheurs et une commande SQL de délimiteur.
1. **ACSD-50512** : corrige l&#39;erreur : *Le lien téléchargeable n&#39;est pas associé au produit. Vérifiez le lien et réessayez.*  cela se produit lors de la mise à jour de la date de début d’une mise à jour d’évaluation de produit téléchargeable.
1. **ACSD-50949** : corrige le problème où le filtre de prix dans [!UICONTROL Advanced Search] ne renvoie pas les résultats appropriés lorsqu’il est utilisé avec le filtre de SKU.
1. **ACSD-51645** : corrige l’erreur générée lors de l’enregistrement d’un nouveau [!UICONTROL Cart Price Rule] si le `Magento_OfflineShipping` d’extension est désactivé.
1. **ACSD-50895** : corrige le problème en raison duquel les balises [!DNL Google Analytics] 3 GTM ne sont pas déclenchées si [!DNL Google Analytics] 4 GTM n’est pas configuré.
1. **ACSD-51102** : corrige le problème où une règle de catalogue appliquée à un grand nombre de produits n’est pas correctement indexée lorsque la règle est activée par une mise à jour planifiée.
1. **ACSD-50368** : corrige le problème en raison duquel le `group_id` du client est ignoré lorsqu’un client est créé via l’API Async REST ou l’API Async Bulk REST.
1. **ACSD-51497** : corrige le problème en raison duquel un client ne peut pas trier une page de catalogue par [!UICONTROL Custom Attribute] du type de liste déroulante.
1. **ACSD-51408** : corrige le problème en raison duquel le statut de l’élément de commande est incorrectement défini sur [!UICONTROL Backordered].
1. **ACSD-51735** : corrige le problème en raison duquel le statut de l’article de commande est incorrectement défini sur [!UICONTROL Ordered] lorsque le stock de produits est *0*.
1. **ACSD-51792** : corrige le problème en raison duquel une page ne comporte pas d’événement d’impression lorsque le [!DNL Google Tag Manager] 4 est activé.
1. **ACSD-51471** : corrige le problème en raison duquel un utilisateur administrateur ne peut pas enregistrer une mise à jour planifiée pour un produit groupé qui utilise un produit simple doté lui-même d’une mise à jour planifiée.
1. **ACSD-51700** : corrige l’erreur qui se produit lors du changement de vue de la boutique sur une page de modification de produit téléchargeable par l’administrateur.
1. **ACSD-51120** : corrige le problème où le cache des requêtes GraphQL GET n’est pas effacé pour les pages CMS qui contiennent des blocs CMS mis à jour via une mise à jour d’évaluation.
1. **ACSD-51240** : corrige le problème en raison duquel le fichier chargé est manquant si l’enregistrement est effectué via le formulaire d’enregistrement de l’entreprise.
1. **ACSD-51907** : corrige le problème en raison duquel un utilisateur administrateur restreint ne peut pas créer d’avoir avec remboursement hors ligne.
1. **ACSD-52148** : corrige le problème d’échec occasionnel de la connexion au [!UICONTROL Google V3 reCAPTCHA Admin].
1. **ACSD-51431** : corrige le problème de fonctionnement du statut d’un indexeur même s’il n’existe aucune nouvelle entrée dans le journal des modifications.
1. **ACSD-51892** : corrige le problème de performances en raison duquel les fichiers de configuration se chargent plusieurs fois pendant le déploiement.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
