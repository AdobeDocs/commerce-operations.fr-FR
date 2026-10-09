---
title: 'ACSD-51114 : les produits aléatoires disparaissent des catalogues volumineux lorsque l’indexation asynchrone est activée'
description: Appliquez le correctif ACSD-51114 pour résoudre le problème d’Adobe Commerce Les produits aléatoires ont disparu des catalogues volumineux lorsque l’indexation asynchrone est activée.
feature: Catalog Management, Categories, Products
role: Admin
exl-id: ab1816ef-fb09-46e7-8102-32865f806874
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%
---
# ACSD-51114 : les produits aléatoires disparaissent des catalogues volumineux lorsque l’indexation asynchrone est activée

>[!NOTE]
>
>Ce correctif est obsolète.

Le correctif ACSD-51114 corrige le problème Les produits aléatoires ont disparu des catalogues volumineux lorsque l’indexation asynchrone est activée. Ce correctif est disponible lorsque la version 1.1.30 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-51114. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]:Search pour les correctifs]. Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
