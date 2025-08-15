---
title: 'ACSD-58471 : le chargement du contenu dynamique échoue sur la page des détails du produit, lorsque les règles de prix de catalogue associées ont été planifiées'
description: Appliquez le correctif ACSD-58471 pour résoudre le problème d’Adobe Commerce en raison duquel le contenu dynamique ne se charge pas sur la page des détails du produit, au moment où les règles de prix de catalogue associées étaient planifiées.
feature: Catalog Management
role: Admin, Developer
exl-id: 6ff68b74-67fc-400c-aa79-a1274fd19708
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-58471 : le chargement du contenu dynamique échoue sur la page des détails du produit, lorsque les règles de prix de catalogue associées ont été planifiées

Le correctif ACSD-58471 résout le problème où le contenu dynamique ne se charge pas sur la page des détails du produit, au moment où les règles de prix de catalogue associées étaient planifiées. Le système affiche désormais correctement le contenu dynamique associé aux règles de prix de catalogue planifiées sur la page des détails du produit. Ce correctif est disponible lorsque la version 1.1.55 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-58471. Notez que ce problème doit être résolu dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p4

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le contenu dynamique ne se charge pas sur la page des détails du produit lorsque des règles de prix de catalogue sont planifiées.

<u>Procédure à suivre </u> :

1. Créez un bloc dynamique dans le [!UICONTROL Admin] Commerce > **[!UICONTROL Content]** > **[!UICONTROL Dynamic Blocks]**.
1. Créez un bloc statique dans [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Blocks]**. Utilisez des widgets pour ajouter du contenu.
1. Créez un produit et ajoutez le bloc CMS à la description.
1. Créez une règle de catalogue avec une mise à jour planifiée et affectez le produit et le bloc dynamique créé dans **[!UICONTROL Marketing]** > Promotions > **[!UICONTROL Catalog Products Rules]**.
1. Exécutez le cron et vérifiez que la page des détails du produit affiche le contenu dynamique après l’heure de début planifiée.
1. Créez une règle de catalogue sans mise à jour planifiée et affectez le produit et le bloc dynamique créé dans **[!UICONTROL Marketing]** > Promotions > **[!UICONTROL Catalog Products Rules]**.
1. Exécutez le cron et vérifiez si la page des détails du produit affiche le contenu dynamique après l’heure planifiée.


<u>Résultats attendus</u> :

Le contenu dynamique se charge après l’heure de début planifiée.

<u>Résultats réels</u> :

Le contenu dynamique ne se charge pas.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
