---
title: 'ACSD-56979 : images de produit supprimées après la suppression de la mise à jour d’évaluation'
description: Appliquez le correctif ACSD-56979 pour résoudre le problème d’Adobe Commerce en raison duquel les images des produits sont supprimées après la suppression d’une mise à jour d’évaluation
feature: Products
role: Admin, Developer
exl-id: 1e0fbd5c-285b-408e-ba52-72619e29167b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-56979 : images de produit supprimées après la suppression de la mise à jour d’évaluation

Le correctif ACSD-56979 corrige le problème de suppression des images de produits après la suppression d’une mise à jour d’évaluation. Ce correctif est disponible lorsque la version 1.1.49 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-56979. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions Adobe Commerce et Magento Open Source :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les images de produit sont supprimées après la suppression d’une mise à jour d’évaluation.

<u>Procédure à suivre </u> :

1. Dans la barre latérale d’administration de Commerce, accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et créez un produit.
1. Sous **[!UICONTROL Images and Videos]**, chargez une image et enregistrez le produit.
1. Dans la zone de **[!UICONTROL Scheduled Changes]**, sélectionnez **[!UICONTROL Schedule New Update]**.
   1. Choisissez une date de début située dans le futur.
   1. Ne choisissez pas de date de fin.
1. Dans la zone de **[!UICONTROL Scheduled Changes]**, sélectionnez le lien **[!UICONTROL View/Edit]**.
1. Accédez à **[!UICONTROL Remove from Update]** > **[!UICONTROL Delete the Update]** et sélectionnez **[!UICONTROL Done]**.
1. Actualisez la page.

<u>Résultats attendus</u> :

Puisque la mise à jour est supprimée avant la date de début planifiée, le produit doit rester le même.

<u>Résultats réels</u> :

Le contenu de l’image est perdu et affiche zéro octet.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
