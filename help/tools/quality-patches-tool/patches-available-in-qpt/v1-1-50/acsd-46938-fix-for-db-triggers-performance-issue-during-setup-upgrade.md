---
title: '"ACSD-46938 : problèmes de performances avec les déclencheurs DB lors de "setup:upgrade"'
description: Appliquez le correctif ACSD-46938 pour résoudre le problème Adobe Commerce en raison duquel la commande "setup:upgrade" modifie le mode d’indexation de la planification à l’enregistrement, provoquant des ralentissements significatifs des performances.
feature: Upgrade
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-46938 : problèmes de performances avec les déclencheurs DB pendant `setup:upgrade`

Le correctif ACSD-46938 corrige le problème en raison duquel la commande `setup:upgrade` changeait le mode d’indexation de la planification à l’enregistrement, provoquant des ralentissements de performances significatifs. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 est installé. L’ID de correctif est ACSD-46938. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Dégradation des performances lors de la recréation du déclencheur DB dans `setup:upgrade`.

<u>Étapes à reproduire</u> :

1. Créez un catalogue volumineux avec de nombreux produits et catégories.
1. Connectez-vous à [!UICONTROL Admin].
1. Définissez tous les indexeurs sur le mode [!UICONTROL Update By Schedule].
1. Ouvrez n’importe quel produit.
1. Mettez-le à jour. Par exemple, affectez-lui une nouvelle catégorie.
1. Cliquez sur [!UICONTROL Save].
1. Exécutez les commandes `bin/magento setup:upgrade` et `bin/magento cron:run` en parallèle.

<u>Résultats attendus</u> :

Le temps d’exécution de la commande `bin/magento setup:upgrade` augmente considérablement lorsque la commande `bin/magento cron:run` est exécutée simultanément.

<u>Résultats réels</u> :

Le temps d’exécution de la commande n’augmente pas.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].