---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.79'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.79.
feature: Tools and External Services
role: Admin, Developer
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
source-wordcount: '320'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.79

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.79.

QPT v1.1.79 comprend les correctifs suivants :
1. **[ACP2E-4402](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4402.md)** : correction d&#39;un problème en raison duquel les produits créés en tant que désactivés n&#39;étaient pas ajoutés aux résultats de [!UICONTROL Target Rule] associés après leur activation.
1. **[ACP2E-4505](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4505.md)** : corrige le problème en raison duquel il était possible d’enregistrer une catégorie avec des données obsolètes à partir d’un onglet de navigateur en double, créant ainsi une dépendance circulaire.
1. **[ACP2E-4531](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4531.md)** : correction d’un problème en raison duquel la modification de la clé URL d’une page CMS ne mettait pas à jour l’URL hiérarchique de la page.
1. **[ACP2E-4601](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4601.md)** : corrige le problème en raison duquel le traitement des transactions de paiement pouvait se comporter de manière inefficace sous certaines conditions.
1. **[ACP2E-4603](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4603.md)** : correction d’un problème en raison duquel l’exécution de la réindexation du produit [!UICONTROL Catalog Permissions] laissait inchangées les lignes d’index d’autorisation existantes, empêchant la répercussion fiable des autorisations de catégorie mises à jour sur les produits.
1. **[ACP2E-4706](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4706.md)** : correction du problème en raison duquel les produits non activés dans la portée d’administration étaient ignorés par l’indexeur de [!UICONTROL Target Rule].
1. **[ACP2E-4720](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4720.md)** : correction d’un problème en raison duquel la livraison gratuite n’était pas correctement appliquée ni supprimée pour les produits groupés avec des règles de remise sur le panier.
1. **[ACP2E-4475](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4475.md)** : correction d’un problème en raison duquel la page de liste des produits filtre et trie incorrectement les produits en rupture de stock par prix lorsque l’option [!UICONTROL Display Out of Stock Products] est activée.
1. **[AC-10698](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/ac-10698.md)** : correction du problème en raison duquel le système envoyait la devise au niveau de toutes les commandes au lieu de l’associer à des commandes individuelles.
1. **[ACP2E-4411](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4411.md)** : correction d’un problème en raison duquel un prix incorrect était affiché pour un produit groupé sur la page du panier et dans le mini-panier pour les magasins multidevises.
1. **[ACP2E-4110](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4110.md)** : correction du problème en raison duquel les produits groupés avec un **[!UICONTROL Special Price]** affichent des montants incorrects sur le PDP et le PLP dans une devise autre que la devise par défaut.
1. **[AC-10737](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/ac-10737.md)** : correction d’un problème en raison duquel la commande `bin/magento setup:db:status` ne reconnaissait pas le type de données JSON.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
