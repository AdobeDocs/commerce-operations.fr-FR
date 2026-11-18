---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.85'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.85.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
TQID: 'https://experienceleague.adobe.com/OmF7Ctss9khE5ONHNnfea0dTaN-1-wGTH-EN-gx5jvo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a094ba2e1af14f7139524bf5fa3ee55b169770d2
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.85

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.85.

QPT v1.1.85 comprend les correctifs suivants :

1. **ACP2E-4929** : correction d’un problème en raison duquel les libellés d’attribut de la page **[!UICONTROL Compare Products]** affichaient les traductions à partir d’une vue de magasin différente de la vue de magasin actuelle.
1. **ACP2E-5075** : correction d’un problème en raison duquel une règle de prix de panier à montant fixe avec une condition de catégorie appliquait incorrectement une remise à tous les enfants d’un produit groupé à prix dynamique lorsque la règle ne correspondait qu’au produit parent du lot.
1. **ACP2E-5077** : correction du problème en raison duquel des requêtes GraphQL `customerCart` ou des requêtes REST `POST /V1/carts/mine` simultanées créent des paniers actifs en double pour les clients qui n’en ont pas déjà un.
1. **ACP2E-5088** : correction d’un problème en raison duquel le panier persistant d’un client est effacé à l’expiration de sa session.
1. **ACP2E-3991** : correction d’un problème en raison duquel l’adresse IP du client n’est pas déterminée correctement.
1. **ACP2E-5092** : correction d’un problème en raison duquel la page **[!UICONTROL Company Profile]** et la page de modification du client administrateur affichaient une erreur lorsqu’une adresse d’entreprise enregistrée sans région ajoutait ultérieurement une région à son pays.
1. **ACP2E-5124** : correction du problème en raison duquel le bouton **[!UICONTROL Import]** reste disponible dans les résultats de validation après l’échec de la validation lorsque la valeur **[!UICONTROL Validation Strategy]** est définie sur **[!UICONTROL Stop on Error]**.
1. **AC-17456** : corrige le problème en raison duquel la modification de l’étendue **[!UICONTROL Global]** sur la page **[!UICONTROL Design Configuration]** dans le panneau d’administration renvoie une erreur *HTTP 500* sur PHP 8.4 et 8.5.
1. **ACP2E-5212** : correction d’un problème en raison duquel **[!UICONTROL Quick Order]** accepte des fichiers non CSV renommés avec une extension `.csv`.
1. **ACP2E-5300** : correction du problème en raison duquel les mots-clés recherchent plusieurs numéros de commande séparés par des espaces ou des virgules dans la grille du panneau d’administration **[!UICONTROL Orders]** et ne renvoient aucune commande correspondante.
1. **ACP2E-5354** : correction d’un problème en raison duquel la mise à jour d’un client par le biais de l’API REST entraîne l’affichage multiple d’un client associé à un compte d’entreprise dans la grille **[!UICONTROL Customers]** de l’administrateur.
1. **ACP2E-5208** : correction du problème en raison duquel la section **[!UICONTROL Requisition List]** se recharge sur chaque navigation de page Storefront, même si aucune modification n’a été apportée.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
