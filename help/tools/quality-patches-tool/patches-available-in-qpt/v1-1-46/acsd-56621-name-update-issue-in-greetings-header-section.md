---
title: 'ACSD-56621 : les noms mis à jour ne s’affichent pas dans l’en-tête des salutations pour l’utilisateur administrateur de la société'
description: Appliquez le correctif ACSD-56621 pour résoudre le problème d’Adobe Commerce en raison duquel le prénom et le nom mis à jour de l’utilisateur administrateur de la société ne sont pas reflétés dans la section d’en-tête des salutations.
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 739c1c8c-e079-4ad7-be97-7c60b0347e12
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: 4560f5f5-d00c-5b5d-b61b-369d85ef7a26
    internal-label: User Account
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%
---
# ACSD-56621 : les noms mis à jour ne s’affichent pas dans l’en-tête des salutations pour l’utilisateur administrateur de la société

Le correctif ACSD-56621 corrige le problème en raison duquel le prénom et le nom mis à jour de l’utilisateur administrateur de la société ne sont pas reflétés dans la section d’en-tête des salutations. Ce correctif est disponible lorsque la version 1.1.46 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-56621. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
