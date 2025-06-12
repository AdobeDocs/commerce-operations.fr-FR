---
title: 'ACSD-48313 : [!UICONTROL configurable_variations] colonne non analysée si la valeur de l’attribut contient une virgule'
description: Appliquez le correctif ACSD-48313 pour résoudre le problème d’Adobe Commerce où la colonne [!UICONTROL configurable_variations] n’est pas analysée si la valeur de l’attribut contient une virgule.
feature: Attributes, Configuration
role: Admin
exl-id: 1ce0c8dc-0d03-4ebd-b02a-08090b244190
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-48313 : **[!UICONTROL configurable_variations]** colonne non analysée si la valeur de l’attribut contient une virgule

Le correctif ACSD-48313 résout le problème où **[!UICONTROL configurable_variations]** colonne n’est pas analysée si la valeur de l’attribut contient une virgule. Ce correctif est disponible lorsque la version 1.1.25 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48313. La version dans laquelle ce problème sera résolu n’est pas encore disponible.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Après avoir exporté des produits configurables, le fichier obtenu ne peut plus être importé en raison d’un problème de mise en forme avec l’attribut **[!UICONTROL configurable_variations]**. Cela se produit lorsque des options d’attribut comportent une virgule.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** et créez un attribut _Taille_ :
1. Type d’entrée de catalogue pour le propriétaire de la boutique : **[!UICONTROL Dropdown]**.
1. Créez des options qui comprennent une virgule, par exemple :
   * 10,2 cm
   * 15,5 cm
1. **[!UICONTROL Advanced Attribute Properties]** - Portée : _globale_.
1. Créez un produit configurable à l’aide de la fonctionnalité Créer des configurations .
1. Sélectionnez l’attribut ci-dessus _Taille_ et les deux options qui incluent la virgule.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** et créez une exportation de produits (exécutez le cron pour déclencher la génération du fichier CSV).
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** et essayez de réimporter le même fichier CSV créé ci-dessus.

<u>Résultats attendus</u> :

L’utilisateur doit pouvoir importer le fichier.

<u>Résultats réels</u> :

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
