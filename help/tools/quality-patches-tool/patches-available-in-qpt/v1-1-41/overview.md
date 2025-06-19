---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.41
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.41.
feature: Tools and External Services
role: Admin, Developer
exl-id: 10e1f4f9-8c6b-45b2-b6ed-0758c8019c8c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.41

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.41.

QPT v1.1.41 comprend les correctifs suivants :

1. **ACSD-54376** : corrige le problème qui se produit dans le panier lorsqu’un produit est supprimé du catalogue partagé après avoir été ajouté au panier.
1. **ACSD-53722** : corrige le problème en raison duquel le prix des options de produit groupées passe à 0 $ lorsque les mises à jour planifiées pour différentes portées deviennent actives.
1. **ACSD-53643** : corrige le problème en raison duquel le total de la commande est incorrect lors de la passation d’une commande fournisseur avec des produits désactivés ou en rupture de stock. Elle est corrigée en masquant le bouton *[!UICONTROL Place Order]* pour ces commandes fournisseur.
1. **ACSD-54067** : correction d’un problème en raison duquel une vidéo de produit n’est pas lue sur un appareil mobile.
1. **ACSD-55414** : améliore les performances lorsque MariaDB tente de convertir la valeur entity_id EAV de string en entier.
1. **ACSD-51819** : correction du problème en raison duquel plusieurs commandes peuvent être passées avec le même ID de devis.
1. **ACSD-53118** : corrige le problème d’application du *[!UICONTROL Cart Price Rule]* à l’aide d’un code de coupon lorsque le produit a un attribut vide.
1. **ACSD-54324** : corrige le problème en raison duquel la requête GraphQL requisition_lists ne prend pas en compte les paramètres de pagination et renvoie tous les résultats.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
