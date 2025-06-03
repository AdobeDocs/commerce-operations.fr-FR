---
title: 'ACP2E-3838: [!DNL Page Builder] Les erreurs CORS empêchent l’enregistrement des modifications dans le panneau d’administration en mode production'
description: Appliquez le correctif ACP2E-3838 pour résoudre le problème d’Adobe Commerce où les erreurs CORS [!DNL Page Builder] empêchent d’enregistrer les modifications dans le panneau d’administration en mode production.
feature: Page Builder, Page Content, Admin Workspace
role: Admin, Developer
source-git-commit: 1b9c721c8200f38b6ce5d1b4de87b1f10e07e8d2
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# ACP2E-3838 : [!DNL Page Builder] erreurs CORS empêchent l’enregistrement des modifications dans le panneau d’administration en mode production

Le correctif ACP2E-3838 corrige le problème où [!DNL Page Builder] erreurs CORS empêchent l’enregistrement des modifications dans le panneau d’administration en mode production. Ce correctif est disponible lorsque la version 1.1.64 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACP2E-3838. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!DNL Page Builder] erreurs CORS empêchent l’enregistrement des modifications dans le panneau d’administration en mode production.

<u>Procédure à suivre </u> :

1. Connectez-vous au panneau d’administration.
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Cliquez sur **[!UICONTROL Add New Page]** ou sélectionnez une page CMS existante et cliquez sur **[!UICONTROL Edit]**.
1. Cliquez sur **[!UICONTROL Edit with Page Builder]** pour ajouter un nouveau bloc de contenu ou modifier un bloc existant.
1. Apportez des modifications au contenu, par exemple en ajoutant du texte, des images ou d’autres éléments.
1. Cliquez sur le bouton **[!UICONTROL Save]** .

<u>Résultats attendus</u> :

Le contenu de la page doit être enregistré sans erreur.

<u>Résultats réels</u> :

1. L’enregistrement des modifications [!DNL Page Builder] échoue.
1. La console du navigateur consigne les erreurs CORS.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
