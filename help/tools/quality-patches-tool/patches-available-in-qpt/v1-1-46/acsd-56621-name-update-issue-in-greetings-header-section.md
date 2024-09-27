---
title: "ACSD-56621 : noms mis à jour non affichés dans l’en-tête Salutations pour l’utilisateur administrateur de la société"
description: Appliquez le correctif ACSD-56621 pour résoudre le problème Adobe Commerce en raison duquel le prénom et le nom mis à jour de l’utilisateur administrateur de la société ne sont pas reflétés dans la section d’en-tête des salutations.
feature: Companies, B2B, User Account
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-56621 : noms mis à jour non affichés dans l’en-tête Salutations pour l’utilisateur administrateur de la société

Le correctif ACSD-56621 corrige le problème en raison duquel le prénom et le nom mis à jour de l’utilisateur administrateur de la société ne sont pas reflétés dans la section d’en-tête des salutations. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.46 est installé. L’ID de correctif est ACSD-56621. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les noms mis à jour ne s’affichent pas dans l’en-tête Salutations pour les utilisateurs administrateurs de l’entreprise.

<u>Étapes à reproduire</u> :

1. Accédez au panneau **[!UICONTROL Admin]**.
1. Accédez à **[!UICONTROL Stores]** et sélectionnez **[!UICONTROL Configuration]**.
1. Dans la section **[!UICONTROL General]** , sélectionnez **[!UICONTROL B2B]** pour activer la fonctionnalité d’entreprise B2B.
1. Accédez à **[!UICONTROL Storefront]** et enregistrez une nouvelle société.
1. Connectez-vous en tant qu’utilisateur administrateur de l’entreprise.
1. Accédez à **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** et modifiez les champs de prénom et de nom selon les besoins.

<u>Résultats attendus</u> :

Le prénom et le nom de l’utilisateur dans la section d’en-tête des salutations sont modifiés immédiatement.

<u>Résultats réels</u> :

Le prénom et le nom de l’utilisateur ne sont modifiés que lorsqu’il se déconnecte et se reconnecte.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
