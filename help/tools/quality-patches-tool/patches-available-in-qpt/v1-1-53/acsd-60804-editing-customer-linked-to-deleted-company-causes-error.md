---
title: 'ACSD-60804 : la modification d’un client associé à une entreprise supprimée entraîne une erreur'
description: Appliquez le correctif ACSD-60804 pour résoudre le problème d'Adobe Commerce où la modification d'un client associé à une société supprimée provoque une erreur *Appel à une fonction membre getSuperUserId() sur null*.
feature: Companies, Customers, B2B
role: Admin, Developer
exl-id: 09241160-f5ed-41f8-8bb6-2bb8ed5cccd5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-60804 : la modification d’un client associé à une entreprise supprimée entraîne une erreur

Le correctif ACSD-60804 corrige le problème où la modification d&#39;un client associé à une entreprise supprimée provoque une erreur *Appel à une fonction membre getSuperUserId() sur null*. Ce correctif est disponible lorsque la version 1.1.53 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-60804. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La modification d’un client associé à une entreprise supprimée entraîne une erreur *Appel à une fonction membre getSuperUserId() sur null*.

<u>Conditions préalables requises:</u> :

Installation et activation des modules B2B Adobe Commerce.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Settings]** > **[!UICONTROL B2B]** > **[!UICONTROL Enable Company]**.
1. Accédez à **[!UICONTROL Customers]** > **[!UICONTROL Company]** > **[!UICONTROL Create New Company]**.
1. Connectez-vous à `mysql` pour l’instance .
1. Supprimez la société où `entity_id` = *1*.
1. Accédez à **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Modifiez le client qui a été automatiquement créé lors de la création de la société.

<u>Résultats attendus</u> :

Le client est modifié sans qu’une erreur d’exception ne soit générée.

<u>Résultats réels</u> :

Une erreur se produit : *Appel à une fonction membre getSuperUserId() sur null* si aucune société n&#39;est associée au client.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
