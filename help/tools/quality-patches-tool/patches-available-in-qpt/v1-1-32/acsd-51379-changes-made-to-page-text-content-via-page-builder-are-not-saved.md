---
title: 'ACSD-51379 : les modifications apportées au contenu texte de la page via  [!DNL Page Builder]  ne sont pas enregistrées'
description: Appliquez le correctif ACSD-51379 pour résoudre le problème d’Adobe Commerce en raison duquel les modifications apportées au contenu texte d’une page via  [!DNL Page Builder]  ne sont pas enregistrées.
feature: Page Builder, Page Content
role: Admin
exl-id: 03fc2865-04b6-4330-b80c-8d694baa8c88
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51379 : les modifications apportées au contenu textuel de la page via [!DNL Page Builder] ne sont pas enregistrées

Le correctif ACSD-51379 corrige le problème où les modifications apportées au contenu textuel d’une page via [!DNL Page Builder] ne sont pas enregistrées. Ce correctif est disponible lorsque la version 1.1.32 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51379. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les modifications apportées au contenu texte d’une page via [!DNL Page Builder] ne sont pas enregistrées.

<u>Procédure à suivre </u> :

1. Connectez-vous à Admin.
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. Créez une page de test avec une ligne et un élément de texte sur l’onglet **[!UICONTROL Content]** .
1. Enregistrez la page et revenez à l’onglet **[!UICONTROL Content]** .
1. Modifiez le texte en le sélectionnant et en le modifiant.

   **Remarque :** le problème n’est reproductible que si le texte est sélectionné et modifié sans activer l’éditeur.

1. Cliquez sur le bouton **[!UICONTROL Save and Close]** sur la page de test.
1. Ouvrez à nouveau la page de test et vérifiez l’onglet **[!UICONTROL Content]** .

<u>Résultats attendus</u> :

Le nouveau texte est enregistré avec succès pour les éléments de texte d’origine et dupliqués.

<u>Résultats réels</u> :

L’élément text est dupliqué avec succès, mais le nouveau texte n’est pas enregistré.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
