---
title: 'ACSD-54989 : L’administrateur de la société ne peut pas ordonner lorsque [!UICONTROL Enable Purchase Orders] est défini sur Oui et [!UICONTROL Purchase Order] sur Non'
description: Appliquez le correctif ACSD-54989 pour résoudre le problème Adobe Commerce où l’administrateur de la société ne peut pas passer de commandes si [!UICONTROL Enable Purchase Orders] est défini sur Oui et [!UICONTROL Purchase Order] sur Non.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-54989 : L’administrateur de la société ne peut pas procéder à une commande lorsque *[!UICONTROL Enable Purchase Orders]* est défini sur *Oui* et *[!UICONTROL Purchase Order]* sur *Non*

Le correctif ACSD-54989 corrige le problème où les commandes ne peuvent pas être placées si **[!UICONTROL Enable Purchase Orders]** est défini sur *Oui* et **[!UICONTROL Purchase Order]** défini sur *Non*. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 est installé. L’ID de correctif est ACSD-54989. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les administrateurs d’entreprise ne peuvent pas passer de commande lorsque **[!UICONTROL Enable Purchase Orders]** est défini sur *Oui* et **Bon de commande** défini sur *Non*.

<u>Conditions préalables</u> :

Installez les modules [!DNL B2B].

<u>Étapes à reproduire</u> :

1. Activez l’entreprise et laissez [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *Non*.
1. Créez un produit simple au prix de 100.
1. Créez une société par l’intermédiaire de l’administrateur.
1. Définissez [!UICONTROL **Activer les commandes**] sur *Oui*.
1. Connectez-vous en tant qu’administrateur de la société sur le storefront.
1. Ajoutez le produit simple créé au panier.
1. Passez à la page de passage en caisse et cliquez sur **[!UICONTROL Place Order]** pour terminer l’achat.

<u>Résultats attendus</u> :

Vous pouvez passer une commande avec succès.

<u>Résultats réels</u> :

La page **[!UICONTROL My Account]** s’ouvre et la commande n’est pas placée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
