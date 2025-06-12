---
title: 'ACSD-47054 : prévisualisation du contenu lente car toutes les banques se réindexent'
description: Appliquez le correctif ACSD-47054 pour résoudre le problème d’Adobe Commerce en raison duquel le chargement de la page d’aperçu est lent en raison de la réindexation de tous les magasins.
feature: Page Content
role: Admin, Developer
exl-id: bfbda95a-354b-4b67-8081-84aefbbd7cb4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-47054 : prévisualisation du contenu lente car toutes les banques se réindexent

Le correctif ACSD-47054 corrige le problème où le chargement d’un aperçu de l’évaluation du contenu prend plus de temps lorsqu’il y a de nombreux magasins. Ce correctif est disponible lorsque la version 1.1.37 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47054. Notez que le problème a été résolu dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) : 2.4.2-p2, 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) : 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le chargement de la page d’aperçu prend beaucoup de temps en raison d’une réindexation de tous les magasins.

<u>Procédure à suivre </u> :

1. Accédez à Commerce Admin.
1. Créez toute mise à jour planifiée.
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Dashboard]**.
1. Prévisualisez la mise à jour planifiée.
1. Ouvrez n’importe quelle catégorie.

<u>Résultats attendus</u> :

La page d’aperçu se charge dans un délai acceptable.

<u>Résultats réels</u> :

L’aperçu de l’évaluation du contenu prend beaucoup de temps.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
