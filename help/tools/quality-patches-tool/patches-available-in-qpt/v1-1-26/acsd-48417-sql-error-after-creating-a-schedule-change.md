---
title: 'ACSD-48417 : erreur SQL après la création d’une modification de planning'
description: Appliquez le correctif ACSD-48417 pour résoudre le problème d’Adobe Commerce où une erreur SQL apparaît après la création d’une modification de planning pour un produit et l’enregistrement d’un autre produit.
feature: Storage
role: Admin
exl-id: c8e7c7aa-ac53-4218-8c3c-ea2240af17c9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-48417 : erreur SQL après la création d’une modification de planning

Le correctif ACSD-48417 corrige le problème d’apparition d’une erreur SQL après la création d’une modification de planification pour un produit et l’enregistrement d’un autre produit. Ce correctif est disponible lorsque la version 1.1.26 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48417. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur SQL apparaît après la création d’une modification de planification pour un produit et l’enregistrement d’un autre produit.

<u>Procédure à suivre </u> :

1. Installer Magento 2.4-développer EE + Données d’exemple.
1. Accédez au panneau d’administration > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Modifiez n&#39;importe quel produit (par exemple, Joust Duffle Bag [SKU : 24-MB01]).
1. Planifier une nouvelle mise à jour :
   * Sélectionner un **[!UICONTROL Save as a New Update]**
   * Nom de la mise à jour : « Mise à jour 1 »
   * Date de début : heure actuelle + 1 min
   * Date de fin : heure actuelle +1 heure
   * Remplacer le nom du produit par : « Joust Duffle Bag 2 »
   * Enregistrez le produit.
1. Accédez à l’interface de ligne de commande, exécutez cron et attendez que le planning soit appliqué.

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. Encore une fois, accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et modifiez tout produit configurable (par exemple, Chaz Kangeroo Hoodie [SKU : MH01]).

   * Désactivez toutes les variantes. Accédez à la colonne Actions > **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**.
   * Enregistrez le paramètre configurable.

<u>Résultats attendus</u> :

Aucune erreur lors de l’enregistrement du produit.

<u>Résultats réels</u> :

L’erreur suivante se produit :

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
