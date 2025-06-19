---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.56
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.56.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6433df73-b6df-4c88-93a4-12ac1e5080ea
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.56

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.56.

QPT v1.1.56 comprend les correctifs suivants :

1. **ACSD-63244** : corrige les problèmes où une erreur JavaScript empêche le rendu correct du [!DNL Google Maps] et où il y a beaucoup de *Uncaught TypeError : this._each n&#39;est pas une fonction* erreurs dans la console du panneau [!UICONTROL Admin].
1. **ACSD-63242** : corrige le problème de lenteur des importations lors de l’ajout de produits de catalogue comportant plus de 10 000 entrées.
1. **ACSD-63062** : corrige le problème en raison duquel des calculs de remise de panier incorrects se produisent lorsque plusieurs règles qui se chevauchent sont appliquées.
1. **ACSD-62979** : corrige le problème en raison duquel l’utilisation d’un [!UICONTROL Store ID] incorrect dans l’en-tête de GraphQL provoque une erreur de mémoire fatale.
1. **ACSD-62971** : corrige le problème en raison duquel l’importation d’origines de stock avec des valeurs non numériques dans la colonne *[!UICONTROL Quantity]* entraîne la définition de la *quantité* sur *0*.
1. **ACSD-62872** : corrige le problème lié à la validation d’attributs uniques où les mises à jour de planning sont validées de manière incorrecte.
1. **ACSD-62755** : corrige le problème où [!DNL TinyMCE] 7 exige que la taille et la police de caractères soient spécifiquement ajoutées dans les paramètres d’initialisation de l’éditeur.
1. **ACSD-62670** : corrige le problème en raison duquel l’exportation du rapport [!UICONTROL Products Ordered] au format CSV et XML renvoie une erreur.
1. **ACSD-62577** : corrige le problème de performances lentes des requêtes de recherche storefront en optimisant les index de requête et de table.
1. **ACSD-62475** : corrige le problème de fusion incorrecte des produits [!UICONTROL Gift Card] dans le panier.
1. **ACSD-62428** : correction du problème en raison duquel `is_out_of_stock` est défini sur une valeur incorrecte dans l’index de recherche catalogue lorsque la [!DNL SKU] n’est pas définie en tant qu’attribut consultable.
1. **ACSD-62355** : améliore le temps de chargement de la page d’édition du produit configurable lorsque le produit configurable est basé sur de nombreux attributs avec de nombreuses valeurs.
1. **ACSD-61805** : corrige le problème de rupture de stock des produits sur le storefront après la mise à jour du statut de la commande en attente via [!DNL REST API].
1. **ACSD-60811** : corrige le problème en raison duquel la mise à jour du statut de la commande avec une valeur ou un commentaire personnalisé n’est possible que si le statut actuel est *[!UICONTROL Processing]* ou *[!UICONTROL Fraud]*.
1. **ACSD-62952** : corrige le problème d’affichage inexact de la date de [!UICONTROL Gift Registry] sur le storefront.
1. **ACSD-55339** : corrige le problème où un produit [!DNL SKU] commençant par *0* (zéro) supprime le *0*, empêchant la mise à jour du devis.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
