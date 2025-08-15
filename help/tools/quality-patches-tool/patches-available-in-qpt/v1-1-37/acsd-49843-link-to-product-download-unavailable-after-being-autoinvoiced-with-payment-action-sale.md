---
title: 'ACSD 49843 : lien de téléchargement de produit indisponible après avoir été facturé automatiquement avec [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'
description: Appliquez le correctif ACSD-49843 pour résoudre le problème d'Adobe Commerce où le lien de téléchargement de produit n'est pas disponible après que l'article commandé a été facturé automatiquement par un mode de paiement en ligne lorsque [!UICONTROL Payment Action] est défini sur [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: e990b550-fb32-48d2-9c39-2176d7ab34c9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
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
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
