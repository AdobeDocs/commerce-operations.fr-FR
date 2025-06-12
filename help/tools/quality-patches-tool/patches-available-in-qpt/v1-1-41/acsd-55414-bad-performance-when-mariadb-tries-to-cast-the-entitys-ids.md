---
title: 'ACSD-55414 : mauvaises performances lorsque MariaDB tente de convertir les entitys_ids'
description: Appliquez le correctif ACSD-55414 pour résoudre le problème d’Adobe Commerce lorsque la base de données MariaDB tente de convertir « entitys_ids » de chaîne en entier, ce qui nuit aux performances de réindexation.
feature: Attributes
role: Admin, Developer
exl-id: 76309cef-559e-4a55-a27b-7d807ef9f74e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-55414 : mauvaises performances lorsque MariaDB tente de lancer le `entitys_ids`

Le correctif ACSD-55414 corrige le problème où les performances de réindexation sont entravées lorsque MariaDB tente de convertir des `entitys_ids` de chaîne en entier. Ce correctif est disponible lorsque la version 1.1.41 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-55414. Notez que le problème a été résolu dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les performances de la réindexation sont affectées lorsque la base de données MariaDB tente de convertir une `entitys_ids` de chaîne en entier.

<u>Procédure à suivre </u> :

1. Mettez à jour les `setup/performance-toolkit/profiles/ce/small.xml` en configurant *50000* produits simples.
1. Générez ce profil en exécutant la commande : `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Exécuter la réindexation : `bin/magento indexer:reindex catalog_product_attribute`.

<u>Résultats attendus</u> :

La réindexation prend un temps raisonnable pour se terminer.

<u>Résultats réels</u> :

La réindexation prend trop de temps.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
