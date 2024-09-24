---
title: "MDVA-38799 : produits téléchargeables non enregistrés après la création d’une mise à jour intermédiaire"
description: Le correctif MDVA-38799 résout le problème en raison duquel les produits téléchargeables ne sont pas enregistrés après la création d’une mise à jour intermédiaire. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0 est installé. L’ID de correctif est MDVA-38799. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.
feature: Products, Staging
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-38799 : produits téléchargeables non enregistrés après la création d’une mise à jour intermédiaire

Le correctif MDVA-38799 résout le problème en raison duquel les produits téléchargeables ne sont pas enregistrés après la création d’une mise à jour intermédiaire. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0 est installé. L’ID de correctif est MDVA-38799. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0-2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits téléchargeables ne sont pas enregistrés après la création d’une mise à jour intermédiaire. Les utilisateurs reçoivent le message d’erreur : *L’exemple téléchargeable n’est pas lié au produit. Vérifiez le lien et réessayez*.

<u>Étapes à reproduire</u> :

1. Accédez à **Catalogue** > **Produits**.
1. Cliquez sur la liste déroulante en regard de Ajouter un produit et sélectionnez Produit téléchargeable.
   * Renseignez le nom, le SKU, le prix et la quantité du produit.
1. Faites défiler jusqu’à la page d’informations téléchargeables.
1. Sous Exemples, cliquez sur **Ajouter un lien**.
   * Remplissez le titre, Télécharger le fichier (le type de fichier n’a pas d’importance).
1. Cliquez sur **Enregistrer**. Vous obtiendrez le message suivant : *Vous avez enregistré le produit*.
1. Cliquez sur **Planifier une nouvelle mise à jour** en haut de la page.
   * Remplissez le Nom de mise à jour et indiquez une Date de début et une Date de fin légales.
1. Cliquez sur **Enregistrer** lors de la mise à jour intermédiaire.
1. Cliquez sur **Enregistrer** sur le produit.

<u>Résultats attendus</u> :

Le produit est enregistré sans erreur.

<u>Résultats réels</u> :

Vous recevez le message d’erreur : *L’exemple téléchargeable n’est pas lié au produit. Vérifiez le lien et réessayez*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
