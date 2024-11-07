---
title: 'Aperçu : [!DNL Quality Patches Tool] (QPT) v1.1.54'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.54.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 4f5ce23584cdb3bc52b8375717ba96c24364423c
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.54

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.54.

QPT v1.1.54 comprend les correctifs suivants :

1. **ACSD-60267** : résolution du problème en raison duquel la taxe sur les produits fixes (FPT) s’applique correctement lors de l’ajout de produits simples avec FPT directement dans le panier, mais échoue lors de la sélection de ces produits par le biais d’options de produits configurables.
1. **ACSD-61103** : résolution du problème en raison duquel le nombre d’échecs dans la table `customer_entity` n’est pas réinitialisé à zéro une fois qu’un client s’est connecté avec succès via des points de terminaison API.
1. **ACSD-61134** : résolution du problème de désélection automatique du mode de paiement [!DNL Braintree Vault] dans le workflow de passage en caisse lorsqu’un acheteur met à jour son adresse de facturation en désélectionnant la case à cocher *[!UICONTROL My billing and shipping address are the same]*.
1. **ACSD-61199** : résolution du problème en raison duquel l’onglet de hiérarchie de page CMS n’affiche pas une arborescence correcte lors de la modification d’une page CMS avec une hiérarchie existante.
1. **ACSD-61200** : correction d’un problème en raison duquel les calculs pour *[!UICONTROL Total Amount]* et *[!UICONTROL Total Amount Actual]* dans les ventes manquaient les *[!UICONTROL Discount Tax Compensation Amount]* et *[!UICONTROL Shipping Discount Tax Compensation Amount]*, ce qui provoquait des incohérences dans les données des commandes client.
1. **ACSD-61522** : résolution du problème où il est possible de saisir des adresses électroniques dans les champs *[!UICONTROL First Name]* et *[!UICONTROL Last Name]* du client invité et d’envoyer des emails de confirmation de commande non valides.
1. **ACSD-61756** : améliore les performances des filtres `AdvancedSalesRule`.
1. **ACSD-61799** : corrige le problème en raison duquel la remise totale est incorrectement calculée lorsque plusieurs règles de panier avec remises fixes sont appliquées au guillemet.
1. **ACSD-61845** : corrige l’erreur qui se produit lorsqu’une requête est envoyée avec uniquement l’en-tête *text/html* accept.
1. **ACSD-62056** : résolution du problème d’échec du téléchargement d’images pour un produit configurable si MSI est installé.
1. **ACSD-62485** : résolution du problème de l’arrêt du fonctionnement du consommateur `async.operations.all` lors de la création d’une entreprise.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
