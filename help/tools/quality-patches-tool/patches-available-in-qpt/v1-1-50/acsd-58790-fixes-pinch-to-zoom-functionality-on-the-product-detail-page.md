---
title: 'ACSD-58790 : corrige la fonctionnalité de pincement pour zoomer sur les images de la page des détails du produit dans la vue mobile sur [!DNL Chrome]'
description: ACSD-58790 corrige le problème Adobe Commerce en raison duquel l’image dans la vue mobile sur [!DNL Chrome] n’effectuait pas de zoom avant sur l’image comme prévu.
feature: Storefront
role: Admin, Developer
exl-id: 46b324bf-c2a0-4086-87ee-96e8c4883494
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-58790 : corrige la fonctionnalité de pincement pour zoomer sur les images de la page des détails du produit dans la vue mobile sur [!DNL Chrome]

Le correctif ACSD-58790 corrige le problème Adobe Commerce en raison duquel l’image dans la vue mobile sur [!DNL Chrome] n’effectuait pas de zoom avant sur l’image comme prévu. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 est installé. L’ID de correctif est ACSD-58790. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Correction de la fonctionnalité de pincement pour zoomer sur les images de page des détails du produit dans la vue mobile sur [!DNL Chrome].

<u>Étapes à reproduire</u> :

1. Créez un produit avec une image.
1. Ouvrez le produit à partir d’un navigateur [!DNL Chrome].
1. Cliquez sur l’image et vérifiez que l’image s’agrandit en double-cliquant dessus.
1. Basculez vers la vue mobile à l’aide des outils de développement [!DNL Chrome].
1. Cliquez sur l’image.
1. Double-appuyez.

<u>Résultats attendus</u> :

L’image est agrandie lorsque vous double-cliquez dessus.

<u>Résultats réels</u> :

L’image n’effectue pas de zoom avant lorsque vous double-cliquez dessus. Ce problème est spécifique à [!DNL Chrome] dans la vue mobile, car la fonctionnalité de zoom fonctionne comme prévu dans [!DNL Firefox].

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
