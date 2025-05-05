---
title: 'ACSD-56979 : suppression des images de produit après la mise à jour intermédiaire supprimée'
description: Appliquez le correctif ACSD-56979 pour résoudre le problème Adobe Commerce en raison duquel les images de produit sont supprimées après la suppression d’une mise à jour intermédiaire.
feature: Products
role: Admin, Developer
exl-id: 1e0fbd5c-285b-408e-ba52-72619e29167b
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-56979 : suppression des images de produit après la mise à jour intermédiaire supprimée

Le correctif ACSD-56979 corrige le problème de suppression des images de produits après suppression d’une mise à jour intermédiaire. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49 est installé. L’ID de correctif est ACSD-56979. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec Adobe Commerce et les versions de Magento Open Source :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les images de produit sont supprimées après la suppression d’une mise à jour intermédiaire.

<u>Étapes à reproduire</u> :

1. Dans la barre latérale d’administration de Commerce, accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et créez un produit.
1. Sous **[!UICONTROL Images and Videos]**, téléchargez une image et enregistrez le produit.
1. Dans la zone **[!UICONTROL Scheduled Changes]**, sélectionnez **[!UICONTROL Schedule New Update]**.
   1. Choisissez une date de début quelques minutes à l’avenir.
   1. Ne choisissez pas de date de fin.
1. Dans la zone **[!UICONTROL Scheduled Changes]**, sélectionnez le lien **[!UICONTROL View/Edit]**.
1. Accédez à **[!UICONTROL Remove from Update]** > **[!UICONTROL Delete the Update]** et sélectionnez **[!UICONTROL Done]**.
1. Actualisez la page.

<u>Résultats attendus</u> :

Comme la mise à jour est supprimée avant la date de début planifiée, le produit doit rester le même.

<u>Résultats réels</u> :

Le contenu de l’image est perdu et n’affiche aucun octet.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
