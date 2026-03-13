---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.76
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.76.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: d852c8dc40d061b878daf25aac0c7cf57628954c
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.76

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.76.

QPT v1.1.76 comprend les correctifs suivants :
1. **[ACSD-67370](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67370.md)** : corrige plusieurs problèmes en raison desquels des prix incorrects étaient affichés pour les produits groupés sur PDP/PLP et la page du panier pour les magasins multidevises.
1. **[ACSD-67091](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67091.md)** : corrige l’erreur de taille maximale de l’ensemble d’écriture pour garantir le nettoyage de l’index de produit des règles de catalogue en implémentant deux stratégies de suppression en fonction du volume de données.
1. **[ACSD-68410](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-68410.md)** : correction d’un problème en raison duquel la commande d’un devis négociable ajoute ou fusionne incorrectement des lignes de panier supplémentaires dans le devis. Les produits sont désormais correctement ajoutés au panier après avoir quitté la dernière étape de passage en caisse de devis négociable.
1. **ACSD-69086** : corrige le problème en raison duquel la tâche cron ne parvient pas à effacer les tables de journal des modifications, provoquant des blocages de [!DNL Galera Cluster] lors de la gestion de grandes quantités de données.
1. **ACSD-69115** : correction d’un problème en raison duquel les erreurs de panier n’étaient pas affichées pour l’utilisateur administrateur lors de la gestion du panier pour un client affecté à un site web autre que celui par défaut.
1. **[ACSD-69203](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69203.md)** : correction d’un problème en raison duquel le widget **[!UICONTROL Products List]** renvoie des résultats incorrects lorsque plusieurs catégories étaient répertoriées dans la condition de catégorie.
1. **[ACSD-69129](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69129.md)** : correction d’un problème en raison duquel la suppression du site web de base par défaut et l’utilisation du site web secondaire en tant que site web par défaut entraînaient une erreur lors de la tentative de mise à jour du prix de niveau du site web secondaire via l’API [!DNL REST].
1. **ACSD-69203** : correction d’un problème en raison duquel le widget **[!UICONTROL Products List]** renvoie des résultats incorrects lorsque plusieurs catégories étaient répertoriées dans la condition de catégorie.
1. **[ACSD-69261](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69261.md)** : correction d’un problème en raison duquel un coupon de règle de prix de panier configuré pour une utilisation unique par client a été réutilisé plusieurs fois en raison d’une gestion incorrecte de l’attribut `times_used` dans les scénarios d’annulation de facture partielle et de quantité restante.
1. **ACSD-69308** : correction d’un problème en raison duquel les règles de prix de catalogue ne s’appliquaient pas lorsque `special_price` était défini uniquement au niveau du site web (et non au **[!UICONTROL All Store Views]**). Après la correction, les règles de prix de catalogue s’appliquent correctement en vérifiant d’abord le magasin par défaut du site web.
1. **ACSD-69261** : correction d’un problème en raison duquel un coupon de règle de prix de panier configuré pour une utilisation unique par client a été réutilisé plusieurs fois en raison d’une gestion incorrecte de l’attribut `times_used` dans les scénarios d’annulation de facture partielle et de quantité restante.
1. **[ACSD-69308](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69308.md)** : correction d’un problème en raison duquel les règles de prix de catalogue ne s’appliquaient pas lorsque `special_price` était défini uniquement au niveau du site web (et non au **[!UICONTROL All Store Views]**).
1. **ACSD-69319** : correction d’un problème en raison duquel les prix des offres groupées n’étaient pas correctement indexés lorsque les produits enfants étaient en stock sous des sources personnalisées.
1. **[ACSD-69325](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69325.md)** : correction d’un problème en raison duquel la modification du boîtier de SKU provoquait une rupture de stock du produit sur le storefront.
1. **ACSD-69331** : correction d’un problème en raison duquel les créateurs de contenu de la galerie multimédia ne pouvaient pas créer de dossiers avec uniquement l’autorisation `create_folder`. Après le correctif, ils peuvent créer des dossiers comme prévu.
1. **[ACSD-69541](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69541.md)** : correction d’un problème en raison duquel la réduction de la quantité d’un produit dans le [!UICONTROL Admin] à une quantité inférieure à la quantité précédente dans un panier arrêtait la possibilité de modifier la quantité du produit dans ce panier via GraphQL.
1. **[ACSD-69333](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69333.md)** : correction d’un problème en raison duquel les modifications de SKU étaient autorisées pour les produits avec une mise à jour planifiée active. Après la correction, les modifications de SKU sont interdites pendant les mises à jour actives ; les enregistrements échouent avec une erreur claire et le champ SKU d’administration est désactivé. Cela évite les incohérences de l&#39;inventaire MSI dues aux modifications de SKU lors des restaurations intermédiaires.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
