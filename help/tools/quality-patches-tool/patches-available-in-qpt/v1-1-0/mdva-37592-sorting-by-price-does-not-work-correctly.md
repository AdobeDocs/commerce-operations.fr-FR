---
title: 'MDVA-37592 : Le tri par prix ne fonctionne pas pour les produits dont le prix est égal à zéro'
description: Le correctif Adobe Commerce MDVA-37592 résout le problème où le tri par prix ne fonctionne pas correctement pour les produits dont le prix zéro est affecté à un catalogue partagé. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 est installé. L’ID du correctif est MDVA-37592. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
exl-id: 4d4a158c-2020-42a4-9b8b-14c9b48b4107
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%
---
# MDVA-37592 : Le tri par prix ne fonctionne pas pour les produits dont le prix est égal à zéro

Le correctif Adobe Commerce MDVA-37592 résout le problème où le tri par prix ne fonctionne pas correctement pour les produits dont le prix zéro est affecté à un catalogue partagé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.0 est installé. L’ID du correctif est MDVA-37592. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur notre architecture cloud 2.4.0-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (tous les types de déploiement) 2.3.6-2.4.2-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le tri par prix ne fonctionne pas correctement pour les produits dont le prix zéro est affecté à un catalogue partagé.

<u>Conditions préalables</u> :

B2B est installé.

<u>Procédure à suivre </u> :

1. Activez le catalogue partagé.
1. Créez quatre produits aux prix suivants et affectez-les à une catégorie : 50 $, 60 $, 70 $ et 80 $.
1. Créez un catalogue partagé avec les produits ci-dessus.
1. Définissez le prix personnalisé sur zéro pour le produit au prix de 70 $.
1. Créez maintenant un utilisateur d&#39;entreprise et affectez-le au catalogue partagé qui vient d&#39;être créé.
1. Connectez-vous à l’aide du compte d’entreprise et accédez à la catégorie à laquelle les produits sont affectés.
1. Essayez de trier par prix.

<u>Résultats attendus</u> :

Le produit au prix zéro est trié correctement.

<u>Résultats réels</u> :

Le produit au prix zéro n&#39;est PAS trié correctement. Au lieu de cela, il est trié selon le prix d’origine.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
