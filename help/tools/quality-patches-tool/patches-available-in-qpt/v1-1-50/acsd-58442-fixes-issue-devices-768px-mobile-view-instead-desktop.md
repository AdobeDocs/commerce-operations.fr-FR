---
title: 'ACSD-58442 : correction du problème en raison duquel les appareils d’une largeur de 768 pixels étaient traités comme des appareils mobiles, ce qui entraînait le chargement du menu et de l’en-tête dans la vue mobile et non sur le bureau'
description: Appliquez le correctif ACSD-58442 pour résoudre le problème d’Adobe Commerce où les appareils d’une largeur de 768 px sont traités comme des appareils mobiles, ce qui entraîne le chargement du menu et de l’en-tête dans une vue mobile plutôt que sur le bureau.
feature: Storefront
role: Admin, Developer
exl-id: 86ea64aa-10fc-4fa3-9902-918fb8983ca0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-58442 : correction du problème en raison duquel les appareils d’une largeur de 768 pixels étaient traités comme des appareils mobiles, ce qui entraînait le chargement du menu et de l’en-tête dans la vue mobile et non sur le bureau

Le correctif ACSD-58442 corrige le problème d’Adobe Commerce où les appareils d’une largeur de 768 px sont traités comme des appareils mobiles, ce qui entraîne le chargement du menu et de l’en-tête dans une vue mobile au lieu d’un bureau. Ce correctif est disponible lorsque la version 1.1.50 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-58442. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le système traite désormais les appareils d’une largeur de 768 pixels comme des ordinateurs de bureau, en s’assurant que le menu et l’en-tête se chargent correctement. Auparavant, les appareils d’une largeur de 768 pixels étaient traités comme des appareils mobiles, ce qui entraînait le chargement du menu et de l’en-tête dans une vue mobile.

<u>Procédure à suivre </u> :

1. Chargez la page d’accueil sur un iPad Mini ou utilisez l’outil d’inspection du navigateur pour redimensionner le navigateur à une largeur de 768 px **.
1. Ouvrez le menu principal.

<u>Résultats attendus</u> :

Le menu et l’en-tête se chargent comme une vue de bureau.

<u>Résultats réels</u> :

Le menu et l’en-tête se chargent en tant que vue mobile.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
