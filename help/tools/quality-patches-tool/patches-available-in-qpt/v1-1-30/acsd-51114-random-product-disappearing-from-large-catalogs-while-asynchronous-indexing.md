---
title: 'ACSD-51114 : les produits aléatoires disparaissent des catalogues volumineux lorsque l’indexation asynchrone est activée'
description: Appliquez le correctif ACSD-51114 pour résoudre le problème d’Adobe Commerce Les produits aléatoires ont disparu des catalogues volumineux lorsque l’indexation asynchrone est activée.
feature: Catalog Management, Categories, Products
role: Admin
exl-id: ab1816ef-fb09-46e7-8102-32865f806874
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51114 : les produits aléatoires disparaissent des catalogues volumineux lorsque l’indexation asynchrone est activée

>[!NOTE]
>
>Ce correctif est obsolète.

Le correctif ACSD-51114 corrige le problème Les produits aléatoires ont disparu des catalogues volumineux lorsque l’indexation asynchrone est activée. Ce correctif est disponible lorsque la version 1.1.30 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51114. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]:Search for patches]. Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits aléatoires disparaissaient des catalogues volumineux lorsque l’indexation asynchrone était activée.

<u>Procédure à suivre </u> :

1. Créez un ensemble de 10 produits.
1. Définissez tous les indexeurs sur le mode **[!UICONTROL Update on Save]**.
1. Créez une catégorie et affectez-lui tous les produits.
1. Désactivez tous les produits.
1. Ouvrez la catégorie et vérifiez qu’elle ne contient aucun produit.
1. Définissez tous les indexeurs sur le mode **[!UICONTROL Update on Schedule]**.
1. Définissez la `DEFAULT_BATCH_SIZE` sur 2 dans `lib/internal/Magento/Framework/Mview/View.php#L31`.
1. Activez les produits dans l&#39;ordre suivant : 1er, 9ème, 2ème, 5ème, 10ème, 3ème.
1. Exécutez la commande cron .
1. Ouvrez à nouveau la catégorie.

<u>Résultats attendus</u> :

Tous les produits activés s’affichent.

<u>Résultats réels</u> :

Tous les produits activés ne s’affichent pas.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
