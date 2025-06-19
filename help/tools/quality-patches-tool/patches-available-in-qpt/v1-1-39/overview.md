---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.39
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.39.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6116f566-2ff8-4148-ab60-cec65f9b7a6f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.39

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.39.

QPT v1.1.39 comprend les correctifs suivants :

1. **ACSD-53704** : corrige le problème où l’historique d’équilibrage des points de récompense est mal calculé après l’expiration des points de récompense.
1. **ACSD-53583** : améliore les performances de réindexation partielle pour les indexeurs *Produits de catégorie* et *Catégories de produits*.
1. **ACSD-54026** : corrige un message d’erreur incorrect pour une requête `updateCompanyRole` GraphQL destinée à un utilisateur non autorisé.
1. **ACSD-54106** : corrige le problème en raison duquel le tri des produits de catégorie par nom pour les caractères accentués turcs est incorrect.
1. **ACSD-52219** : corrige le problème en raison duquel les filtres enregistrés des grilles d’administration ne fonctionnent pas comme prévu lors des changements fréquents d’affichage des signets.
1. **ACSD-54342** : corrige un message d’erreur incorrect *Erreur dans la structure des données : les valeurs sont mélangées* lors de l’importation d’un fichier CSV sans données valides.
1. **ACSD-54660** : ajout d’un nouvel attribut d’entrée *sort* pour trier les commandes client dans GraphQL par `sort_field` et `sort_direction`.
1. **ACSD-54776** : corrige le problème en raison duquel les valeurs de champ de produit *[!UICONTROL Use Default Value]* et non par défaut non cochées ne sont pas enregistrées pour la deuxième vue de site web, de magasin et de magasin.
1. **ACSD-53998** : correction d’un problème en raison duquel un **[!UICONTROL Dynamic Block]** basé sur un **[!UICONTROL Customer Segment]** ne fonctionne pas correctement après s’être déconnecté d’un compte client.
1. **ACSD-53204** : correctifs *Le produit ne peut pas être enregistré.* erreur lors de requêtes simultanées d’ajout d’images à la galerie de produits à l’aide du point d’entrée `rest/V1/products/<sku>/media`.
1. **ACSD-47657** : ajout d’un mécanisme de mise en cache pour les informations d’identification AWS. Un fournisseur d’informations d’identification utilise désormais le cache de Magento pour mettre en cache les informations d’identification récupérées d’AWS pour la configuration EC2.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
