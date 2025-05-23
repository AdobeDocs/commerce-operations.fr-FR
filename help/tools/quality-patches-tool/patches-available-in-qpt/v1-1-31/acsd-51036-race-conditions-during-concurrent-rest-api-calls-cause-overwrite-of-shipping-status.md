---
title: 'ACSD-51036 : Les conditions de course lors d’appels API REST simultanés entraînent le remplacement de l’état d’expédition.'
description: Appliquez le correctif ACSD-51036 pour résoudre le problème Adobe Commerce en raison duquel des conditions de concurrence se produisent lors d’appels d’API REST simultanés, ce qui entraîne un remplacement du statut de livraison dans le tableau des articles commandés.
feature: REST, Orders, Shipping/Delivery
role: Admin
exl-id: 6150d072-05fe-4010-b31b-8ccde9cab656
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51036 : Les conditions de concurrence lors d’appels API REST simultanés entraînent le remplacement du statut de livraison dans le tableau des éléments triés.

Le correctif ACSD-51036 corrige le problème en raison duquel les conditions de concurrence lors d’appels d’API REST simultanés entraînent le remplacement du statut de livraison dans le tableau des articles commandés. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.31 est installé. L’ID de correctif est ACSD-51036. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les conditions de concurrence lors d’appels d’API REST simultanés entraînent le remplacement du statut de livraison dans le tableau des articles commandés.

<u>Étapes à reproduire</u> :

1. Créez une commande avec deux éléments.
1. Facturation Article A.
1. Envoyez simultanément une demande de remboursement pour l’article A via l’API REST pendant que vous envoyez une demande d’expédition pour l’article B.
1. Accédez à la commande dans **[!UICONTROL Admin Panel]**.

<u>Résultats attendus</u>

L’état *[!UICONTROL Shipped 1]* doit être présent pour l’élément B dans la table *[!UICONTROL Items]* classée.

<u>Résultats réels</u>

L’état *[!UICONTROL Shipped 1]* n’est pas présent pour l’élément B dans la table *[!UICONTROL Items]* classée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
