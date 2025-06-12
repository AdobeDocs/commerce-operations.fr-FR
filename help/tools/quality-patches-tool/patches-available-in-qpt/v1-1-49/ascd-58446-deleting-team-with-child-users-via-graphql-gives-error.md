---
title: 'ACSD-58446 : la suppression d’une équipe avec des utilisateurs ou des équipes enfants via GraphQL génère un message d’erreur sans information'
description: Appliquez le correctif ACSD-58446 pour résoudre le problème d’Adobe Commerce où la suppression d’une équipe avec des utilisateurs ou des équipes enfants via GraphQL renvoie un message d’erreur informatif incompatible avec l’interface utilisateur.
feature: GraphQL
role: Admin, Developer
exl-id: 943ab281-cc41-4b96-8a7c-fff8c074267c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-58446 : la suppression d’une équipe avec des utilisateurs ou des équipes enfants via GraphQL génère un message d’erreur sans information

Le correctif ACSD-58446 corrige le problème d’Adobe Commerce en raison duquel la suppression d’une équipe avec des utilisateurs ou des équipes enfants via GraphQL renvoie un message d’erreur informatif incompatible avec l’interface utilisateur. Ce correctif est disponible lorsque la version 1.1.49 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-58446. Notez que le problème est planifié pour être corrigé dans Adobe Commerce B2B 1.5.1

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La suppression d’une équipe avec des utilisateurs ou des équipes enfants via GraphQL renvoie un message d’erreur informatif incompatible avec l’interface utilisateur.

## Conditions préalables requises :

Modules B2B Adobe Commerce installés.

<u>Procédure à suivre </u> :

1. Activez la fonctionnalité *[!UICONTROL Company]*.
1. Créez un compte d’entreprise.
1. Connectez-vous au **[!UICONTROL Admin]** et activez le compte d’entreprise.
1. Vérifiez l’e-mail et définissez un mot de passe pour le nouveau compte d’entreprise.
1. Créez une nouvelle équipe pour l’entreprise.
1. Connectez-vous en tant qu’utilisateur de l’entreprise sur Storefront et ajoutez un nouvel utilisateur pour l’équipe créée.
1. Connectez-vous au **[!UICONTROL Admin]**, désactivez l’utilisateur de l’entreprise et définissez *[!UICONTROL Customer Active]* = *Non*
1. Veillez à supprimer l’équipe créée via GraphQL.

   ```
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u>Résultats attendus</u> :

Un message d’erreur informatif cohérent avec l’interface utilisateur est renvoyé.

<u>Résultats réels</u> :

Un message d’erreur de serveur interne générique incompatible avec l’interface utilisateur est renvoyé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
