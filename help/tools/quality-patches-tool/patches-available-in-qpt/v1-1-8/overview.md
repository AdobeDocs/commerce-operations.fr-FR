---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.8
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.8.
feature: Tools and External Services
role: Admin
exl-id: bcc35189-bed7-4076-bd9e-3d4ca47b3215
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 0%

---

# Présentation d’[!DNL Quality Patches Tool] (QPT) v1.1.8

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.8.

QPT v1.1.8 comprend les correctifs suivants :

1. **MDVA-38393** : correction du problème en raison duquel les règles de catalogue ne fonctionnent plus pour un produit configurable si son produit simple est renommé.
1. **MDVA-39153** : correction d’un problème en raison duquel un montant de remise n’est pas calculé correctement lors de la réorganisation dans l’administration.
1. **MDVA-41139** : correction du problème en raison duquel les produits configurables sont en rupture de stock après l’importation d’un produit lorsque la quantité=0 d’un produit simple pour l’une de ses sources est affectée.
1. **MDVA-41215** : corrige le problème où les utilisateurs obtiennent l’erreur 500 après avoir défini le cookie *mage-messages* s’il existe déjà, mais qu’il n’existe aucun nouveau message.
1. **MDVA-42326** : corrige le problème où les clients obtiennent une erreur lors du passage en caisse après une temporisation de session, même si le panier persistant est activé.
1. **MDVA-42341** : permet de résoudre le problème en raison duquel la requête `categoryList` GraphQL ne filtre pas les résultats si une requête comporte l’en-tête Store .

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
