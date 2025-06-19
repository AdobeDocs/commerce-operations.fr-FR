---
title: 'ACSD-57565 : le tableau de bord des commandes affiche des informations de commande incorrectes'
description: Appliquez le correctif ACSD-57565 pour résoudre le problème d’Adobe Commerce où le tableau de bord des commandes affiche des informations de commande incorrectes jusqu’à ce que la période soit mise à jour.
feature: Roles/Permissions
role: Admin, Developer
exl-id: dc4ad263-725e-4605-9b85-fc4305ab9a29
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-57565 : le tableau de bord des commandes affiche des informations de commande incorrectes

Le correctif ACSD-57565 corrige le problème où le tableau de bord des commandes affiche des informations de commande incorrectes jusqu’à ce que la période soit mise à jour. Ce correctif est disponible lorsque la version 1.1.48 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-57565. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif

## Problème

Le tableau de bord des commandes affiche des informations de commande incorrectes.

<u>Procédure à suivre </u> :

1. Activez **[!UICONTROL dashboard charts]**.
1. Créez une commande et facturez-la.
1. Patientez au moins 24 heures après la création de la commande.
1. Vérifiez les données **[!UICONTROL dashboard chart]**.
1. Notez le nombre complet de commandes.
1. Remplacez l’heure par *mois en cours*, puis revenez à *aujourd’hui*.

<u>Résultats attendus</u> :

Le graphique du tableau de bord doit afficher en permanence les statistiques correctes.

<u>Résultats réels</u> :

Le graphique de tableau de bord affiche des statistiques incorrectes au premier chargement. Les statistiques précises du graphique sont mises à jour après la période.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
