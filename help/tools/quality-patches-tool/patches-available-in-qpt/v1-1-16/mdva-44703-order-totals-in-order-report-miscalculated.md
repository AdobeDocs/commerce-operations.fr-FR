---
title: 'MDVA-44703 : les totaux des commandes dans l''état Commandes sont mal calculés'
description: Le correctif MDVA-44703 corrige le problème en raison duquel les totaux des commandes dans le rapport Commandes sont mal calculés pour l’utilisateur administrateur restreint. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 est installé. L’ID du correctif est MDVA-44703. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.
feature: Orders
role: Admin
exl-id: bdd38ba6-f282-4026-8f65-b76543859123
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%
---
# MDVA-44703 : les totaux des commandes dans l&#39;état Commandes sont mal calculés

Le correctif MDVA-44703 corrige le problème en raison duquel les totaux des commandes dans le rapport Commandes sont mal calculés pour l’utilisateur administrateur restreint. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.16 est installé. L’ID du correctif est MDVA-44703. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les totaux des commandes du rapport Commandes sont incorrects pour l’utilisateur administrateur restreint.

<u>Procédure à suivre </u> :

1. Créez un site web supplémentaire avec deux magasins.
1. Créez un utilisateur administrateur restreint ayant accès au nouveau site web uniquement.
1. Connectez-vous en tant qu’utilisateur administrateur restreint.
1. Créez deux commandes avec des totaux différents, une pour chaque nouveau magasin.
1. Créez des factures pour les commandes.
1. Accédez à **Rapports** > **Ventes** et ouvrez **rapport Commandes**.
1. Actualiser les statistiques.
1. Voir le rapport pour chaque magasin.

<u>Résultats attendus</u> :

Les totaux des ventes correspondent au montant de la commande de chaque magasin.

<u>Résultats réels</u> :

Le total des ventes agrégées pour l’ensemble du site web s’affiche pour chaque magasin.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
