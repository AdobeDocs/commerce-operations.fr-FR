---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.53'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.53.
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e7c8d45-dc0c-4182-8cd0-727b28294d58
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
source-wordcount: '243'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.53

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.53.

QPT v1.1.53 comprend les correctifs suivants :

1. **ACSD-48318** : corrige le problème en raison duquel l’imbrication de l’émulation de l’environnement n’est pas autorisée. Désormais, l’émulation commence pendant l’appel `send()` une fois qu’elle s’arrête pendant l’appel `getInfoBlockHtml()`.
1. **ACSD-59930** : améliore les performances des flux *[!UICONTROL Create]*, *[!UICONTROL Save]* et *[!UICONTROL Delete]* de l&#39;entreprise.
1. **ACSD-60584** : corrige le problème en raison duquel un jeton d’accès créé pour l’utilisateur sur un site web est autorisé à accéder aux informations du client ou à les modifier sur d’autres sites web.
1. **ACSD-60804** : corrige le problème en raison duquel la modification d’un client lié à une entreprise supprimée provoquait l’erreur *Appel à une fonction membre `getSuperUserId()` sur null*.
1. **ACSD-61133** : correction du problème en raison duquel le cron `sales_clean_quotes` supprime les devis des commandes fournisseur non approuvées.
1. **ACSD-61528** : corrige le problème en raison duquel la récupération de rôles du [!UICONTROL Admin] à l’aide de GraphQL ne renvoie aucun résultat.
1. **ACSD-61553** : corrige le problème en raison duquel les remises *[!UICONTROL Cart Price Rule]* sont incorrectement calculées lorsque plusieurs remises avec des priorités et des *[!UICONTROL Maximum Qty Discount is Applied To]* différentes sont appliquées au produit.
1. **ACSD-61667** : améliore la performance des stocks pour la création d&#39;expédition dans le cas de nombreuses sources avec *ramassage en magasin*.
1. **ACSD-61969** : corrige le problème en raison duquel l’utilisateur ou l’utilisatrice doit saisir un code de coupon sensible à la casse qui correspond exactement au code de coupon configuré.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
