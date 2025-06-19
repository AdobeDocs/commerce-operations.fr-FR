---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.37
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.37.
feature: Tools and External Services
role: Admin, Developer
exl-id: 92338019-d71c-4fe8-984f-879d551b418f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.37

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.37.

QPT v1.1.37 comprend les correctifs suivants :

1. **ACSD-52613** : corrige le problème d’actualisation des caches et des index même si aucune mise à jour n’est apportée aux éléments `Inventory_source` par l’API REST.
1. **ACSD-51884** : corrige le problème en raison duquel le chemin d’accès au cache de l’image du produit devient incorrect après l’exécution de la commande de redimensionnement.
1. **ACSD-53628** : correction du problème en raison duquel le rapport de commande client CSV affiche des caractères spéciaux incorrects.
1. **ACSD-49843** : corrige le problème en raison duquel le lien de téléchargement du produit n’est pas disponible après la facturation automatique de l’article commandé par le mode de paiement en ligne avec le paramètre *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* activé.
1. **ACSD-53148** : correction du problème en raison duquel deux requêtes parallèles dans GraphQL pour l’ajout d’un même produit configurable au panier entraînaient deux articles distincts dans le panier avec le même SKU de produit.
1. **ACSD-47054** : corrige le problème en raison duquel la réindexation de l’aperçu exécute la réindexation pour tous les magasins, ce qui entraîne de la lenteur.
1. **ACSD-52606** : corrige le problème en raison duquel le message d’erreur *Votre commande n’est pas prête pour l’enlèvement* s’affiche lorsque l’utilisateur clique sur **[!UICONTROL Notify Order is Ready for Pickup]**.
1. **ACSD-51574** : corrige le problème en raison duquel l’image n’est pas mise à jour sur le front-end après l’avoir remplacée par une autre image portant le même nom.
1. **ACSD-53728** : corrige le problème en raison duquel l’indexeur AEP du produit prend plus de temps à se terminer.
1. **ACSD-53979** : corrige le problème JS qui se produit sur la page d’accueil si le message de bienvenue contient une apostrophe.
1. **ACSD-52143** : corrige le problème de suppression des options personnalisées après l’importation du produit.
1. **ACSD-53750** : corrige l’erreur *Canal rompu ou connexion fermée* lors de la réindexation de `catalog_product_price` multithread.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
