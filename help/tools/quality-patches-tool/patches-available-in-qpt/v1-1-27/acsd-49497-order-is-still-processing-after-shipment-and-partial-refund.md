---
title: "ACSD-49497 : commande toujours en traitement après l'expédition et remboursement partiel"
description: Appliquez le correctif ACSD-49497 pour corriger le problème Adobe Commerce où l’état de la commande reste en traitement après l’expédition et un remboursement partiel est appliqué.
feature: Admin Workspace, Orders, Shipping/Delivery
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-49497 : traitement des commandes en cours après expédition et remboursement partiel

Le correctif ACSD-49497 corrige le problème lorsque l’état de la commande reste en traitement après l’expédition et qu’un remboursement partiel est appliqué. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 est installé. L’ID de correctif est ACSD-49497. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’état d’une nouvelle commande reste dans l’état *[!UICONTROL Processing]* même après l’expédition et un remboursement partiel est appliqué.

<u>Étapes à reproduire</u> :

1. Créez une commande avec plusieurs éléments.
1. À partir de **[!UICONTROL Admin]**, créez une facture pour la commande.
1. À partir de **[!UICONTROL Admin]**, créez une note de crédit et remboursez un article seulement partiellement.
1. À partir de **[!UICONTROL Admin]**, demandez l’expédition des éléments restants dans la commande.
1. Observez l’état de la commande.

<u>Résultats attendus</u> :

L’état de la commande doit être *[!UICONTROL Complete]*.

<u>Résultats réels</u> :

L’état de la commande reste *[!UICONTROL Processing]*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
