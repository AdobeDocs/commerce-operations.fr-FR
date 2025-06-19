---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.51
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.51.
feature: Tools and External Services
role: Admin, Developer
exl-id: 277b6301-944b-4913-84a3-bbcca2c92ce1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.51

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.51.

QPT v1.1.51 comprend les correctifs suivants :

1. **ACSD-59786** : corrige le problème en raison duquel GraphQL renvoie une erreur de serveur interne lors de la tentative d’obtention d’un ID de devis pour un devis expiré.
1. **ACSD-60234** : permet de résoudre le problème d’affichage d’un montant incorrect sur les [!DNL PayPal] lors de l’application de la remise via le mode de paiement.
1. **ACSD-59967** : corrige le problème en raison duquel une erreur JavaScript empêche le [!DNL Google Maps] d’effectuer correctement le rendu.
1. **ACSD-60326** : permet de résoudre le problème d’erreur dans la requête GraphQL relative au statut du retour des clients.
1. **ACSD-60538** : correction d’un problème en raison duquel, si un produit est désactivé dans *[!UICONTROL All Store Views]* et activé uniquement dans des portées d’affichage de magasin spécifiques, les attributs de produit ne s’affichent pas correctement dans la réponse GraphQL, ce qui entraîne un affichage incorrect du produit.
1. **ACSD-60631** : correction du problème en raison duquel GraphQL renvoie une erreur lorsqu’un même produit simple est affecté à plusieurs produits configurables.
1. **ACSD-60632** : permet de résoudre le problème d’enregistrement d’une nouvelle adresse chaque fois qu’une commande est envoyée, que la commande ait été créée avec succès ou non.
1. **ACSD-60816** : corrige le problème en raison duquel les scripts [!DNL New Relic Browser Monitoring] injectés par l’agent APM ne sont pas conformes à la CSP (Content Security Policy, politique de sécurité du contenu), empêchant leur exécution.
1. **ACSD-61195** : corrige le problème en raison duquel aucun article de panier n’est renvoyé sur la dernière page pour la requête de GraphQL de panier.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
