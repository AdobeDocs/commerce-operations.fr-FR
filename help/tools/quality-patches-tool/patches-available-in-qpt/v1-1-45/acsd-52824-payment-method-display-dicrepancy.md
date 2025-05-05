---
title: "ACSD-52824 : méthodes de paiement désactivées affichées pour les clients de l’entreprise"
description: Appliquez le correctif ACSD-52824 pour résoudre le problème Adobe Commerce où les méthodes de paiement  [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] apparaissent pour les clients de l’entreprise même s’ils sont désactivés dans les paramètres de l’entreprise.
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-52824 : Méthodes de paiement désactivées affichées pour les clients de l’entreprise

Le correctif ACSD-52824 corrige le problème en raison duquel les méthodes de paiement [!DNL PayPal Express], [!DNL Google Pay] et [!DNL Apple Pay] apparaissent pour les clients de l’entreprise, même si elles sont désactivées dans les paramètres de l’entreprise. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45 est installé. L’ID de correctif est ACSD-52824. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les modes de paiement désactivés s’affichent pour les clients de l’entreprise.

<u>Étapes à reproduire</u> :

1. Configurez et activez [!DNL PayPal Express Checkout]. Accédez à **[!UICONTROL Basic Settings]** > sélectionnez **[!DNL PayPal Express Checkout]** et définissez l’option de **[!UICONTROL Display on Shopping Cart]** sur *Oui*.
1. Configurez [!DNL Braintree] et activez [!DNL Apple Pay] et [!DNL Google Pay] à [!DNL Braintree].
1. Accédez à **[!UICONTROL Customers]** > **[!UICONTROL Companies]** et créez une nouvelle société.
1. Cliquez sur **[!UICONTROL Advanced Settings]**, recherchez **[!UICONTROL Applicable Payment Methods]** et choisissez **[!UICONTROL Selected Payment Methods]**.
1. Sous **[!UICONTROL Selected Payment Methods]**, sélectionnez les méthodes de paiement activées et non associées à *[!DNL PayPal Express Checkout]*, *[!DNL Apple Pay]* ou *[!DNL Google Pay]*. Par exemple, sélectionnez **[!UICONTROL Check/Money Order]**.
1. Après avoir sélectionné les méthodes de paiement appropriées, créez un client et associez-le à la société créée précédemment.
1. Connectez-vous avec le compte client associé à l’entreprise et ajoutez des éléments au panier.
1. Faites attention au mini-panier, au panier et à l’étape de paiement lors du processus de passage en caisse.

<u>Résultats attendus</u> :

Les options de paiement de [!DNL PayPal] et [!DNL Braintree] ne sont pas visibles dans le mini panier et le panier.

<u>Résultats réels</u> :

Les options de paiement de [!DNL PayPal] et [!DNL Braintree] restent visibles dans le mini panier et le panier.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
