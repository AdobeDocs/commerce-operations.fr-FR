---
title: "ACSD-54966 : correctif pour la réutilisation des codes de bons après les commandes en échec"
description: Appliquez le correctif ACSD-54966 pour résoudre le problème Adobe Commerce empêchant la réutilisation des codes de bons limités par promotion et par panier suite à une commande précédemment en échec.
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-54966 : correctif pour la réutilisation des codes de coupon après les commandes en échec

Le correctif ACSD-54966 corrige le problème empêchant la réutilisation des codes de bons limités par client suite à une commande précédemment en échec. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 est installé. L’ID de correctif est ACSD-54966. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un code de bon, limité à un usage unique par client, ne peut pas être réutilisé suite à une commande précédente en échec.

<u>Étapes à reproduire</u> :

1. Configurez une règle de prix de panier avec *[!UICONTROL Uses per Customer]* = *1*.
1. Continuez pour effectuer un achat à l’aide du code de bon attribué.
1. Annulez la commande à partir du panneau d’administration ou exécutez la commande en cas d’échec de paiement.
1. Exécutez la commande : `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. Essayez de passer une commande ultérieure en utilisant le même code de bon pour le même client.

<u>Résultats attendus</u> :

Après l’annulation de la commande ou l’échec de paiement, le client peut réutiliser le code de bon pour un nouvel achat.

<u>Résultats réels</u> :

Le client ne peut pas réutiliser le code de coupon.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
