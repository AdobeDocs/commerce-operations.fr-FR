---
title: "ACSD-60590 : amélioration des performances de la génération de rapports quotidiens agrégés des Bestsellers"
description: Appliquez le correctif ACSD-60590 pour résoudre le problème Adobe Commerce en raison duquel le rapport quotidien agrégé des Bestsellers prend un temps important pour générer un grand volume de commandes passées.
feature: Reporting
role: Admin, Developer
source-git-commit: 4fe3f205754c040b60b6b7f01c7109cb31f70af8
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-60590 : amélioration des performances de la génération de rapports quotidiens agrégés des Bestsellers

Le correctif ACSD-60590 corrige le problème en raison duquel le rapport quotidien agrégé des Bestsellers prend un temps important pour générer un grand volume de commandes passées. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.52 est installé. L’ID de correctif est ACSD-60590. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le rapport quotidien agrégé des Bestsellers prend beaucoup de temps pour générer un grand volume de commandes passées.

<u>Conditions préalables</u>

Un grand nombre de commandes (par exemple : *500k*).

<u>Étapes à reproduire</u> :

1. Exécutez la commande suivante :

   `update sales_order set created_at = DATE(DATE_SUB(NOW(), INTERVAL ROUND(RAND()*3650) DAY))  ;`

1. Exécutez la tâche `aggregate_sales_report_bestsellers_data`.

<u>Résultats attendus</u> :

La tâche se termine en moins de 30 secondes.

<u>Résultats réels</u> :

La requête prend environ 10 minutes pour chaque magasin pour les dates `created_at`.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
