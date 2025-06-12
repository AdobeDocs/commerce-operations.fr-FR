---
title: 'Les erreurs ACSD-49628: [!DNL Page Builder] CORS empêchent l’enregistrement du produit.'
description: Appliquez le correctif ACSD-49628 pour résoudre le problème d’Adobe Commerce où les erreurs  [!DNL Page Builder] CORS empêchent l’enregistrement du produit.
feature: Categories, Page Builder, Products
role: Admin
exl-id: 5bceddfa-5fbf-4ebe-a233-de7720764849
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-49628 : [!DNL Page Builder] erreurs CORS empêchent l’enregistrement du produit

Le correctif ACSD-49628 corrige le problème où [!DNL Page Builder] erreurs CORS empêchent un administrateur d’enregistrer un produit. Ce correctif est disponible lorsque la version 1.1.32 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-49628. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!DNL Page Builder] erreurs CORS empêchent l’enregistrement d’un produit.

<u>Procédure à suivre </u> :

1. Connectez-vous en tant qu’administrateur
1. Créez un rôle d’utilisateur avec les autorisations suivantes :

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**.
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**.

1. N’ajoutez aucune autorisation *[!UICONTROL Content]*.
1. Créez un autre utilisateur administrateur et attribuez-lui les rôles créés ci-dessus.
1. Créer un produit et se déconnecter.
1. Connectez-vous en tant que second administrateur.
1. Essayez de modifier et d’enregistrer le produit.

<u>Résultats attendus</u> :

Le second administrateur peut enregistrer le produit, mais le bouton **[!UICONTROL Edit with Page Builder]** ne s’affiche pas pour l’administrateur sans autorisations *[!UICONTROL Content]*.

<u>Résultats réels</u> :

Le second administrateur ne peut pas enregistrer le produit en raison de plusieurs erreurs de [!DNL Page Builder].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
