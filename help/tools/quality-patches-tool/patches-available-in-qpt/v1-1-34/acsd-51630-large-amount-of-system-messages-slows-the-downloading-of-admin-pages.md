---
title: 'ACSD-51630 : de nombreux messages système ralentissent le téléchargement des pages d’administration'
description: Appliquez le correctif ACSD-51630 pour résoudre le problème de performances d’Adobe Commerce en raison duquel une grande quantité de messages système ralentit le téléchargement des pages d’administration.
feature: Admin Workspace, System
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-51630 : téléchargement lent de nombreux messages système des pages d’administration

Le correctif ACSD-51630 corrige le problème de performances où un grand nombre de messages système ralentissent le téléchargement des pages d’administration. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.34 est installé. L’ID de correctif est ACSD-51630. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 &lt; 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

De nombreux messages système ralentissent le téléchargement des pages d’administration

<u>Étapes à reproduire</u> :

1. Effectuez un grand nombre de requêtes (~50k) au DELETE `/rest/async/v1/products/ {sku}`.
1. Accédez à n’importe quelle **page d’administration**.

<u>Résultats attendus</u> :

La page se charge au bon moment. Seuls les messages affichés doivent être chargés.

<u>Résultats réels</u> :

Le chargement de la page prend trop de temps. Tous les messages existants sont chargés depuis la base de données.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].