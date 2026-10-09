---
title: 'ACSD-64149 : le segment client avec une condition de [!UICONTROL Date range] peut être enregistré lorsqu’une seule date est modifiée'
description: Appliquez le correctif ACSD-64149 pour résoudre le problème d’Adobe Commerce où le segment client avec une condition **[!UICONTROL Date range]** peut être enregistré lorsqu’une seule des dates est modifiée.
feature: Customers, Admin Workspace
role: Admin, Developer
exl-id: 5423bbd3-75e9-4137-b2d5-3a0ceb3384ad
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%
---
# ACSD-64149 : le segment client avec une condition de [!UICONTROL Date range] peut être enregistré lorsqu’une seule date est modifiée

Le correctif ACSD-64149 corrige le problème où un segment client avec une condition de période peut être enregistré lorsqu’une seule des dates est modifiée. Ce correctif est disponible lorsque la version 1.1.60 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64149. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de la modification d’un segment client existant avec une condition sur des produits dans le panier spécifié par une période, le `matchCustomerSegmentProcessor` de clients échoue avec une erreur SQL.

<u>Procédure à suivre </u> :

1. Assurez-vous que le `matchCustomerSegmentProcessor` de consommateurs est en cours d’exécution :

   ```shell
   $ bin/magento que:cons:st matchCustomerSegmentProcessor
   ```

1. Allez à la **[!UICONTROL Magento backend]**.
1. Accédez à **[!UICONTROL Customers]** > **[!UICONTROL Segments]**.
1. Cliquez sur **[!UICONTROL Add Segment]**.
1. Saisissez un **[!UICONTROL Segment Name]**, sélectionnez un site web sous **[!UICONTROL Assigned to Website]** et assurez-vous que le **[!UICONTROL Status]** est défini sur *Actif*.
1. Cliquez sur **[!UICONTROL Save and Continue Edit]**.
1. Accédez à l’onglet **[!UICONTROL Conditions]** et ajoutez une nouvelle condition : *Produits{} > {}Liste de produits*{*}*.
1. Ajoutez une sous-condition pour la **[!UICONTROL Date range]** et définissez une **[!UICONTROL Date range]** valide.
1. Cliquez sur le bouton de confirmation vert en regard de la **[!UICONTROL Date range]**.
1. Cliquez à nouveau sur le **[!UICONTROL Date range]**, sélectionnez le sélecteur de dates, modifiez l’une des valeurs de date et confirmez en cliquant sur le bouton vert.

<u>Résultats attendus</u> :

Le sélecteur de **[!UICONTROL Date range]** ne doit pas ajouter d’heure à la date lors de la modification.

<u>Résultats réels</u> :

* Le sélecteur de **[!UICONTROL Date range]** ajoute une heure à la date :
  * Une seule date comporte la date, tandis que l’autre contient la date et l’heure spécifiées.
* L’erreur suivante s’affiche dans les journaux :

  ```yaml
  report.CRITICAL: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 2, query was: SELECT `item`.`quote_id` FROM `quote_item` AS `item`
  INNER JOIN `quote` AS `list` ON item.quote_id = list.entity_id WHERE (list.is_active = 1) AND () [] []
  ```


## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : mises à niveau et correctifs > Appliquer des correctifs dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
