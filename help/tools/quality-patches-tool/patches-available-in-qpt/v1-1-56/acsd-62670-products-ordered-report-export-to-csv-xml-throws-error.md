---
title: 'ACSD-62670 : [!UICONTROL Ordered Products Report] exportation au format CSV et XML renvoie une erreur 404'
description: Appliquez le correctif ACSD-62670 pour résoudre le problème d’Adobe Commerce où l’exportation du [!UICONTROL Ordered Products Report] au format CSV et XML renvoie une erreur.
feature: Reporting, Admin Workspace, Data Import/Export
role: Admin, Developer
exl-id: 99d77ddd-4fb3-4eda-8771-62c0e25f49d1
type: Troubleshooting
source-git-commit: 3469da56c15499de4ceb5313c3cc2dfde0f0771c
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# ACSD-62670 : *[!UICONTROL Ordered Products Report]* exportation au format CSV et XML renvoie une erreur

Le correctif ACSD-62670 corrige le problème en raison duquel l’exportation du *[!UICONTROL Ordered Products Report]* au format CSV et XML renvoie une erreur. Ce correctif est disponible lorsque la version 1.1.56 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) est installée. L’ID du correctif est ACSD-62670. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’exportation du *[!UICONTROL Ordered Products Report]* au format CSV et XML renvoie une erreur.

<u>Procédure à suivre </u> :

1. Accédez au panneau *Admin* et accédez à **[!UICONTROL Reports]** > **[!UICONTROL Products]** > **[!UICONTROL Ordered]**.
1. Essayez d’exporter des fichiers CSV ou Excel.

<u>Résultats attendus</u> :

Les rapports sont exportés sans erreur.

<u>Résultats réels</u> :

L&#39;exportation du *[!UICONTROL Ordered Products Report]* entraîne l&#39;erreur 404.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
