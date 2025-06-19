---
title: 'ACSD-49835 : [!UICONTROL Use Default Value] case à cocher n’est pas enregistrée'
description: Appliquez le correctif ACSD-49835 pour résoudre le problème d’Adobe Commerce où la case à cocher [!UICONTROL Use Default Value] n’est pas correctement enregistrée au niveau du magasin pour un attribut à sélection multiple.
feature: Storefront
role: Admin
exl-id: e8d5a95f-b17d-49fc-a6d3-e03554667438
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# ACSD-49835 : [!UICONTROL Use Default Value] case à cocher n’est pas enregistrée

Le correctif ACSD-49835 corrige le problème où la case à cocher [!UICONTROL Use Default Value] n’est pas enregistrée correctement au niveau du magasin pour un attribut à sélection multiple. Ce correctif est disponible lorsque la version 1.1.29 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-49835. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La case à cocher [!UICONTROL Use Default Value] n’est pas enregistrée correctement au niveau du magasin pour un attribut à sélection multiple.

<u>Procédure à suivre </u> :

1. Créez un **[!UICONTROL Multiple-select Attribute]** dans **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** et ajoutez-le à un jeu d’attributs.
1. Accédez à un **[!UICONTROL Product]** et enregistrez-**[!UICONTROL Values]** dans **[!UICONTROL All Store Views (Default Scope)]**.
1. Accédez à un **[!UICONTROL Store View Scope]** spécifique et enregistrez le produit.
1. Accédez à **[!UICONTROL Store View Scope]** et cochez la case **[!UICONTROL Use Default Value]** .

<u>Résultats attendus</u> :

Les valeurs d’attribut à sélection multiple sont correctement enregistrées lorsque vous cochez la case [!UICONTROL Use Default Value] dans la [!UICONTROL Store View Scope].

<u>Résultats réels</u> :

Les valeurs d’attribut à sélection multiple ne sont pas correctement enregistrées lorsque vous cochez la case [!UICONTROL Use Default Value] dans le [!UICONTROL Store View Scope].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
