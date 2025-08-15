---
title: 'ACSD-59514 : Forms dans l’administration avec une erreur de  [!DNL Page Builder]  dans la console du navigateur'
description: Appliquez le correctif ACSD-59514 pour résoudre le problème d’Adobe Commerce en raison duquel les formulaires dans l’administration avec l’erreur «  [!DNL Page Builder]  générait le rendu pendant 5 secondes sans libérer les verrous » [!DNL Page Builder]’affichaient pas. dans la console du navigateur après l’envoi du formulaire, les modifications ne peuvent pas être enregistrées.
feature: Page Builder
role: Admin, Developer
exl-id: 3d1167d2-0a75-48ac-bc31-5bbd3c4a409e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-59514 : Forms dans Admin avec [!DNL Page Builder] erreur de renvoi dans la console du navigateur

Le correctif ACSD-59514 corrige le problème en raison duquel les formulaires dans Admin avec [!DNL Page Builder] renvoyaient l’erreur *[!DNL Page Builder]étaient rendus pendant 5 secondes sans libérer les verrous.* dans la console du navigateur après l’envoi du formulaire et les modifications ne peuvent pas être enregistrées. Ce correctif est disponible lorsque la version 1.1.50 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-59514. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Forms dans Admin avec [!DNL Page Builder] renvoie l’erreur *[!DNL Page Builder]a effectué le rendu pendant 5 secondes sans libérer les verrous.* dans la console du navigateur après l’envoi du formulaire et les modifications ne peuvent pas être enregistrées.

<u>Conditions préalables</u> :

Les modules Adobe Commerce [!DNL Page Builder] sont installés et activés.

<u>Procédure à suivre </u> :

1. Ouvrez le panneau d’administration et cliquez sur le bouton [!UICONTROL Content] .
1. Sélectionnez le bloc et modifiez-le.
1. Modifiez le contenu et cliquez sur [!UICONTROL Save].
1. Ouvrez la console et affichez le message d’erreur.

<u>Résultats attendus</u> :

Le bloc est enregistré avec succès.

<u>Résultats réels</u> :

Le chargeur ne cesse de tourner et le bloc n’est pas enregistré. L’erreur suivante s’affiche dans la console du navigateur :
*[!DNL Page Builder]a effectué un rendu pendant 5 secondes sans libérer les verrous.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
