---
title: 'ACSD-54972 : l’URL de catégorie canonique n’est pas mise à jour'
description: Appliquez le correctif ACSD-54972 pour résoudre le problème d’Adobe Commerce en raison duquel l’URL de catégorie canonique ne se met pas à jour après avoir modifié l’URL de catégorie.
feature: Catalog Management, Products, Categories
role: Admin, Developer
exl-id: c4b17c08-9a2b-44a2-925e-f4c5cce7b760
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-54972 : l’URL de catégorie canonique ne se met pas à jour après avoir modifié l’URL de catégorie

Le correctif ACSD-54972 corrige le problème en raison duquel l’URL de catégorie canonique ne se met pas à jour après avoir modifié l’URL de catégorie. Ce correctif est disponible lorsque la version 1.1.43 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54972. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’URL de catégorie canonique ne se met pas à jour après avoir modifié l’URL de catégorie.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**.

   * Définir *[!UICONTROL Use Canonical Link Meta Tag for Categories]* : *OUI*

2. Créez une catégorie (par exemple, *Nom* : *Catégorie 01*, *Clé URL* : *catégorie-01*).
3. Mettez à jour la *clé d’URL* sur une valeur différente de la valeur d’origine tout en gardant la case à cocher **[!UICONTROL Create Permanent Redirect for old URL]** activée.
4. Nettoyez le cache.
5. Accédez au *[!UICONTROL Category Page]* sur le front-end.
6. Vérifiez la source de la page et recherchez la balise *canonique*.

<u>Résultats attendus</u> :

`<link rel="canonical" href="http://127.0.0.1/pub/category-01-new.html" />`

<u>Résultats réels</u> :

`<link rel="canonical" href="http://127.0.0.1/pub/category-01.html" />`

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
