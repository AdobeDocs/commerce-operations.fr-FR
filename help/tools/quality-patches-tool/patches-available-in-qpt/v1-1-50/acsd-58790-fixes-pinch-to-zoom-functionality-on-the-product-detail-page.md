---
title: 'ACSD-58790 : corrige la fonctionnalité de pincement pour zoomer sur les images de la page des détails du produit en mode mobile sur  [!DNL Chrome]'
description: ACSD-58790 corrige le problème d’Adobe Commerce en raison duquel l’image en mode mobile on [!DNL Chrome] n’a pas effectué le zoom avant prévu sur l’image.
feature: Storefront
role: Admin, Developer
exl-id: 46b324bf-c2a0-4086-87ee-96e8c4883494
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-58790 : corrige la fonctionnalité de pincement pour zoomer sur les images de la page des détails du produit en mode mobile sur [!DNL Chrome]

Le correctif ACSD-58790 corrige le problème d’Adobe Commerce en raison duquel l’image en mode mobile sur [!DNL Chrome] n’a pas effectué le zoom avant prévu sur l’image. Ce correctif est disponible lorsque la version 1.1.50 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-58790. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Correction de la fonctionnalité de pincement pour zoomer sur les images de la page des détails du produit en mode mobile sur [!DNL Chrome].

<u>Procédure à suivre </u> :

1. Créez un produit avec une image.
1. Ouvrez le produit à partir d’un navigateur [!DNL Chrome].
1. Cliquez sur l’image et vérifiez que l’image effectue un zoom sur un double-clic.
1. Basculez vers la vue mobile à l’aide des outils de développement [!DNL Chrome].
1. Cliquez sur l’image.
1. Appuyez deux fois.

<u>Résultats attendus</u> :

Lorsque vous double-cliquez dessus, l’image effectue un zoom avant.

<u>Résultats réels</u> :

L’image n’effectue pas de zoom avant lorsque vous double-cliquez dessus. Ce problème est spécifique aux [!DNL Chrome] en mode mobile, car la fonctionnalité de zoom fonctionne comme prévu dans [!DNL Firefox].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
