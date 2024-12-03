---
title: 'Présentation : [!DNL Quality Patches Tool]  (QPT) v1.1.53'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.53.
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e7c8d45-dc0c-4182-8cd0-727b28294d58
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.53

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.53.

QPT v1.1.53 comprend les correctifs suivants :

1. **ACSD-48318** : résolution du problème d’imbrication de l’émulation de l’environnement non autorisée. Désormais, l’émulation démarre pendant l’appel `send()` une fois que l’émulation s’arrête pendant l’appel `getInfoBlockHtml()`.
1. **ACSD-59930** : améliore les performances des flux *[!UICONTROL Create]*, *[!UICONTROL Save]* et *[!UICONTROL Delete]* de l’entreprise.
1. **ACSD-60584** : correction d’un problème en raison duquel un jeton d’accès créé pour l’utilisateur sur un site web était autorisé à accéder aux informations du client ou à les modifier sur d’autres sites web.
1. **ACSD-60804** : correction d’un problème en raison duquel la modification d’un client lié à une société supprimée provoquait l’erreur *Appeler à une fonction membre `getSuperUserId()` sur null*.
1. **ACSD-61133** : correction d’un problème en raison duquel le cron `sales_clean_quotes` supprimait les guillemets des commandes non approuvées.
1. **ACSD-61528** : résolution du problème en raison duquel la récupération des rôles de [!UICONTROL Admin] à l’aide de GraphQL ne renvoie aucun résultat.
1. **ACSD-61553** : correction d’un problème en raison duquel *[!UICONTROL Cart Price Rule]* remises sont incorrectement calculées lorsque plusieurs remises avec des priorités différentes et *[!UICONTROL Maximum Qty Discount is Applied To]* sont appliquées au produit.
1. **ACSD-61667** : améliore les performances d’inventaire pour la création d’expédition dans le cas de nombreuses sources avec *Récupération en magasin*.
1. **ACSD-61969** : résolution du problème en raison duquel l’utilisateur est tenu de saisir un code de bon sensible à la casse qui correspond exactement au code de bon configuré.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
