---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.35
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.35.
feature: Tools and External Services
role: Admin
exl-id: 5ffbade4-c95e-4b59-9262-1b141614c753
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.35

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.35.

QPT v1.1.35 comprend les correctifs suivants :

1. **ACSD-51899** : corrige le problème en raison duquel l’adresse d’expédition par défaut à l’étape de passage en caisse est automatiquement renseignée avec une adresse de retrait en magasin sélectionnée précédemment.
1. **ACSD-52041** : corrige le problème en raison duquel le message d’erreur : *[ERROR] [!DNL Page Builder] était rendu pendant 5 secondes sans libérer les verrous*. s’affiche dans [!DNL Chrome] navigateur lors de l’enregistrement de contenu modifié avec [!DNL Page Builder].
1. **ACSD-52095** : corrige le problème en raison duquel la valeur `manage_stock` était incorrectement définie sur 0 dans le fichier CSV après l’exportation du produit.
1. **ACSD-51358** : corrige le problème en raison duquel la suppression d’une mise à jour planifiée sans date de fin entraîne la suppression d’autres mises à jour planifiées pour la même entité.
1. **ACSD-48070** : corrige le problème en raison duquel la modification d’une mise à jour planifiée déclenche une exception.
1. **ACSD-51890** : corrige le problème en raison duquel il est possible de cliquer plusieurs fois sur le bouton [!UICONTROL Submit review] sans [!DNL Google] validation reCAPTCHA v3.
1. **ACSD-51984** : corrige le problème en raison duquel les options non cochées *Utiliser la valeur par défaut et les valeurs de champ de produit non par défaut* ne sont pas enregistrées pour la deuxième vue de site web, de magasin et de magasin.
1. **ACSD-52398** : corrige l’erreur *La quantité demandée n’est pas disponible* qui se produit lors de la tentative de mise à jour de la quantité d’un produit groupé dans le panier sur le storefront.
1. **ACSD-52786** : corrige le problème d’application d’un SKU de condition de règle de catalogue à tous les produits commençant par le SKU donné.
1. **ACSD-52921** : corrige le problème en raison duquel une erreur interne se produit lors de la demande des détails du panier à GraphQL lorsqu’un produit configurable en rupture de stock se trouve dans le panier.
1. **ACSD-51683** : corrige le problème en raison duquel une option personnalisable ne peut pas être ajoutée au panier à l’aide de GraphQL.
1. **ACSD-52133** : corrige le problème en raison duquel un compte client ne peut pas être enregistré après une mise à niveau.
1. **ACSD-52202** : correction du problème en raison duquel la quantité vendable du stock par défaut passe incorrectement à 0 lorsqu’un stock autre que le stock par défaut passe à 0 quantité lors de l’exécution de la commande.
1. **ACSD-51265** : corrige le problème lié aux performances de réindexation `catalog_product_price` lorsqu’il y a trop de produits groupés dans le système.
1. **ACSD-52831** : corrige le problème en raison duquel les clients ne peuvent pas passer d&#39;ordres de devis négociables lorsque le [!DNL Google reCAPTCHA v3 Invisible] est activé.
1. **ACSD-51845** : corrige le problème en raison duquel les produits suivants avec des prix de niveau et différents ensembles d’attributs ne peuvent pas être mis à jour via l’API REST en bloc asynchrone.
1. **ACSD-52815** : correction du problème en raison duquel l’entrée du champ de quantité d’une source non définie par défaut ne prend en charge que 6 chiffres au maximum, contrairement à 8 pour un stock défini par défaut.
1. **ACSD-51149** : corrige le problème où l’[!UICONTROL Scheduled ImportExport] avec le [!UICONTROL Catalog Permissions] activé invalide les indexeurs, puis les vidages du cache par cron.
1. **ACSD-50815** : corrige le problème en raison duquel la quantité décimale d’un produit simple ne peut pas être utilisée pour une nouvelle option de produit groupé.
1. **ACSD-52399** : corrige le problème en raison duquel l’option de produit configurable avec une Qté vendable de 0 affiche *En stock* sur la page du produit.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
