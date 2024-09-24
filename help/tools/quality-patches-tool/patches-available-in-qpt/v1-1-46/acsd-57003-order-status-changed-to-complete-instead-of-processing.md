---
title: 'ACSD-57003 : l’état de la commande passe à *Terminé* au lieu de passer à *Traitement*'
description: Appliquez le correctif ACSD-57003 pour résoudre le problème Adobe Commerce en raison duquel l’état de la commande passe à *Terminé* au lieu de passer à *Traitement*.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-57003 : l’état de la commande passe à *Complete* au lieu de passer à *Processing*

Le correctif ACSD-57003 corrige le problème où l’état de la commande passe à *Complete* au lieu de passer à *Processing*. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.46 est installé. L’ID de correctif est ACSD-57003. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’état de la commande passe à *Complete* au lieu de se changer en *Traitement* lorsqu’une commande est partiellement remboursée et expédiée.

<u>Étapes à reproduire</u> :

1. Créez une commande avec deux produits configurables.
1. Facturez tous les éléments.
1. N&#39;expédiez que le premier article.
1. Rétablissement/création d’une note de crédit uniquement pour l’élément expédié (*premier élément*).
1. Vérifiez l’état de la commande.

<u>Résultats attendus</u> :

L’état de la commande doit être à l’état _Processing_.

<u>Résultats réels</u> :

L’état de la commande passe à *Complete* après la création d’une note de crédit pour l’article partiellement expédié.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
