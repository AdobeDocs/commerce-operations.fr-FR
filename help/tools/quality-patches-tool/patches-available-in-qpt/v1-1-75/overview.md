---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.75
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.75.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: cb39f5a778ee8af49823f45704d0bb68a13fbf08
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.75

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.75.

QPT v1.1.75 comprend les correctifs suivants :
1. **ACSD-68289** : correction d’un problème en raison duquel la recherche en texte intégral renvoie désormais les produits correspondants si la condition de correspondance minimale est remplie collectivement pour tous les champs pouvant faire l’objet d’une recherche, plutôt que d’exiger que la condition soit remplie par un seul champ.
1. **ACSD-68359** : corrige un problème en raison duquel la sélection d’un magasin lors du passage en caisse à l’aide de **[!UICONTROL Pick in Store]** n’échoue plus en raison de longues URL lorsque de nombreux produits se trouvent dans le panier. Auparavant, cela déclenchait une erreur 414 due à des URL trop longues générées lors d’une vente de magasin.
1. **ACSD-68451** : corrige un problème lié à plusieurs sites web en raison duquel l’administrateur d’une société se connecte à un site web, crée une société non liée sur un autre site web, mais est lié par erreur à cette société non liée.
1. **ACSD-68490** : corrige le problème en raison duquel le bouton **[!UICONTROL Add New Attribute]** est visible pour un utilisateur administrateur restreint lors de la création d’un produit configurable.
1. **ACSD-68517** : corrige une erreur de nouvel envoi de formulaire sur les pages Catalogue et Recherche catalogue.
1. **ACSD-68573** : correction d’un problème en raison duquel les autorisations de catégorie n’étaient pas correctement appliquées aux éléments de la liste de souhaits du client. Après la correction, les éléments de liste de souhaits sont correctement affichés et paginés sur le web et dans GraphQL.
1. **ACSD-68615** : corrige le problème en raison duquel l’interface de ligne de commande de compensation de réservation de stock affichait une exception si la combinaison traitée avait un ID de commande manquant.
1. **ACSD-68793** : correction d’un problème en raison duquel des produits valides étaient incorrectement rejetés lors de leur affectation à un catalogue partagé.
1. **ACSD-68925** : correction d’un problème en raison duquel les réponses aux requêtes GraphQL étaient désormais alignées sur les spécifications GraphQL via HTTP. Un code de réponse 4XX est renvoyé lorsque la requête ne peut pas être analysée, n’est pas autorisée ou rencontre un problème général si la requête est analysée.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
