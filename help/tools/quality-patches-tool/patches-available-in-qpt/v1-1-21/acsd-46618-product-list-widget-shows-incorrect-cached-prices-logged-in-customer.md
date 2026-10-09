---
title: 'ACSD-46618 : le widget Liste de produits affiche des prix mis en cache incorrects pour le client connecté'
description: Appliquez un correctif pour résoudre le problème d’Adobe Commerce où le widget de liste de produits affiche des prix mis en cache incorrects pour un client connecté.
feature: Cache, Orders, Products
role: Admin
exl-id: fa350f84-2fe5-474b-b4fd-d6c1e8bb0f95
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%
---
# ACSD-46618 : le widget Liste de produits affiche des prix mis en cache incorrects pour un client connecté

Le correctif ACSD-46618 résout le problème où le widget de liste de produits affiche des prix mis en cache incorrects pour un client connecté. Ce correctif est disponible lorsque la version 1.1.21 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) est installée. L’ID du correctif est ACSD-46618. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le correctif ACSD-46618 résout le problème où le widget de liste de produits affiche des prix mis en cache incorrects pour un client connecté.

<u>Procédure à suivre </u> :

1. Dans Adobe Commerce Admin, sélectionnez **[!UICONTROL Stores]**, puis **[!UICONTROL Configuration]**, développez **[!UICONTROL Sales]** et sélectionnez **[!UICONTROL Tax]**. Mettez à jour les paramètres de taxe pour afficher les prix incluant et excluant les taxes.
1. Définissez **[!UICONTROL Enable Cross Border Trade]** = _Oui_.
1. Créez une règle fiscale qui s&#39;applique uniquement aux États-Unis.
1. Ajoutez un widget à la page d’accueil comprenant plusieurs produits.
1. Créez deux clients avec une adresse aux États-Unis et une adresse hors États-Unis.
1. Connectez-vous en utilisant le client américain depuis le storefront. Assurez-vous que la page est mise en cache.
1. Observez le prix affiché dans le widget de la page d’accueil.
1. Déconnectez-vous et connectez-vous à l’aide du client non américain.

<u>Résultats attendus</u> :

Le prix affiché dans le widget de la page d&#39;accueil correspond à l&#39;adresse du client.

<u>Résultats réels</u> :

Le widget de la page d’accueil affiche les prix en utilisant la taxe pour les clients non américains.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
