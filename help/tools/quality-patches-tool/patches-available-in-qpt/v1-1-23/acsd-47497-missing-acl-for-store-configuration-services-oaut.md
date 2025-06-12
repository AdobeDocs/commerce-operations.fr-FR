---
title: 'ACSD-47497 : ACL manquante pour le magasin / la configuration / les services [!UICONTROL OAuth]'
description: Appliquez le correctif ACSD-47497 pour résoudre le problème d’Adobe Commerce lorsque des autorisations sont définies pour un rôle particulier et que vous ne pouvez pas définir l’accès à la section de configuration.
feature: Configuration, Identity Management, Services
role: Admin
exl-id: 4dbbd7df-f34b-4db8-a207-3de40fb39c6f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-47497 : ACL manquante pour le magasin / la configuration / les services [!UICONTROL OAuth]

Le correctif ACSD-47497 résout le problème où l’onglet **[!UICONTROL Services]** n’est pas visible dans la section **[!UICONTROL Configuration]** de l’administration Adobe Commerce. Ce correctif est disponible lorsque la version 1.1.23 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47497. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque des autorisations sont définies pour un rôle particulier, vous ne pouvez pas définir l’accès au **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**.

<u>Procédure à suivre </u> :

1. Connectez-vous à l’administration Adobe Commerce. Accédez à **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**.
1. Sélectionnez **[!UICONTROL Role Resources]** dans le rôle Administrateurs et définissez **[!UICONTROL Resource Access]** sous **[!UICONTROL Roles Resources]** sur _Personnalisé_, puis cochez toutes les cases. Sélectionnez **[!UICONTROL Save Role]**.
1. Sélectionnez **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]**. La section Configuration **[!UICONTROL OAuth]** n’est pas disponible.

<u>Résultats attendus</u> :

Dans **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**, la section de configuration est visible.

<u>Résultats réels</u> :

Dans **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**, la section de configuration est manquante.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans notre documentation destinée aux développeurs et développeuses.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
