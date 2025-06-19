---
title: 'ACSD-56621 : les noms mis à jour ne s’affichent pas dans l’en-tête des salutations pour l’utilisateur administrateur de la société'
description: Appliquez le correctif ACSD-56621 pour résoudre le problème d’Adobe Commerce en raison duquel le prénom et le nom mis à jour de l’utilisateur administrateur de la société ne sont pas reflétés dans la section d’en-tête des salutations.
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 739c1c8c-e079-4ad7-be97-7c60b0347e12
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-56621 : les noms mis à jour ne s’affichent pas dans l’en-tête des salutations pour l’utilisateur administrateur de la société

Le correctif ACSD-56621 corrige le problème en raison duquel le prénom et le nom mis à jour de l’utilisateur administrateur de la société ne sont pas reflétés dans la section d’en-tête des salutations. Ce correctif est disponible lorsque la version 1.1.46 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-56621. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les noms mis à jour ne s’affichent pas dans l’en-tête des salutations pour les utilisateurs administrateurs de la société.

<u>Procédure à suivre </u> :

1. Accédez au panneau **[!UICONTROL Admin]** .
1. Accédez à **[!UICONTROL Stores]** et sélectionnez **[!UICONTROL Configuration]**.
1. Dans la section **[!UICONTROL General]** , sélectionnez **[!UICONTROL B2B]** pour activer les fonctionnalités de la société B2B.
1. Accédez au **[!UICONTROL Storefront]** et enregistrez une nouvelle entreprise.
1. Connectez-vous en tant qu’utilisateur administrateur d’entreprise.
1. Accédez à **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** et modifiez les champs Prénom et Nom selon vos besoins.

<u>Résultats attendus</u> :

Le prénom et le nom de l’utilisateur dans la section d’en-tête des salutations sont modifiés immédiatement.

<u>Résultats réels</u> :

Le prénom et le nom de l’utilisateur ne sont modifiés que lorsque l’utilisateur se déconnecte et se reconnecte.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
