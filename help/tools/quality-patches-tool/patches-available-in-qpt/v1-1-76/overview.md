---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.76'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.76.
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
source-wordcount: '484'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.76

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.76.

QPT v1.1.76 comprend les correctifs suivants :
1. **[ACSD-67091](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67091.md)** : corrige l’erreur de taille maximale de l’ensemble d’écriture pour garantir le nettoyage de l’index de produit des règles de catalogue en implémentant deux stratégies de suppression en fonction du volume de données.
1. **[ACSD-67370](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67370.md)** : corrige plusieurs problèmes en raison desquels des prix incorrects étaient affichés pour les produits groupés sur PDP/PLP et la page du panier pour les magasins multidevises.
1. **[ACSD-68410](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-68410.md)** : correction d’un problème en raison duquel la commande d’un devis négociable ajoute ou fusionne incorrectement des lignes de panier supplémentaires dans le devis. Les produits sont désormais correctement ajoutés au panier après avoir quitté la dernière étape de passage en caisse de devis négociable.
1. **[ACSD-69086](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69086.md)** : corrige un problème en raison duquel la tâche cron ne parvenait pas à effacer les tables de journal des modifications, provoquant des blocages de [!DNL Galera Cluster] lors de la gestion de grandes quantités de données.
1. **[ACSD-69115](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69115.md)** : correction d’un problème en raison duquel les erreurs de panier n’étaient pas affichées pour l’utilisateur administrateur lors de la gestion du panier pour un client affecté à un site web autre que celui par défaut.
1. **[ACSD-69129](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69129.md)** : correction d’un problème en raison duquel la suppression du site web de base par défaut et l’utilisation du site web secondaire en tant que site web par défaut entraînaient une erreur lors de la tentative de mise à jour du prix de niveau pour le site web secondaire via l’API [!DNL REST].
1. **[ACSD-69203](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69203.md)** : correction d’un problème en raison duquel le widget **[!UICONTROL Products List]** renvoyait des résultats incorrects lorsque plusieurs catégories étaient répertoriées dans la condition de catégorie.
1. **[ACSD-69261](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69261.md)** : correction d’un problème en raison duquel un coupon de règle de prix de panier configuré pour une utilisation unique par client a été réutilisé plusieurs fois en raison d’une gestion incorrecte de l’attribut `times_used` dans les scénarios d’annulation de facture partielle et de quantité restante.
1. **[ACSD-69308](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69308.md)** : correction d’un problème en raison duquel les règles de prix de catalogue ne s’appliquaient pas lorsque `special_price` était défini uniquement au niveau du site web (et non au **[!UICONTROL All Store Views]**). Après la correction, les règles de prix de catalogue s’appliquent correctement en vérifiant d’abord le magasin par défaut du site web.
1. **[ACSD-69319](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69319.md)** : correction d’un problème en raison duquel les prix des offres groupées n’étaient pas correctement indexés lorsque les produits enfants étaient en stock sous des sources personnalisées.
1. **[ACSD-69325](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69325.md)** : correction d’un problème en raison duquel la modification du boîtier de SKU provoquait une rupture de stock du produit sur le storefront.
1. **[ACSD-69331](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69331.md)** : correction d’un problème en raison duquel les créateurs de contenu de la galerie multimédia ne pouvaient pas créer de dossiers avec uniquement l’autorisation `create_folder`. Après le correctif, ils peuvent créer des dossiers comme prévu.
1. **[ACSD-69333](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69333.md)** : correction d’un problème en raison duquel les modifications de SKU étaient autorisées pour les produits avec une mise à jour planifiée active. Après la correction, les modifications de SKU sont interdites pendant les mises à jour actives ; les enregistrements échouent avec une erreur claire et le champ SKU d’administration est désactivé. Cela évite les incohérences d’inventaire MSI dues aux modifications de SKU lors des restaurations intermédiaires.
1. **[ACSD-69541](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69541.md)** : correction d’un problème en raison duquel la réduction de la quantité d’un produit dans le [!UICONTROL Admin] à une quantité inférieure à celle qui existe déjà dans un panier rendait impossible la modification de la quantité de ce produit dans ce panier via GraphQL.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
