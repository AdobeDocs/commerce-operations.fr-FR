---
title: 'MDVA-38799 : produits téléchargeables non enregistrés après la création d’une mise à jour d’évaluation'
description: Le correctif MDVA-38799 résout le problème où les produits téléchargeables ne sont pas enregistrés après la création d’une mise à jour d’évaluation. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 est installé. L’ID du correctif est MDVA-38799. Notez que le problème a été corrigé dans la version 2.4.3 d’Adobe Commerce.
feature: Products, Staging
role: Admin
exl-id: 0ae665a8-cda2-4340-91e7-5b9b969a6607
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-38799 : produits téléchargeables non enregistrés après la création d’une mise à jour d’évaluation

Le correctif MDVA-38799 résout le problème où les produits téléchargeables ne sont pas enregistrés après la création d’une mise à jour d’évaluation. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 est installé. L’ID du correctif est MDVA-38799. Notez que le problème a été corrigé dans la version 2.4.3 d’Adobe Commerce.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur les infrastructures cloud 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0-2.4.2-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits téléchargeables ne sont pas enregistrés après la création d’une mise à jour d’évaluation. Les utilisateurs reçoivent le message d’erreur suivant : *L’exemple téléchargeable n’est pas lié au produit. Vérifiez le lien et réessayez*.

<u>Procédure à suivre </u> :

1. Accédez à **Catalogue** > **Produits**.
1. Cliquez sur la liste déroulante en regard de Ajouter un produit et sélectionnez Produit téléchargeable .
   * Renseignez le nom, le SKU, le prix et la quantité du produit.
1. Faites défiler l’écran jusqu’à la page Informations téléchargeables .
1. Sous Exemples, cliquez sur **Ajouter un lien**.
   * Renseignez le champ Titre , Charger le fichier (le type de fichier n’a pas d’importance).
1. Cliquez sur **Enregistrer**. Le message suivant s’affiche : *Vous avez enregistré le produit*.
1. Cliquez sur **Planifier une nouvelle mise à jour** en haut de la page.
   * Remplissez le Nom de la mise à jour ainsi qu’une Date de début et une Date de fin légales.
1. Cliquez sur **Enregistrer** lors de la mise à jour de l’évaluation.
1. Cliquez sur **Enregistrer** sur le produit.

<u>Résultats attendus</u> :

Le produit est enregistré sans erreur.

<u>Résultats réels</u> :

Le message d’erreur suivant s’affiche : *L’exemple téléchargeable n’est pas lié au produit. Vérifiez le lien et réessayez*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
