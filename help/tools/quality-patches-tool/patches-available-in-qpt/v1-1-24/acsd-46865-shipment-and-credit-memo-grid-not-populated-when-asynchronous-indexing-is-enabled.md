---
title: 'ACSD-46865 : [!UICONTROL shipment] et [!UICONTROL credit memo] non renseignés lorsque [!UICONTROL asynchronous indexing] est activé'
description: Appliquez le correctif ACSD-46865 pour résoudre le problème d’Adobe Commerce où les grilles [!UICONTROL shipment] et [!UICONTROL credit memo] ne sont pas renseignées lorsque [!UICONTROL asynchronous indexing] est activé.
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 6f84f5b6-6c34-476c-aae5-9a8ba306f8e4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46865 : [!UICONTROL shipment] et [!UICONTROL credit memo] non renseignés lorsque [!UICONTROL asynchronous indexing] est activé

Le correctif ACSD-46865 corrige le problème où les grilles [!UICONTROL shipment] et [!UICONTROL credit memo] ne sont pas renseignées lorsque [!UICONTROL asynchronous indexing] est activé. Ce correctif est disponible lorsque la version 1.1.24 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-46865. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les grilles [!UICONTROL Shipment] et [!UICONTROL credit memo] ne sont pas renseignées lorsque [!UICONTROL asynchronous indexing] est activé.

<u>Procédure à suivre </u> :

1. Dans [!DNL Commerce] Admin, accédez à **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *YES*.
2. Accédez à nouveau à **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Nettoyez le cache de configuration.
4. Passer une nouvelle commande d&#39;invité pour un produit simple.
5. Exécutez cron.
6. Ouvrez la commande dans l&#39;administrateur [!UICONTROL Commerce] en accédant à **[!UICONTROL Sales]** > **[!UICONTROL Orders]** et générez une facture et un avoir.
7. Déplacez la commande vers [!UICONTROL Archive].
8. Créez une autre commande pour un produit simple.
9. Exécutez cron.
10. Accédez à la nouvelle commande et générez une nouvelle livraison, une facture et un avoir.
11. Exécutez cron.
12. Vérifiez les grilles [!UICONTROL shipments], [!UICONTROL invoices] et [!UICONTROL credit memo] dans l’administration.

<u>Résultats attendus</u> :

Les nouveaux [!UICONTROL shipment], [!UICONTROL invoice] et [!UICONTROL credit memo] s’affichent.

<u>Résultats réels</u> :

Les nouveaux [!UICONTROL shipment], [!UICONTROL invoice] et [!UICONTROL credit memo] ne s’affichent pas.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
