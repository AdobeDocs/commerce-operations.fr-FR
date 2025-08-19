---
title: 'ACP2E-3977 : le champ **[!UICONTROL Cap Reward Points Balance At]** ne peut pas être laissé vide'
description: Appliquez le correctif ACP2E-3977 pour résoudre le problème d’Adobe Commerce en raison duquel le champ **[!UICONTROL Cap Reward Points Balance At]** ne pouvait pas être laissé vide lorsque le champ **[!UICONTROL Rewards Points Balance Redemption Threshold]** était défini, ce qui provoquait une erreur de validation.
feature: Configuration, Rewards
role: Admin, Developer
source-git-commit: 4fd9b66967639f3afff322bfd82e68cfb79b2138
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# ACP2E-3977 : **[!UICONTROL Cap Reward Points Balance At]** champ ne peut pas être laissé vide

Le correctif ACP2E-3977 corrige le problème où **[!UICONTROL Cap Reward Points Balance At]** champ ne peut pas être laissé vide, même s’il doit être autorisé. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACP2E-3977. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p10

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le fait de laisser **[!UICONTROL Cap Reward Points Balance At]** vide déclenche une erreur de validation, même si la limite doit être désactivée lorsqu’elle est laissée vide.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward points]**.
1. **[!UICONTROL Rewards Points Balance Redemption Threshold]** = *30*.
1. Laissez **[!UICONTROL Cap Reward Points Balance At]** vide.
1. Enregistrer.

<u>Résultats attendus</u> :

Une valeur vide pour **[!UICONTROL Cap Reward Points Balance At]** est autorisée et désactive la limitation.

<u>Résultats réels</u> :

*Le solde des points de récompense plafonnés n&#39;est pas valide. Le solde doit être un nombre positif ou laissé vide. Vérifiez et réessayez.* erreur s’affiche.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
