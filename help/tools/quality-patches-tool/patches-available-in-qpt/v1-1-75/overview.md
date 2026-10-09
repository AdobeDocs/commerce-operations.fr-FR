---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.75'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.75.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.75

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.75.

QPT v1.1.75 comprend les correctifs suivants :
1. **ACSD-68289** : correction d’un problème en raison duquel la recherche en texte intégral renvoie désormais les produits correspondants si la condition de correspondance minimale est remplie collectivement pour tous les champs pouvant faire l’objet d’une recherche, plutôt que d’exiger que la condition soit remplie par un seul champ.
1. **ACSD-68359** : corrige l’erreur *414* lors de la sélection de **[!UICONTROL Pick in Store]** avec des paniers volumineux.
1. **ACSD-68451** : corrige un problème lié à plusieurs sites web en raison duquel l’administrateur d’une société se connecte à un site web, crée une société non liée sur un autre site web, mais est lié par erreur à cette société non liée.
1. **ACSD-68517** : corrige une erreur de nouvel envoi de formulaire sur les pages **[!UICONTROL Catalog]** et **[!UICONTROL Catalog Search]**.
1. **ACSD-68490** : bouton **[!UICONTROL Add New Attribute]** visible par l’administrateur restreint lors de la création du produit configurable.
1. **ACSD-68573** : les autorisations de catégorie n’ont pas été appliquées aux éléments de la liste de souhaits du client, ce qui a entraîné un affichage et une pagination incorrects sur le storefront web et dans [!DNL GraphQL].
1. **ACSD-68615** : corrige le problème en raison duquel l’interface de ligne de commande de compensation de réservation de stock affichait une exception si la combinaison traitée avait un ID de commande manquant.
1. **ACSD-68793** : correction d’un problème en raison duquel des produits valides étaient incorrectement rejetés lors de leur affectation à un catalogue partagé.
1. **ACSD-68925** : correction d’un problème en raison duquel les réponses aux requêtes GraphQL étaient désormais alignées sur les spécifications GraphQL via HTTP. Un code de réponse 4XX est renvoyé lorsque la requête ne peut pas être analysée, n’est pas autorisée ou rencontre un problème général si la requête est analysée.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
