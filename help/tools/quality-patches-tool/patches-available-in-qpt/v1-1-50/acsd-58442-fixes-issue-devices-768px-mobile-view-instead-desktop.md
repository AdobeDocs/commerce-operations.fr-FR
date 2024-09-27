---
title: "ACSD-58442 : résolution du problème des périphériques avec une largeur de 768 px traités comme mobiles, provoquant le chargement du menu et de l’en-tête dans la vue mobile et non sur le bureau"
description: Appliquez le correctif ACSD-58442 pour résoudre le problème Adobe Commerce en raison duquel les appareils dont la largeur est de 768 px sont traités comme mobiles, ce qui entraîne le chargement du menu et de l’en-tête dans une vue mobile au lieu du bureau.
feature: Storefront
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# ACSD-58442 : corrige le problème des périphériques avec une largeur de 768 px traités comme mobiles, en raison duquel le menu et l’en-tête se chargeaient dans la vue mobile et non sur le bureau

Le correctif ACSD-58442 corrige le problème Adobe Commerce en raison duquel les appareils dont la largeur est de 768 pixels sont traités comme mobiles, ce qui entraîne le chargement du menu et de l’en-tête dans une vue mobile au lieu d’un bureau. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 est installé. L’ID de correctif est ACSD-58442. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le système traite désormais les périphériques dont la largeur est de 768 pixels comme des ordinateurs de bureau, en s’assurant que le menu et l’en-tête se chargent correctement. Auparavant, les appareils dont la largeur était de 768 px étaient traités comme mobiles, ce qui entraînait le chargement du menu et de l’en-tête dans une vue mobile.

<u>Étapes à reproduire</u> :

1. Chargez la page d’accueil sur une miniature iPad ou utilisez l’outil d’inspection d’un navigateur pour redimensionner le navigateur sur une largeur de *768px*.
1. Ouvrez le menu principal.

<u>Résultats attendus</u> :

Le menu et l’en-tête sont chargés en tant qu’affichage de bureau.

<u>Résultats réels</u> :

Le menu et l’en-tête se chargent sous la forme d’une vue mobile.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].


