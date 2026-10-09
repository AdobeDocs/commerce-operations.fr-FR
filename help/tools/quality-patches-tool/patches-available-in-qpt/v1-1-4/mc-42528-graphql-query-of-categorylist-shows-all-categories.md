---
title: 'MC-42528 : la requête GraphQL de categoryList affiche toutes les catégories'
description: Le correctif MC-42528 résout le problème où la requête GraphQL de « categoryList » renvoie à la fois les catégories affectées et non affectées lorsque la catégorie de navigation d’une catégorie particulière est définie sur « Deny ». Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 est installé. L’ID du correctif est MC-42528. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
exl-id: 0611a7ff-9d55-4d95-9d4e-9ce1d9096bb6
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%
---
# MC-42528 : la requête GraphQL de categoryList affiche toutes les catégories

Le correctif MC-42528 résout le problème où la requête GraphQL de `categoryList` renvoie à la fois les catégories affectées et non affectées lorsque la catégorie de navigation d’une catégorie particulière est définie sur « Refuser ». Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.4 est installé. L’ID du correctif est MC-42528. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête GraphQL de `categoryList` renvoie les catégories affectées et non affectées.

<u>Procédure à suivre </u> :

1. Créez deux catégories, CAT1 et CAT2, et attribuez peu de produits à chaque catégorie.
1. Créez un catalogue partagé privé.
1. Créez un utilisateur société et affectez-le au catalogue partagé créé.
1. Attribuez CAT1 au catalogue personnalisé et définissez l’autorisation de catégorie sur « Autoriser » la catégorie de navigation pour le groupe de clients du catalogue privé.
1. Définissez l’autorisation de catégorie pour CAT2 sur « Refuser » la catégorie de navigation pour le groupe de clients ou clientes du catalogue privé.
1. Exécutez la requête `categoryList` ou `categories` GraphQL en tant qu’utilisateur de la société.

<u>Résultats attendus</u> :

Seul le CAT1 apparaît dans la réponse.

<u>Résultats réels</u> :

Toutes les catégories s’affichent dans la réponse, quelles que soient les autorisations de navigation de la catégorie.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
