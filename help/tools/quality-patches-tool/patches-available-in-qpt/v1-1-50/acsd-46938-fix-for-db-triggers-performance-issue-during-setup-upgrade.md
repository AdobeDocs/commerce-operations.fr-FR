---
title: 'ACSD-46938 : problèmes de performances avec les déclencheurs de base de données pendant « setup:upgrade »'
description: Appliquez le correctif ACSD-46938 pour résoudre le problème d’Adobe Commerce où la commande « setup:upgrade » modifie le mode de l’indexeur, le faisant passer de « schedule » à « save », ce qui entraîne des ralentissements importants des performances.
feature: Upgrade
role: Admin, Developer
exl-id: a4e88329-c5bb-4666-8738-b78b86056b71
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-46938 : problèmes de performances avec les déclencheurs de base de données pendant l’`setup:upgrade`

Le correctif ACSD-46938 corrige le problème où la commande `setup:upgrade` modifie le mode de l’indexeur de « schedule » à « save », ce qui entraîne des ralentissements importants des performances. Ce correctif est disponible lorsque la version 1.1.50 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-46938. Notez que le problème a été résolu dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Dégradation des performances lors de la recréation du déclencheur de base de données dans `setup:upgrade`.

<u>Procédure à suivre </u> :

1. Créez un catalogue volumineux avec de nombreux produits et catégories.
1. Connectez-vous à l’[!UICONTROL Admin] .
1. Définissez tous les indexeurs sur le mode [!UICONTROL Update By Schedule].
1. Ouvrez n’importe quel produit.
1. Mettez-le à jour. Par exemple, attribuez-lui une nouvelle catégorie.
1. Cliquez sur [!UICONTROL Save].
1. Exécutez les commandes `bin/magento setup:upgrade` et `bin/magento cron:run` en parallèle.

<u>Résultats attendus</u> :

Le temps d&#39;exécution de la commande `bin/magento setup:upgrade` augmente de façon significative lorsque la commande `bin/magento cron:run` est exécutée simultanément.

<u>Résultats réels</u> :

Le temps d&#39;exécution de la commande n&#39;augmente pas.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
