---
title: 'ACSD-61756 : dégradation des performances des filtres « AdvancedSalesRule » en raison d’index de base de données manquants'
description: Appliquez le correctif ACSD-61756 pour résoudre le problème d’Adobe Commerce où la requête « magento_salesrule_filter » effectue une analyse complète des tables sans utiliser d’index, ce qui entraîne une dégradation des performances lors de la gestion de grands volumes d’enregistrements. Ce correctif améliore les performances en ajoutant les index de base de données manquants pour les filtres « AdvancedSalesRule ».
feature: Price Rules, Price Indexer
role: Admin, Developer
exl-id: 418c7c40-83ee-4cd9-8ebb-b356886ffb58
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-61756 : dégradation des performances des filtres `AdvancedSalesRule` en raison d’index de base de données manquants

Appliquez le correctif ACSD-61756 pour améliorer les performances des filtres `AdvancedSalesRule` en ajoutant les index de base de données manquants. Cela corrige le problème où la requête `magento_salesrule_filter` effectue une analyse complète de la table sans utiliser les index, ce qui entraîne une dégradation des performances lorsqu’il y a de nombreux enregistrements dans la table. Ce correctif est disponible lorsque la version 1.1.54 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-61756. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p9

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête `magento_salesrule_filter` effectue une analyse complète de la table sans utiliser d’index, ce qui entraîne une dégradation des performances des filtres `AdvancedSalesRule` lorsque la table contient de nombreux enregistrements.

<u>Procédure à suivre </u> :

1. Effectuez un passage en caisse avec plusieurs règles de vente actives.

<u>Résultats attendus</u> :

Amélioration des performances des règles de vente.

<u>Résultats réels</u> :

La requête effectue une analyse complète de la table et ne parvient pas à utiliser les index, ce qui entraîne une dégradation des performances lorsqu’il y a de nombreux enregistrements dans la table.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
