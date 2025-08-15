---
title: 'ACSD-52219 : résolution du problème de filtre des grilles d’administration dans le changement d’affichage des signets'
description: Appliquez le correctif ACSD-52219 pour résoudre le problème d’Adobe Commerce en raison duquel les filtres enregistrés des grilles d’administration ne fonctionnent pas comme prévu lorsque vous basculez fréquemment entre les vues de signets.
feature: Admin Workspace
role: Admin
exl-id: 3f1af6ba-88a0-480c-b16e-c00c655e346f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-52219 : résolution du problème de filtre des grilles d’administration dans le changement d’affichage des signets

Le correctif ACSD-52219 corrige le problème en raison duquel les filtres enregistrés des grilles d’administration ne fonctionnent pas comme prévu lorsque vous basculez fréquemment entre les vues de signets. Ce correctif est disponible lorsque la version 1.1.39 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-52219. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque vous basculez fréquemment entre les vues de signet, les filtres enregistrés dans les grilles d’administration ne fonctionnent pas comme prévu.

<u>Procédure à suivre </u> :

1. Accédez à la grille de [!DNL Sales Order] dans l’Admin.
1. Créez deux à trois filtres.
1. Vérifiez les paramètres de filtre en changeant de vue pour vous assurer qu’ils sont enregistrés avec précision.
1. Accédez à Filtre1 ou Filtre2.
1. Actualisez la page pour mettre à jour les données affichées.
1. Basculez vers une autre vue et notez que les filtres restent inchangés.
1. Notez que la vue par défaut affiche désormais les résultats filtrés, même si aucun filtre spécifique n’a été défini pour celle-ci.

<u>Résultats attendus</u> :

Les filtres ne sont pas intervertis et conservent leur état d’origine.

<u>Résultats réels</u> :

Lors de la modification d’une vue, les filtres sont mélangés et la vue correcte n’est pas enregistrée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
