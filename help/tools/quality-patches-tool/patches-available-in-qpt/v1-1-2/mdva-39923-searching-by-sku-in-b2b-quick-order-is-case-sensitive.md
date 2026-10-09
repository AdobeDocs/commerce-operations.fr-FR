---
title: 'MDVA-39923 : la recherche par SKU dans la fonctionnalité de commande rapide B2B est sensible à la casse'
description: Le correctif MDVA-39923 corrige le problème où les clients obtiennent une erreur lorsqu’ils recherchent la fonctionnalité de commande rapide par SKU dans B2B avec un cas différent de celui avec lequel le nom est enregistré. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID du correctif est MDVA-39923. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: B2B, Catalog Management, Orders, Search
role: Admin
exl-id: 9bed5615-b398-42f5-8313-ae2acca59155
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%
---
# MDVA-39923 : la recherche par SKU dans la fonctionnalité de commande rapide B2B est sensible à la casse

Le correctif MDVA-39923 corrige le problème où les clients obtiennent une erreur lorsqu’ils recherchent la fonctionnalité de commande rapide par SKU dans B2B avec un cas différent de celui avec lequel le nom est enregistré. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID du correctif est MDVA-39923. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La recherche par SKU dans la fonctionnalité de commande rapide B2B est sensible à la casse et affiche une erreur lorsqu’une autre casse est utilisée que celle avec laquelle le SKU est enregistré.

<u>Conditions préalables</u> :

Les modules B2B sont installés.

<u>Procédure à suivre </u> :

1. Connectez-vous en tant qu’administrateur et accédez à **Magasins** > **Configuration** > **B2B**.
1. Activez **Catalogue partagé** et **Commande rapide**.
1. Créez un produit avec un SKU en majuscules, par exemple TEST20-1234.
1. Attribuez le produit créé au **catalogue partagé**.
1. Connectez-vous en tant que client et cliquez sur **Commande rapide**.
1. Saisissez le SKU en minuscules, par exemple test20-1234.

<u>Résultats attendus</u> :

Le produit doit être trouvé quel que soit le cas utilisé.

<u>Résultats réels</u> :

Le message d’erreur suivant est reçu : *1 produit(s) nécessite(nt) votre attention*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
