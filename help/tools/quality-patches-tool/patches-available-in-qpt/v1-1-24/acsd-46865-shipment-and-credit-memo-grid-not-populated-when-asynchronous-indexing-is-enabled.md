---
title: 'ACSD-46865 : [!UICONTROL shipment] et [!UICONTROL credit memo] non renseignés lorsque [!UICONTROL asynchronous indexing] est activé'
description: Appliquez le correctif ACSD-46865 pour résoudre le problème d’Adobe Commerce où les grilles [!UICONTROL shipment] et [!UICONTROL credit memo] ne sont pas renseignées lorsque [!UICONTROL asynchronous indexing] est activé.
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 6f84f5b6-6c34-476c-aae5-9a8ba306f8e4
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%
---
# ACSD-46865 : [!UICONTROL shipment] et [!UICONTROL credit memo] non renseignés lorsque [!UICONTROL asynchronous indexing] est activé

Le correctif ACSD-46865 corrige le problème où les grilles [!UICONTROL shipment] et [!UICONTROL credit memo] ne sont pas renseignées lorsque [!UICONTROL asynchronous indexing] est activé. Ce correctif est disponible lorsque la version 1.1.24 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-46865. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
