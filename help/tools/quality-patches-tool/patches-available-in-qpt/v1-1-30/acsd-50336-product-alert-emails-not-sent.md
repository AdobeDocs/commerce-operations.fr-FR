---
title: "ACSD-50336 : emails d’alerte de produit non envoyés"
description: Appliquez le correctif ACSD-50336 pour résoudre le problème Adobe Commerce en raison duquel les emails d’alerte de produit ne sont pas envoyés lorsqu’un produit est de nouveau en stock ou que le prix est modifié.
feature: Communications, Personalization, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-50336 : emails d’alerte de produit non envoyés

Le correctif ACSD-50336 corrige le problème en raison duquel les emails d’alerte de produit ne sont pas envoyés lorsqu’un produit est à nouveau en stock ou que le prix est modifié. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 est installé. L’ID de correctif est ACSD-50336. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1 - 2.4.4-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les emails d’alerte de produit ne sont pas envoyés lorsqu’un produit est de nouveau en stock ou que le prix est modifié.

<u>Conditions préalables</u> :

Configurez des alertes de produit pour le moment où un produit est de nouveau ajouté en stock.

<u>Étapes à reproduire</u> :

1. Connectez-vous en tant que client sur le storefront.
1. Ouvrez un produit qui n’est pas en stock.
1. Abonnez-vous pour recevoir une notification lorsque le produit est *de retour en stock*.
1. Mettez à jour le produit de [!UICONTROL Admin] pour qu’il soit _de retour en stock_.

<u>Résultats attendus</u> :

Une notification par e-mail sur le fait que le produit est *de retour en stock* est envoyée au client.

<u>Résultats réels</u> :

Le client ne reçoit pas de notification par e-mail sur le fait que le produit est *de retour en stock*. L’erreur suivante s’affiche dans le journal :

```
report. CRITICAL: Magento\ProductAlert\Model\Mailing\ErrorEmailSender::execute(): Argument #2 ($storeId) must be of type int, string given, called in vendor/magento/module-product-alert/Model/Mailing/AlertProcessor.php on line 130 [] [] 
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
