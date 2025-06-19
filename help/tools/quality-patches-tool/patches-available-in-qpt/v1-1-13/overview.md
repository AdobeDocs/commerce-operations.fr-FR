---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.13
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.13.
feature: Tools and External Services
role: Admin
exl-id: 61f8a517-1a50-4d51-b576-38ae29a7ca32
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Présentation d’[!DNL Quality Patches Tool] (QPT) v1.1.13

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.13.

QPT v1.1.13 comprend les correctifs suivants :

1. **MDVA-39605** : correction d’un problème en raison duquel [!DNL Redis] TTL de cache (date d’expiration) avait une valeur incorrecte.
1. **MDVA-42046** : permet de résoudre le problème d’affectation d’une valeur incorrecte à un attribut de produit avec un champ de saisie de date lors de la mise à jour d’un produit.
1. **MDVA-42283** : correction d’un problème en raison duquel le format de date et d’heure dans la grille de commande d’administration pour les paramètres régionaux français n’était pas valide.
1. **MDVA-42969** : correction du problème en raison duquel la règle de produit associé ne fonctionne que lorsque le segment client est défini sur *Tous*.
1. **MDVA-43451** : corrige le problème en raison duquel l’erreur *Le magasin demandé est introuvable. Vérifiez le magasin et réessayez.* s’affiche lors de la configuration d’un catalogue partagé pour un site web spécifique.
1. **MDVA-43491** : correction d’un problème en raison duquel le libellé de l’image de base n’est pas mis à jour lors de l’importation de produits pour un site web multi-magasin.
1. **MDVA-43601** : correction du problème lié aux déclencheurs manquants après une réindexation complète.
1. **MDVA-43824** : permet de résoudre le problème d’affichage d’une erreur lors de l’annulation d’une commande avec une remise.
1. **MDVA-43862** : corrige le problème en raison duquel le client ne peut pas mettre à jour les articles du panier en raison d’une erreur GraphQL *mutation UpdateCartItems*.
1. **MDVA-43935** : correction du problème en raison duquel le produit de montée en gamme est affiché deux fois.
1. **MDVA-44188** : correction du problème en raison duquel les e-mails émis par le système avec des `.-` dans les adresses ne sont pas envoyés.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
