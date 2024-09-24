---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.39'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.39.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.39

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.39.

QPT v1.1.39 comprend les correctifs suivants :

1. **ACSD-53704** : corrige le problème en raison duquel l’historique d’équilibrage des points de récompense est mal calculé après l’expiration des points de récompense.
1. **ACSD-53583** : améliore les performances de réindexation partielle pour les indexeurs *Produits de catégorie* et *Catégories de produits*.
1. **ACSD-54026** : corrige un message d’erreur incorrect pour une requête GraphQL `updateCompanyRole` pour un utilisateur non autorisé.
1. **ACSD-54106** : corrige le problème de tri des produits de catégorie par nom pour les caractères accentués turcs.
1. **ACSD-52219** : correction d’un problème en raison duquel les filtres enregistrés des grilles d’administration ne fonctionnaient pas comme prévu lors du basculement fréquent entre les vues de signets.
1. **ACSD-54342** : corrige un message d’erreur incorrect *Erreur dans la structure de données : les valeurs sont mélangées* lors de l’importation d’un fichier CSV sans données valides.
1. **ACSD-54660** : ajout d’un nouvel attribut d’entrée *sort* pour trier les commandes client dans GraphQL par `sort_field` et `sort_direction`.
1. **ACSD-54776** : résolution du problème en raison duquel les valeurs de champ de produit non cochées *[!UICONTROL Use Default Value]* et non par défaut ne sont pas enregistrées pour la deuxième vue de site Web, de magasin et de magasin.
1. **ACSD-53998** : corrige le problème en raison duquel un **[!UICONTROL Dynamic Block]** basé sur un **[!UICONTROL Customer Segment]** ne fonctionnait pas correctement après déconnexion d’un compte client.
1. **ACSD-53204** : correctifs *Le produit ne peut pas être enregistré.* lors de demandes simultanées d’ajout d’images à la galerie de produits à l’aide du point de terminaison `rest/V1/products/<sku>/media`.
1. **ACSD-47657** : ajout d’un mécanisme de mise en cache pour les informations d’identification AWS. Un fournisseur d’informations d’identification utilise désormais le cache du Magento pour mettre en cache les informations d’identification extraites d’AWS pour la configuration EC2.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
