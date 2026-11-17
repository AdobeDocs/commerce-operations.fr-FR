---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.85'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.85.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 59431a80af552bd266da55fb49e489453cc64e71
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
