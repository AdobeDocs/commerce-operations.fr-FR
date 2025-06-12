---
title: 'ACSD-48813 : la recherche n’affiche pas les résultats pertinents en fonction du poids de recherche des attributs'
description: Appliquez le correctif ACSD-48813 pour résoudre le problème d’Adobe Commerce où la recherche n’affiche pas les résultats pertinents en fonction du poids de recherche des attributs.
feature: Admin Workspace, Attributes, Search
role: Admin
exl-id: 98ef7eb1-c13e-4c56-9a25-8e61cfb5fade
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-48813 : la recherche n’affiche pas les résultats pertinents en fonction du poids de recherche des attributs

Le correctif ACSD-48813 corrige le problème où la recherche n’affiche pas de résultats pertinents en fonction du poids de recherche des attributs. Ce correctif est disponible lorsque la version 1.1.29 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48813. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La recherche n’affiche pas de résultats pertinents en fonction du poids de recherche des attributs.

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce avec des exemples de données.
1. Définissez le moteur de recherche sur [!DNL Elasticsearch].
1. Connectez-vous en tant qu’administrateur
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Products]**.
1. Ouvrez l’attribut *name*.
1. Ouvrez l’onglet *[!UICONTROL Properties]* du storefront.
1. Sélectionnez [!UICONTROL Search Weight] = *10* dans la valeur de la liste déroulante.
1. Cliquez sur **[!UICONTROL Save Attribute]**.
1. Ouvrez maintenant le storefront et recherchez le mot *Back*.

<u>Résultats attendus</u> :

Les produits de sac à dos sont renvoyés en haut des résultats de recherche.

<u>Résultats réels</u> :

Les produits de sac à dos sont retournés au milieu des résultats de recherche.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
