---
title: 'ACSD-54966 : correctif pour la réutilisation des codes coupon après des ordres ayant échoué'
description: Appliquez le correctif ACSD-54966 pour résoudre le problème Adobe Commerce empêchant la réutilisation des codes coupon limités par promotions et panier suite à une commande précédemment en échec.
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
exl-id: e08062e5-62ff-4da6-918f-896af36edccc
source-git-commit: f109d3544912ee09b25d882333840cf81d2f08e3
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-54966 : correctif pour la réutilisation des codes coupon après des ordres ayant échoué

Le correctif ACSD-54966 corrige le problème en empêchant la réutilisation des codes coupon limités par client suite à une commande précédemment en échec. Ce correctif est disponible lorsque la version 1.1.42 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54966. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1
* Adobe Commerce 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p10, 2.4.6 - 2.4.6-p8
* Adobe Commerce : 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un code coupon, limité à un usage unique par client, ne peut pas être réutilisé suite à l&#39;échec d&#39;une commande précédente.

<u>Procédure à suivre </u> :

1. Configurez une règle de prix de panier avec *[!UICONTROL Uses per Customer]* = *1*.
1. Effectuez un achat à l’aide du code de coupon affecté.
1. Annulez la commande à partir du panneau d’administration ou exécutez la commande en cas d’échec de paiement.
1. Exécutez la commande : `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. Essayez de passer une commande ultérieure en utilisant le même code de coupon pour le même client.

<u>Résultats attendus</u> :

Après avoir annulé la commande ou rencontré un échec de paiement, le client peut réutiliser le code de coupon pour un nouvel achat.

<u>Résultats réels</u> :

Le client ne peut pas réutiliser le code de coupon.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
