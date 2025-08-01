---
title: 'ACSD-48210 : l’attribut d’étendue spécifique à la vue de magasin remplace les valeurs globales'
description: Appliquez le correctif ACSD-48210 pour résoudre le problème Adobe Commerce de mise à jour d’un attribut *[!UICONTROL Website Scope]* dans une vue de magasin spécifique qui remplace les valeurs d’attribut dans la portée globale.
feature: Products, Attributes
role: Admin, Developer
exl-id: 944089c6-2f05-4c51-86ea-ede124bff80b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-48210 : les attributs d’étendue spécifiques à la vue de magasin remplacent les valeurs globales

Le correctif ACSD-48210 corrige le problème en raison duquel, lors de la mise à jour d’un attribut *[!UICONTROL Website Scope]* dans une vue de magasin spécifique, remplace les valeurs d’attribut dans la portée globale. Ce correctif est disponible lorsque la version 1.1.50 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48210. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de la mise à jour d’un attribut *[!UICONTROL Website Scope]* dans une vue de magasin spécifique, remplace les valeurs d’attribut dans la portée globale.

L&#39;importation de prix de produit avec plusieurs lignes partageant le même `SKU` et `store_view_code` a provoqué des mises à jour incorrectes des prix dans les étendues de *[!UICONTROL All Store View]* et de *[!UICONTROL Default Store]*. La modification de l’attribut de portée de site web dans une vue de magasin spécifique ne remplace plus la valeur de l’attribut dans la portée globale.
<u>Procédure à suivre </u> :

1. Configurez le *[!UICONTROL Catalog Price Scope]* à *[!UICONTROL Website]*.
1. Créez un produit simple appelé *SP01* et définissez le prix sur *$84.50*.
1. Importez le produit à l’aide du fichier CSV suivant fourni ci-dessous :

   ```
   sku,store_view_code,price
   SP01,default,99.99
   SP01,default,86.59
   ```

1. Vérifiez le prix du produit dans les portées *[!UICONTROL All Store View]* et *[!UICONTROL Default Store]*.

<u>Résultats attendus</u> :

* La première valeur non vide est utilisée pour la portée *[!UICONTROL Default Store]*.
* La portée de la *[!UICONTROL All Store View]* reste inchangée.

<u>Résultats réels</u> :

* Le prix du périmètre de *[!UICONTROL All Store View]* passe à 86,59 **.
* Le prix du périmètre de *[!UICONTROL Default Store]* passe à 86,59 **.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
