---
title: 'ACSD-54776 : les [!UICONTROL Use Default Value] non cochées et les valeurs de champ de produit non par défaut ne sont pas enregistrées pour la deuxième vue de site web, de magasin et de magasin'
description: Appliquez le correctif ACSD-54776 pour résoudre le problème d’Adobe Commerce où les valeurs de champ de produit non cochées [!UICONTROL Use Default Value] et non par défaut ne sont pas enregistrées pour la deuxième vue de site web, de magasin et de magasin.
feature: Products
role: Admin, Developer
exl-id: d9f63abb-5d00-4777-a186-1120344af018
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-54776 : les *[!UICONTROL Use Default Value]* non cochées et les valeurs de champ de produit non par défaut ne sont pas enregistrées

>[!NOTE]
>
>Ce correctif remplace le correctif [ACSD-51984](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) publié dans QPT 1.1.35.

Le correctif ACSD-54776 corrige le problème en raison duquel les valeurs de champ de produit non cochées **[!UICONTROL Use Default Value]** et non par défaut ne sont pas enregistrées pour la deuxième vue de site web, de magasin et de magasin. Ce correctif est disponible lorsque la version 1.1.39 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54776. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p4, 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les valeurs de champ de produit *[!UICONTROL Use Default Value]* et non par défaut non cochées ne sont pas enregistrées pour la deuxième vue de site web, de magasin et de magasin.

<u>Procédure à suivre </u> :

1. Accédez au serveur principal, puis à **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** et créez un site web, un magasin et une vue de magasin.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, créez un produit simple et enregistrez-le, puis affectez le produit aux deux sites web à partir du **[!UICONTROL Product in Websites]**.
1. Modifiez la portée sur la vue de magasin nouvellement créée à partir de l’étape 2.
1. Accédez à **[!UICONTROL Search Engine Optimization]** et décochez les cases **[!UICONTROL Use Default Value]** pour [!UICONTROL Meta Title], [!UICONTROL Meta Keywords] et [!UICONTROL Meta Description].
1. Nettoyez le texte des champs *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* et *[!UICONTROL Meta Description]*, puis cliquez sur **[!UICONTROL Save]**.
1. Accédez à nouveau à **[!UICONTROL Search Engine Optimization]**.

<u>Résultats attendus</u>

Les valeurs des champs et des cases à cocher sont enregistrées.

<u>Résultats réels</u>

Les valeurs des champs et des cases à cocher ne sont pas enregistrées.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr>) dans le guide de [!DNL Quality Patches Tool].
