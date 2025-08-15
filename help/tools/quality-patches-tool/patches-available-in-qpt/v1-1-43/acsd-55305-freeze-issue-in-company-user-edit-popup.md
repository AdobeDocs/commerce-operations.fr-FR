---
title: 'ACSD-55305 : blocage des fenêtres contextuelles lors de la modification des utilisateurs de l’entreprise dans [!UICONTROL My Account]'
description: Appliquez le correctif ACSD-55305 pour résoudre le problème d’Adobe Commerce où [!UICONTROL Edit Company User] fenêtre contextuelle sur la page de [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] se fige avec un chargeur sur l’écran.
feature: Companies, B2B
role: Admin, Developer
exl-id: eeb2b136-022f-42d5-85e2-85537f4677d6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-55305 : blocage des fenêtres contextuelles lors de la modification des utilisateurs de l’entreprise dans [!UICONTROL My Account]

Le correctif ACSD-55305 corrige le problème où [!UICONTROL Edit Company User] fenêtre contextuelle sur la page [!UICONTROL My Account]> [!UICONTROL Company Structure] se fige avec un chargeur sur l’écran. Ce correctif est disponible lorsque la version 1.1.43 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-55305. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur se produit lors de la tentative d’utilisation de la fenêtre contextuelle *[!UICONTROL Edit Company User]* dans la page *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* , car celle-ci se fige avec un chargeur affiché à l’écran.

<u>Procédure à suivre </u> :

1. Créez une société B2B.
1. Créez un attribut à sélection multiple pour les clients.
1. Attribuez une valeur à l’attribut nouvellement créé pour l’administrateur de la société.
1. Connectez-vous en tant qu’administrateur d’entreprise.
1. Accédez à la [!UICONTROL account dashboard] et à la **[!UICONTROL Company Structure]**.
1. Sélectionnez l’utilisateur.
1. Cliquez sur **[!UICONTROL Edit Selected]**.

<u>Résultats attendus</u> :

La fenêtre contextuelle du formulaire s’affiche avec précision, ce qui permet de modifier les informations de la société.

<u>Résultats réels</u> :

La fenêtre contextuelle du formulaire s’affiche sans possibilité de modification.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
