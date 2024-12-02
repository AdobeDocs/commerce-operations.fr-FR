---
title: 'ACSD-47106 : nouvel attribut personnalisé sur la page de création de l’entreprise non enregistré'
description: Appliquez le correctif ACSD-47106 pour résoudre le problème Adobe Commerce en raison duquel une valeur ne peut pas être enregistrée dans un nouvel attribut personnalisé sur la page de création d’une entreprise.
feature: Attributes, B2B, Companies
role: Developer
exl-id: 5835760d-fca1-44ba-aa5e-8797258c7c75
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47106 : nouvel attribut personnalisé sur la page de création de l’entreprise non enregistré

Le correctif ACSD-47106 corrige le problème lorsqu’une valeur ne peut pas être enregistrée dans un nouvel attribut personnalisé sur la page de création d’une entreprise. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.22 est installé. L’ID de correctif est ACSD-47106. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une valeur ne peut pas être enregistrée dans un nouvel attribut personnalisé sur la page de création d’une entreprise.

<u>Conditions préalables</u> :

* Les modules B2B sont installés.

<u>Étapes à reproduire</u> :

1. Accédez à l’administrateur Commerce > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Customer]** > **[!UICONTROL Add New Attribute]**.
1. Créez un attribut : _Test 01_.
1. Accédez à l’Admin Commerce > **[!UICONTROL Customers]** > **[!UICONTROL Companies]** > et créez une nouvelle société avec tous les détails requis.
1. Essayez d&#39;ajouter une valeur à l&#39;attribut personnalisé _Test 01_.
1. Essayez de mettre à jour la valeur de l&#39;attribut personnalisé _Test 01_.

<u>Résultats attendus</u> :

Les modifications sont enregistrées.

<u>Résultats réels</u> :

Les modifications ne sont pas enregistrées.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
