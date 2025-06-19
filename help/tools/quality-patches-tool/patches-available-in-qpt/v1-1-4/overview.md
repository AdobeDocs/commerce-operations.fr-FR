---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.4
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.4.
feature: Tools and External Services
role: Admin
exl-id: 67e87ea1-196a-4bc1-ae9d-f3f1184b4986
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Présentation d’[!DNL Quality Patches Tool] (QPT) v1.1.4

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.4.

QPT v1.1.4 comprend les correctifs suivants :

1. **MC-42528** : correction du problème en raison duquel la requête `categoryList` GraphQL renvoie à la fois les catégories affectées et non affectées.
1. **MDVA-25631** : améliore les performances pour la modification et l’enregistrement des segments de clients qui contiennent un grand nombre de clients.
1. **MDVA-26005** : corrige le problème en raison duquel il est impossible de sélectionner une catégorie dans une arborescence de catégories pour les conditions de la règle Prix du panier.
1. **MDVA-29400** : correction du problème lié aux commandes dupliquées passées avec [!DNL PayPal Express Checkout].
1. **MDVA-37725** : correction du problème en raison duquel les e-mails de commande asynchrones envoyés à partir de sites web non par défaut contiennent des URL de logo provenant du site web par défaut.
1. **MDVA-39482** : corrige le problème de rupture de stock d’un produit importé avec une quantité « 0 » lorsque les commandes en souffrance sont activées.
1. **MDVA-40101** : corrige le problème où les articles ne sont pas supprimés du mini panier après un placement de commande réussi à l’aide du passage en caisse [!DNL PayPal Express].
1. **MDVA-40399** : correction du problème en raison duquel les factures partielles d’une même commande ne peuvent pas être créées simultanément via l’API REST.
1. **MDVA-40401** : correction du problème en raison duquel la valeur d’utilisation des coupons change même en cas d’échec de la commande.
1. **MDVA-40435** : corrige le problème avec une remise incorrecte sur les produits groupés avec des prix dynamiques lorsqu’ils sont appliqués via GraphQL.
1. **MDVA-40537** : corrige le problème où les utilisateurs et utilisatrices reçoivent une erreur lors de la création d’une vue de magasin s’il existe plusieurs pages CMS avec la même clé URL.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
