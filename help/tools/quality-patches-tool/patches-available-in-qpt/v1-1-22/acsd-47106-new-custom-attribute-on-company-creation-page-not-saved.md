---
title: 'ACSD-47106 : nouvel attribut personnalisé sur la page de création d’entreprise non enregistré'
description: Appliquez le correctif ACSD-47106 pour résoudre le problème d’Adobe Commerce où une valeur ne peut pas être enregistrée dans un nouvel attribut personnalisé sur une page de création de société.
feature: Attributes, B2B, Companies
role: Developer
exl-id: 5835760d-fca1-44ba-aa5e-8797258c7c75
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47106 : nouvel attribut personnalisé sur la page de création d’entreprise non enregistré

Le correctif ACSD-47106 corrige le problème où une valeur ne peut pas être enregistrée dans un nouvel attribut personnalisé sur une page de création d’entreprise. Ce correctif est disponible lorsque la version 1.1.22 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47106. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une valeur ne peut pas être enregistrée dans un nouvel attribut personnalisé sur une page de création d’entreprise.

<u>Conditions préalables</u> :

* Les modules B2B sont installés.

<u>Procédure à suivre </u> :

1. Accédez à Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Customer]** > **[!UICONTROL Add New Attribute]**.
1. Créez un attribut : _Test 01_.
1. Accédez à Commerce Admin > **[!UICONTROL Customers]** > **[!UICONTROL Companies]** > et créez une société avec tous les détails requis.
1. Essayez d&#39;ajouter une valeur à l&#39;attribut personnalisé _Test 01_.
1. Essayez de mettre à jour la valeur de l’attribut personnalisé _Test 01_.

<u>Résultats attendus</u> :

Les modifications sont enregistrées.

<u>Résultats réels</u> :

Les modifications ne sont pas enregistrées.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
