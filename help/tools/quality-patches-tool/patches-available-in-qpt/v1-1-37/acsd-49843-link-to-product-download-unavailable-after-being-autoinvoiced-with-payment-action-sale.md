---
title: 'ACSD 49843 : lien de téléchargement de produit indisponible après avoir été facturé automatiquement avec [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'
description: Appliquez le correctif ACSD-49843 pour résoudre le problème d'Adobe Commerce où le lien de téléchargement de produit n'est pas disponible après que l'article commandé a été facturé automatiquement par un mode de paiement en ligne lorsque [!UICONTROL Payment Action] est défini sur [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: e990b550-fb32-48d2-9c39-2176d7ab34c9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
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
source-wordcount: '510'
ht-degree: 0%
---
# ACSD-49843 : lien de téléchargement de produit indisponible après avoir été facturé automatiquement avec [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

Le correctif ACSD-49843 corrige le problème en raison duquel le lien de téléchargement du produit n’est pas disponible après que l’article commandé a été facturé automatiquement par un mode de paiement en ligne lorsque [!UICONTROL Payment Action] est défini sur [!UICONTROL Intent Sale]. Ce correctif est disponible lorsque la version 1.1.37 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-49843. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le lien de téléchargement de produit n’est pas disponible une fois que l’article commandé a été facturé automatiquement par un mode de paiement en ligne lorsque [!UICONTROL Payment Action] est défini sur [!UICONTROL Intent Sale].

<u>Procédure à suivre </u> :

1. Connectez-vous à l’administration Adobe Commerce et accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * Dans la liste déroulante [!UICONTROL Payment Action], sélectionnez **[!UICONTROL Intent Sale]** et définissez *[!UICONTROL Enable Card Payments]* sur *Oui*.

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]**, et assurez-vous qu’il est défini sur *« Facturé »*.
1. Dans le storefront, connectez-vous en tant que client.

   * Ajoutez au panier n’importe quel produit téléchargeable ainsi qu’un produit simple.
   * Utilisez [!DNL Braintree Pay] pour passer la commande à l’aide de l’option de carte .

1. Accédez à **[!UICONTROL My Orders]** et vérifiez que la facture est automatiquement créée pour la commande et que les deux statuts d&#39;article sont *« Facturé »*.
1. Accédez à **[!UICONTROL My Downloadable Products]** et notez que le lien de téléchargement n’est pas encore disponible.
1. Dans l’administrateur, accédez à cette commande et créez une expédition pour elle.
1. Dans le storefront, accédez à **[!UICONTROL My Downloadable Products]** et notez que le lien de téléchargement est maintenant disponible.

<u>Résultats attendus</u> :

Le lien de téléchargement est disponible lorsque le statut du produit téléchargeable est *« Facturé »*.

<u>Résultats réels</u> :

Le lien de téléchargement n’est pas disponible même lorsque le statut du produit téléchargeable indique *« Facturé »*. Il n&#39;est disponible qu&#39;après la création d&#39;une expédition pour le produit physique.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
