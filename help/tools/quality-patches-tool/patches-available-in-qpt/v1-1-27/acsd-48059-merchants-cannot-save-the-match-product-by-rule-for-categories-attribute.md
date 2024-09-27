---
title: 'ACSD-48059 : les marchands ne peuvent pas enregistrer [!UICONTROL Match product by rule] pour l’attribut Categories.'
description: Appliquez le correctif ACSD-48059 pour résoudre le problème Adobe Commerce en raison duquel les commerçants ne peuvent pas enregistrer le [!UICONTROL Match product by rule] pour l’attribut Categories .
feature: Admin Workspace, Attributes, Categories, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-48059 : Les vendeurs ne peuvent pas enregistrer le *[!UICONTROL Match product by rule]* pour l’attribut categories

Le correctif ACSD-48059 corrige le problème où les marchands ne peuvent pas enregistrer le *[!UICONTROL Match product by rule]* pour l’attribut categories dans [!DNL Visual Merchandiser]. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 est installé. L’ID de correctif est ACSD-48059. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) >=2.3.7 &lt;2.4.7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les commerçants ne peuvent pas enregistrer l’attribut *[!UICONTROL Match product by rule]* pour les catégories dans [!DNL Visual Merchandiser].

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Visual Merchandiser]** > **[!UICONTROL Visible Attributes for Category Rules]**, ajoutez des catégories.
1. Accédez à l’administrateur Adobe Commerce > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
   * Accédez à la section [!UICONTROL Products in Category] .
   * Ajoutez une nouvelle condition *[!UICONTROL Match products by rule]* avec l’attribut categories.

<u>Résultats attendus</u> :

La catégorie est enregistrée avec succès.

<u>Résultats réels</u> :

* Vous ne pouvez pas enregistrer la catégorie avec la nouvelle règle et la nouvelle condition.
* *Un problème s’est produit lors de l’enregistrement de l’erreur category* s’affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
