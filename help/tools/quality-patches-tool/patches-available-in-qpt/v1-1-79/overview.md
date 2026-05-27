---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.79
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.79.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: cfac00d94a7ac89c2a36aa122a18f89e5f77f630
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.79

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.79.

QPT v1.1.79 comprend les correctifs suivants :
1. **ACP2E-4402** : correction d&#39;un problème en raison duquel les produits créés en tant que désactivés n&#39;étaient pas ajoutés aux résultats de [!UICONTROL Target Rule] associés après leur activation.
1. **ACP2E-4505** : corrige le problème en raison duquel il était possible d’enregistrer une catégorie avec des données obsolètes à partir d’un onglet de navigateur en double, créant ainsi une dépendance circulaire.
1. **ACP2E-4531** : correction d’un problème en raison duquel la modification de la clé URL d’une page CMS ne mettait pas à jour l’URL hiérarchique de la page.
1. **[ACP2E-4603](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4603.md)** : correction d’un problème en raison duquel l’exécution de la réindexation du produit [!UICONTROL Catalog Permissions] laissait inchangées les lignes d’index d’autorisation existantes, empêchant la répercussion fiable des autorisations de catégorie mises à jour sur les produits.
1. **[ACP2E-4601](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4601.md)** : corrige le problème en raison duquel le traitement des transactions de paiement pouvait se comporter de manière inefficace sous certaines conditions.
1. **ACP2E-4706** : correction d’un problème en raison duquel les produits non activés dans l’étendue [!UICONTROL Admin] étaient ignorés par l’indexeur de [!UICONTROL Target Rule].
1. **ACP2E-4720** : correction d’un problème en raison duquel la livraison gratuite n’était pas correctement appliquée ni supprimée pour les produits groupés avec des règles de remise sur le panier.
1. **ACP2E-4411** : correction d’un problème en raison duquel un prix incorrect était affiché pour un produit groupé sur la page du panier et dans le mini-panier pour les magasins multidevises.
1. **ACP2E-4475** : correction d’un problème en raison duquel la page de liste des produits filtre et trie incorrectement les produits en rupture de stock par prix lorsque l’option **[!UICONTROL Display Out of Stock Products]** est activée.
1. **ACP2E-4110** : correction du problème en raison duquel les produits groupés à un prix spécial affichaient des montants incorrects sur PDP et PLP dans une devise autre que la devise par défaut.
1. **AC-10698** : correction du problème en raison duquel le système envoyait la devise au niveau de toutes les commandes au lieu de l’associer à des commandes individuelles. Les prix et totaux des transactions sont désormais envoyés par commande à [!DNL Google Tag], ce qui améliore la précision du suivi des données d’e-commerce.
1. **[AC-10737](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/ac-10737.md)** : correction d’un problème en raison duquel la commande `bin/magento setup:db:status` ne reconnaissait pas le type de données JSON.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
