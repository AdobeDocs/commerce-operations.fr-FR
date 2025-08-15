---
title: 'ACSD-48059 : les commerçants ne peuvent pas enregistrer de [!UICONTROL Match product by rule] pour l’attribut Catégories.'
description: Appliquez le correctif ACSD-48059 pour résoudre le problème d’Adobe Commerce en raison duquel les commerçants ne peuvent pas enregistrer le [!UICONTROL Match product by rule] pour l’attribut Categories.
feature: Admin Workspace, Attributes, Categories, Products
role: Admin
exl-id: e156a752-81b3-4404-81e2-af7ed29f2b1d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-48059 : les commerçants ne peuvent pas enregistrer le *[!UICONTROL Match product by rule]* pour l’attribut categories

Le correctif ACSD-48059 corrige le problème en raison duquel les commerçants ne peuvent pas enregistrer les *[!UICONTROL Match product by rule]* de l’attribut categories dans [!DNL Visual Merchandiser]. Ce correctif est disponible lorsque la version 1.1.27 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48059. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) >=2.3.7 &lt;2.4.7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les commerçants ne peuvent pas enregistrer l’attribut *[!UICONTROL Match product by rule]* pour les catégories dans [!DNL Visual Merchandiser].

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Visual Merchandiser]** > **[!UICONTROL Visible Attributes for Category Rules]**, ajoutez des catégories.
1. Accédez à Adobe Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
   * Accédez à la section [!UICONTROL Products in Category] .
   * Ajoutez une nouvelle condition de *[!UICONTROL Match products by rule]* avec l’attribut categories .

<u>Résultats attendus</u> :

La catégorie a été enregistrée.

<u>Résultats réels</u> :

* Vous ne pouvez pas enregistrer la catégorie avec la nouvelle règle et la nouvelle condition.
* *Un problème est survenu lors de l’enregistrement de la catégorie* une erreur s’affiche.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
