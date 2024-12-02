---
title: 'ACSD-53176 : La règle de produit avec "est l’une des conditions" ne correspond pas'
description: Appliquez le correctif ACSD-53176 pour résoudre le problème Adobe Commerce où la règle de produit associée "est l’une des conditions" ne fonctionne pas correctement pour "Produits à faire correspondre".
feature: Marketing Tools
role: Admin
exl-id: 8260c6ac-3ca2-4361-9e36-a8a58468fa95
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-53176 : La règle de produit avec la condition `is one of` ne correspond pas

Le correctif ACSD-53176 corrige le problème en raison duquel la condition `is one of` de la règle de produit associée ne fonctionne pas correctement pour **Produits à faire correspondre**. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.36 est installé. L’ID de correctif est ACSD-53176. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La condition `is one of` de la règle de produit associée ne fonctionne pas correctement pour **Produits à faire correspondre**.

<u>Étapes à reproduire</u> :

1. Créez 3 à 4 produits.
1. Créez une règle de produit associée.

   Définissez la règle pour qu’elle corresponde à deux produits ou plus :
   * `SKU is one of "S1,S2".`

   Définissez la règle pour afficher deux éléments ou plus :
   * `Product SKU is one of constant value "S2,S3".`

1. Ouvrez le produit S1 sur Storefront.

<u>Résultats attendus</u> :

Les produits associés &quot;S2&quot; et &quot;S3&quot; s’affichent sur les deux pages de produits &quot;S1&quot; et &quot;S2&quot;.

<u>Résultats réels</u> :

Les produits associés ne s’affichent pas sur les pages produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
