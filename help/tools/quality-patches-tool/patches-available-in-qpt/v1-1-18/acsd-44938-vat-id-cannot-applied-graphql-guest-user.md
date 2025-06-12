---
title: 'ACSD-44938 : VAT_ID ne peut pas être appliqué dans la demande pour  [!DNL GraphQL]  utilisateur invité'
description: Le correctif ACSD-44938 corrige le problème en raison duquel « VAT_ID » ne peut pas être appliqué dans une demande  [!DNL GraphQL] ’un utilisateur invité. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 est installé. L’ID du correctif est ACSD-44938. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.
feature: Admin Workspace, GraphQL
role: Admin
exl-id: 62d36c27-545a-4c32-be69-a92e4b3ca2ca
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-44938 : VAT_ID ne peut pas être appliqué à [!DNL GraphQL] demande pour un utilisateur invité

Le correctif ACSD-44938 corrige le problème en raison duquel le `VAT_ID` ne peut pas être appliqué dans une demande de [!DNL GraphQL] pour un utilisateur invité. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) version 1.1.18 est installé. L’ID du correctif est ACSD-44938. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`VAT_ID` ne peut pas être appliqué à une demande de [!DNL GraphQL] pour un utilisateur invité.

<u>Procédure à suivre </u> :

1. Suivez les étapes mentionnées dans le [[!DNL GraphQL] tutoriel](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) dans notre documentation destinée aux développeurs pour créer un panier d’invités.
1. Essayez d’appliquer des `VAT_ID` à l’utilisateur invité à l’aide de [!DNL GraphQL].

<u>Résultats attendus</u> :

`VAT_ID` peut être appliqué de la même manière que pour un client enregistré. Voir [`createCustomerAddress` article sur la mutation ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/create-address/) dans notre documentation destinée aux développeurs et développeuses.

<u>Résultats réels</u> :

`VAT_ID` ne peut pas être appliqué à un utilisateur invité utilisant [!DNL GraphQL].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur le [!DNL Quality Patches Tool], voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
