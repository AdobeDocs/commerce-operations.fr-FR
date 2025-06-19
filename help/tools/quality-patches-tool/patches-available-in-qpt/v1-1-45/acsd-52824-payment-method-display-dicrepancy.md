---
title: 'ACSD-52824 : modes de paiement désactivés affichés pour les clients de l''entreprise'
description: Appliquez le correctif ACSD-52824 pour résoudre le problème d’Adobe Commerce où les modes  [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay]  paiement apparaissent pour les clients de la société bien qu’ils soient désactivés dans les paramètres de la société.
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 39d67de6-1796-4067-ae7a-ef17fcf794e5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-52824 : modes de paiement désactivés affichés pour les clients de l&#39;entreprise

Le correctif ACSD-52824 corrige le problème d’affichage des modes de paiement [!DNL PayPal Express], [!DNL Google Pay] et [!DNL Apple Pay] pour les clients de l’entreprise, bien que désactivés dans les paramètres de l’entreprise. Ce correctif est disponible lorsque la version 1.1.45 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-52824. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les modes de paiement désactivés s&#39;affichent pour les clients de la société.

<u>Procédure à suivre </u> :

1. Configurez et activez [!DNL PayPal Express Checkout]. Accédez à **[!UICONTROL Basic Settings]** > sélectionnez **[!DNL PayPal Express Checkout]** et définissez l’option de **[!UICONTROL Display on Shopping Cart]** sur *Oui*.
1. Configurez [!DNL Braintree] et activez les [!DNL Apple Pay] et les [!DNL Google Pay] via [!DNL Braintree].
1. Accédez à **[!UICONTROL Customers]** > **[!UICONTROL Companies]** et créez une nouvelle société.
1. Cliquez sur **[!UICONTROL Advanced Settings]**, recherchez le **[!UICONTROL Applicable Payment Methods]** et choisissez **[!UICONTROL Selected Payment Methods]**.
1. Sous **[!UICONTROL Selected Payment Methods]**, choisissez les modes de paiement activés et non associés à *[!DNL PayPal Express Checkout]*, *[!DNL Apple Pay]* ou *[!DNL Google Pay]*. Par exemple, sélectionnez **[!UICONTROL Check/Money Order]**.
1. Après avoir sélectionné les modes de paiement appropriés, créez un nouveau client et associez-le à la société créée précédemment.
1. Connectez-vous avec le compte client associé à la société et continuez à ajouter des articles au panier.
1. Surveillez le mini panier, le panier et l’étape de paiement pendant le processus de passage en caisse.

<u>Résultats attendus</u> :

Les options de paiement de [!DNL PayPal] et [!DNL Braintree] ne sont pas visibles dans le mini panier et le panier.

<u>Résultats réels</u> :

Les options de paiement de [!DNL PayPal] et [!DNL Braintree] restent visibles dans le mini panier et le panier.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
