---
title: 'ACSD-51630 : de nombreux messages système ralentissent le téléchargement des pages d’administration'
description: Appliquez le correctif ACSD-51630 pour résoudre le problème de performances d’Adobe Commerce où une grande quantité de messages système ralentit le téléchargement des pages d’administration.
feature: Admin Workspace, System
role: Admin
exl-id: 8f39afea-551a-4306-994a-cb8ce5bd5b4a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-51630 : de nombreux messages système ralentissent le téléchargement des pages d’administration

Le correctif ACSD-51630 corrige le problème de performances en raison duquel un grand nombre de messages système ralentit le téléchargement des pages d’administration. Ce correctif est disponible lorsque la version 1.1.34 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51630. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 &lt; 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

De nombreux messages système ralentissent le téléchargement des pages d’administration

<u>Procédure à suivre </u> :

1. Envoyez un grand nombre de requêtes (~50 000) à DELETE `/rest/async/v1/products/ {sku}`.
1. Accédez à n’importe quelle **page d’administration**.

<u>Résultats attendus</u> :

La page se charge à un moment approprié. Seuls les messages affichés doivent être chargés.

<u>Résultats réels</u> :

Le chargement de la page prend trop de temps. Tous les messages existants sont chargés depuis la base de données.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
