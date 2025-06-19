---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.40
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.40.
feature: Tools and External Services
role: Admin, Developer
exl-id: fd0caa46-834a-4553-bb59-e4c968c59c15
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.40

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.40.

QPT v1.1.40 comprend les correctifs suivants :

1. **ACSD-54680** : corrige le problème en raison duquel il n’est pas possible de traiter un devis B2B envoyé pour un produit avec plusieurs sources affectées.
1. **ACSD-54040** : corrige le problème en raison duquel le champ *[!UICONTROL Created]* est vide dans les détails d’ordre lorsque les modules B2B sont activés.
1. **ACSD-54319** : corrige le problème en raison duquel le prix du produit affiche zéro dans le rapport de *[!UICONTROL Product in Cart]*.
1. **ACSD-53378** : améliore le temps de chargement des pages de passage en caisse pour les clients qui disposent de carnets d’adresses volumineux.
1. **ACSD-52657** : corrige le problème où le mini-art n&#39;est pas mis à jour sur le magasin secondaire, qui utilise un sous-domaine.
1. **ACSD-53414** : corrige le problème en raison duquel un utilisateur administrateur restreint peut voir les pages CMS en dehors de sa portée d’autorisations.
1. **ACSD-54472** : corrige le problème en raison duquel les clients d’une société refusée peuvent toujours s’authentifier et les clients d’une société bloquée et refusée peuvent toujours passer des commandes. Le correctif ajoute une validation supplémentaire pour les points d’entrée GraphQL.
1. **ACSD-52801** : ajoute l’option permettant d’effectuer une correspondance partielle lors de la recherche de produits dans GraphQL.
1. **ACSD-55004** : corrige le problème en raison duquel le programme de validation se bloque lors du chargement d’un fichier d’importation dont la taille est supérieure à la valeur configurée dans `php.ini`.
1. **ACSD-54989** : corrige le problème en raison duquel un administrateur d’entreprise ne peut pas passer de commande lorsque *[!UICONTROL Enable Purchase Orders]* est défini sur *[!UICONTROL Yes]* et *[!UICONTROL Purchase Order]* sur *[!UICONTROL No]*.
1. **ACSD-54007** : corrige l’erreur *« Clé de tableau non définie »_scope »* lors de l’importation de données client.
1. **ACSD-55031** : corrige l’erreur *Le type « mixte » ne peut pas être considéré comme une valeur nulle* lors de la compilation.
1. **ACSD-54961** : corrige le problème en raison duquel un utilisateur administrateur restreint ne peut pas mettre à jour en masse le statut *Révision du produit*.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
