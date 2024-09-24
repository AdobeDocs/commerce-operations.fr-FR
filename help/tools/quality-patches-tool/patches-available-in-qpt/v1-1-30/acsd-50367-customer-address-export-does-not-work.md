---
title: 'ACSD-50367 : L’exportation de l’adresse du client ne fonctionne pas avec un attribut à sélection multiple'
description: Appliquez le correctif ACSD-50367 pour résoudre le problème Adobe Commerce en raison duquel l’exportation de l’adresse du client ne fonctionne pas lors de la création d’un attribut **’adresse du client** à sélection multiple.
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-50367 : L’exportation des adresses client ne fonctionne pas

Le correctif ACSD-50367 corrige le problème en raison duquel l’exportation de l’adresse du client ne fonctionne pas lorsqu’un attribut **`Customer Address`** à sélection multiple sans valeurs est créé. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 est installé. L’ID de correctif est ACSD-50367. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’exportation des adresses client ne fonctionne pas lorsqu’un attribut **`Customer Address`** à sélection multiple sans valeurs est créé.

<u>Conditions préalables</u> :

Créez un client avec une adresse.

<u>Étapes à reproduire</u> :

1. Créez un attribut **`Customer Address`** à sélection multiple dans **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]**, puis sélectionnez le type d’entité **`Customer Address`**.
1. Exportez les adresses du client. Vous verrez que rien n&#39;est exporté.
1. Supprimez l’attribut **`Customer Address`** à sélection multiple et exportez à nouveau les adresses du client. Cette fois, le fichier CSV des adresses est généré.

<u>Résultats attendus</u> :

Les adresses du client peuvent être exportées en tant que fichier CSV lors de la création d’un attribut **`Customer Address`** à sélection multiple.

<u>Résultats réels</u> :

Les adresses du client ne peuvent pas être exportées en tant que fichier CSV lors de la création d’un attribut **`Customer Address`** à sélection multiple.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
