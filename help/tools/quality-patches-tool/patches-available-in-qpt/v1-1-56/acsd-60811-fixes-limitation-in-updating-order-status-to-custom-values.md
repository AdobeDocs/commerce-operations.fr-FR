---
title: 'ACSD-60811 : corrige la limitation dans la mise à jour du statut de commande vers des valeurs personnalisées'
description: Appliquez le correctif ACSD-60811 pour résoudre le problème d’Adobe Commerce où la mise à jour du statut de la commande avec une valeur ou un commentaire personnalisé n’est possible que si le statut actuel est « traitement » ou « fraude ».
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 6d5391b3-7014-4d0a-b4ab-799f0733bbca
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '394'
ht-degree: 0%
---
# ACSD-60811 : corrige la limitation dans la mise à jour du statut de commande vers des valeurs personnalisées

Le correctif ACSD-60811 corrige le problème en raison duquel la mise à jour du statut de la commande avec une valeur ou un commentaire personnalisé n’est possible que si le statut actuel est « [!UICONTROL Processing] » ou « [!UICONTROL Suspected Fraud] ». Ce correctif est disponible lorsque la version 1.1.56 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-60811. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7. 2.4.7-p1, 2.4.7-p2, 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour du statut de la commande avec une valeur ou un commentaire personnalisé n’est possible que si le statut actuel est *traitement* ou *fraude*. Le statut de la commande reste inchangé lorsqu’un nouveau statut est sélectionné et envoyé.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Order Status]** pour créer un statut de commande personnalisé dans le panneau d’administration.
1. Cliquez sur **[!UICONTROL Assign Status to State]** pour attribuer le statut personnalisé à l’état de commande.
1. Modifiez le statut de la commande à partir de la page vue de commande du panneau d’administration.

<u>Résultats attendus</u> :

L’utilisateur administrateur doit pouvoir modifier le statut de la commande en statut de commande personnalisé dans le panneau d’administration.

<u>Résultats réels</u> :

Le statut de la commande reste le même lorsqu’un nouveau statut de commande est sélectionné et envoyé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
