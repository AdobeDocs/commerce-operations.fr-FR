---
title: "ACSD-44938 : L'ID de TVA ne peut pas être appliqué dans la  [!DNL GraphQL] demande d'utilisateur invité"
description: Le correctif ACSD-44938 corrige le problème en raison duquel le &grave;TVA_ID&grave; ne peut pas être appliqué dans une requête [!DNL GraphQL] pour un utilisateur invité. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 est installé. L’ID de correctif est ACSD-44938. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
feature: Admin Workspace, GraphQL
role: Admin
exl-id: 62d36c27-545a-4c32-be69-a92e4b3ca2ca
source-git-commit: 3fdefc6201714c441d63574d293863e83205894b
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-44938 : L&#39;ID de TVA ne peut pas être appliqué dans la requête [!DNL GraphQL] pour un utilisateur invité

Le correctif ACSD-44938 corrige le problème en raison duquel `VAT_ID` ne peut pas être appliqué dans une requête [!DNL GraphQL] pour un utilisateur invité. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.18 est installé. L’ID de correctif est ACSD-44938. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`VAT_ID` ne peut pas être appliqué dans une requête [!DNL GraphQL] pour un utilisateur invité.

<u>Étapes à reproduire</u> :

1. Suivez les étapes mentionnées dans le [[!DNL GraphQL] tutoriel](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) de notre documentation destinée aux développeurs pour créer un panier d’invité.
1. Essayez d&#39;appliquer `VAT_ID` à l&#39;utilisateur invité en utilisant [!DNL GraphQL].

<u>Résultats attendus</u> :

`VAT_ID` peut être appliqué de la même manière que pour un client enregistré. Consultez l’article [`createCustomerAddress` mutation](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/create-address/) dans notre documentation destinée aux développeurs.

<u>Résultats réels</u> :

`VAT_ID` ne peut pas être appliqué à un utilisateur invité utilisant [!DNL GraphQL].

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
