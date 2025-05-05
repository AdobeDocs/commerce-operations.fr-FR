---
title: "ACSD-50512 : erreur lors de la mise à jour de la date de début d’une mise à jour d’évaluation de produit téléchargeable"
description: Appliquez le correctif ACSD-51892 pour résoudre le problème de performances d’Adobe Commerce en raison duquel l’erreur *Le lien téléchargeable n’est pas lié au produit. Vérifiez le lien et réessayez*, survenant lors de la mise à jour de la date de début d’une mise à jour intermédiaire du produit téléchargeable.
feature: Products, Staging
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-50512 : Erreur lors de la mise à jour de la date de début pour la mise à jour de l’évaluation téléchargeable du produit

Le correctif ACSD-50512 corrige le problème où l’erreur *Le lien téléchargeable n’est pas lié au produit. Vérifiez le lien et réessayez*, survient lors de la mise à jour de la date de début d’une mise à jour d’évaluation de produit téléchargeable. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.33 est installé. L’ID de correctif est ACSD-51502. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L&#39;erreur *Le lien téléchargeable n&#39;est pas lié au produit. Vérifiez le lien et réessayez*, survient lors de la mise à jour de la date de début d’une mise à jour d’évaluation de produit téléchargeable.

<u>Étapes à reproduire</u> :

1. Créez un produit téléchargeable, avec les *liens téléchargeables* et les *exemples de liens*.
1. Créez une mise à jour planifiée pour le même produit et enregistrez-le.
1. Editez la mise à jour planifiée préconfigurée (à partir de l&#39;étape 2) et modifiez la date de début.
1. Enregistrez la mise à jour planifiée.

<u>Résultats attendus</u> :

Les modifications apportées à la mise à jour planifiée sont enregistrées avec succès.

<u>Résultats réels</u> :

Vous obtenez l’erreur : *Le lien téléchargeable n’est pas lié au produit. Vérifiez le lien et réessayez*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
