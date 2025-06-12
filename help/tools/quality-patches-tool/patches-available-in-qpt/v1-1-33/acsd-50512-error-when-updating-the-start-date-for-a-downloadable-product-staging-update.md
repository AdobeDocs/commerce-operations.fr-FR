---
title: 'ACSD-50512 : erreur lors de la mise à jour de la date de début d’une mise à jour d’évaluation de produit téléchargeable'
description: Appliquez le correctif ACSD-51892 pour résoudre le problème de performances d’Adobe Commerce où l’erreur *Le lien téléchargeable n’est pas associé au produit.Vérifiez le lien et réessayez*, se produit lors de la mise à jour de la date de début d’une mise à jour d’évaluation de produit téléchargeable.
feature: Products, Staging
role: Admin
exl-id: 9c3b4d45-c500-46a7-8679-a8aa9e0a66d6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-50512 : erreur lors de la mise à jour de la date de début de la mise à jour intermédiaire du produit téléchargeable

Le correctif ACSD-50512 corrige le problème où l’erreur *Le lien téléchargeable n’est pas lié au produit. Vérifiez le lien et réessayez* se produit lors de la mise à jour de la date de début d’une mise à jour d’évaluation de produit téléchargeable. Ce correctif est disponible lorsque la version 1.1.33 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51502. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’erreur *Le lien téléchargeable n’est pas lié au produit. Vérifiez le lien et réessayez* se produit lors de la mise à jour de la date de début d’une mise à jour d’évaluation de produit téléchargeable.

<u>Procédure à suivre </u> :

1. Créez un produit téléchargeable, avec des *liens téléchargeables* et des *exemples de liens*.
1. Créez une mise à jour planifiée pour le même produit et enregistrez-le.
1. Modifiez la mise à jour planifiée préconfigurée (à partir de l’étape 2) et modifiez la date de début.
1. Enregistrez la mise à jour planifiée.

<u>Résultats attendus</u> :

Les modifications apportées à la mise à jour planifiée sont enregistrées avec succès.

<u>Résultats réels</u> :

Vous obtenez l’erreur : *Le lien téléchargeable n’est pas associé au produit. Vérifiez le lien et réessayez*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
