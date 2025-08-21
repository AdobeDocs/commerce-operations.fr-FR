---
title: 'ACSD-62415 : le serveur principal d’Adobe Commerce se charge [!UICONTROL Categories] très lentement'
description: Appliquez le correctif ACSD-62415 pour résoudre le problème d’Adobe Commerce où les performances de la page [!UICONTROL Categories] dans le panneau [!UICONTROL Admin] se chargent très lentement lorsqu’un grand nombre de catégories d’ancrage sont présentes.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8040414630cf3c992e0d68d5693990f8f50fdbcb
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# ACSD-62415 : le serveur principal d’Adobe Commerce se charge **[!UICONTROL Categories]** très lentement lorsque des catégories d’ancrage sont présentes

Le correctif ACSD-62415 corrige le problème en raison duquel les performances de la page **[!UICONTROL Categories]** dans le panneau **[!UICONTROL Admin]** se chargent très lentement lorsqu’un grand nombre de catégories d’ancrage sont présentes. Ce correctif est disponible lorsque la version 1.1.68 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62415. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La page **[!UICONTROL Categories]** du panneau **[!UICONTROL Admin]** se charge très lentement lorsqu’un grand nombre de catégories d’ancrage sont présentes.

<u>Procédure à suivre </u> :

1. Générez des catégories d’ancres 3K.
1. Ouvrez **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** page dans le panneau **[!UICONTROL Admin]** .

<u>Résultats attendus</u> :

La page **[!UICONTROL Categories]** se charge rapidement et la requête ne doit pas être répétée 1 000 fois.

<u>Résultats réels</u> :

Le chargement prend entre 7 et 20 secondes et la requête est exécutée plus de 1 000 fois.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
