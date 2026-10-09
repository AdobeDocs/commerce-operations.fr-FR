---
title: 'MDVA-43167 : l’action de masse de la grille de commande de l’administrateur ne s’applique pas à plusieurs pages'
description: Le correctif MDVA-43167 corrige le problème en raison duquel l’action de masse de la grille de commandes de l’administrateur ne s’applique pas à plusieurs pages lorsque l’utilisateur administrateur sélectionne toutes les commandes. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 est installé. L’ID du correctif est MDVA-43167. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.
feature: Admin Workspace, Orders
role: Admin
exl-id: 992f8a90-300e-41aa-b03d-b8a647dddd51
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%
---
# MDVA-43167 : l’action de masse de la grille de commande de l’administrateur ne s’applique pas à plusieurs pages

Le correctif MDVA-43167 corrige le problème en raison duquel l’action de masse de la grille de commandes de l’administrateur ne s’applique pas à plusieurs pages lorsque l’utilisateur administrateur sélectionne toutes les commandes. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.16 est installé. L’ID du correctif est MDVA-43167. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L&#39;action en masse de la grille des commandes de l&#39;administrateur ne s&#39;applique pas à plusieurs pages lorsque l&#39;utilisateur administrateur sélectionne toutes les commandes.

<u>Procédure à suivre </u> :

1. Achetez n’importe quel produit trois fois pour créer trois commandes.
1. Accédez à **Grille des commandes client**.
1. Remplacez la pagination par une valeur personnalisée de 2.
1. Tout sélectionner.
1. Sélectionnez **Conserver l&#39;action en masse**.

<u>Résultats attendus</u> :

Les trois commandes sont mises en attente.

<u>Résultats réels</u> :

Seules les deux commandes visibles sont mises en attente.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
