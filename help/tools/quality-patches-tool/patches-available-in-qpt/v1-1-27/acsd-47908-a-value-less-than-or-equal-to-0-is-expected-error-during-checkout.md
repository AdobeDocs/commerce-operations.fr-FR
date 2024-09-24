---
title: 'ACSD-47908: *Une valeur inférieure ou égale à 0 est attendue* erreur lors du passage en caisse'
description: Appliquez le correctif ACSD-47908 pour corriger l’erreur Adobe Commerce *Une valeur inférieure ou égale à 0 est attendue* lors de la sélection de la source et de la quantité à l’étape d’expédition lors du passage en caisse.
feature: Admin Workspace, Checkout, Orders
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-47908 : *Une valeur inférieure ou égale à 0 est attendue* erreur lors du passage en caisse

Le correctif ACSD-47908 corrige l’erreur *Une valeur inférieure ou égale à 0 est attendue* lors de la sélection de la source et de la quantité dans l’étape d’expédition lors du passage en caisse. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 est installé. L’ID de correctif est ACSD-47908. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’erreur suivante est générée lors de la sélection de la source et de la quantité dans l’étape d’expédition lors du passage en caisse : *Une valeur inférieure ou égale à 0 est attendue*.

<u>Conditions préalables</u> :

Installez les modules Adobe Commerce Inventory management (MSI).

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** et configurez plusieurs sources.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** et créez un nouveau stock.
   * Attribuez maintenant les sources au nouveau stock.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et modifiez au moins un produit.
   * Assurez-vous que les produits sont attribués aux nouvelles sources et indiquez la quantité disponible.
1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Orders]** et créez une nouvelle commande.
1. Ajoutez ces produits à la commande et placez-les.
1. Cliquez sur **[!UICONTROL Ship]**.
1. Sélectionnez la source à partir de laquelle vous souhaitez expédier l’image.
1. Indiquez la quantité de chaque article à expédier.
1. Rechargez la page.
1. Cliquez sur **[!UICONTROL Proceed to Shipment]**.

<u>Résultats attendus</u> :

La nouvelle page d’expédition s’ouvre sans erreur.

<u>Résultats réels</u> :

* La quantité saisie ne peut pas être validée.
* L’erreur suivante est générée : *Entrez une valeur inférieure ou égale à 0*.

  L’erreur est toutefois incohérente et peut ne pas toujours apparaître.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
