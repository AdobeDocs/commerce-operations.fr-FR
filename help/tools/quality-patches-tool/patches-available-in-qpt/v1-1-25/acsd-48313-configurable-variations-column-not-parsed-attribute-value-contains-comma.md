---
title: 'ACSD-48313 : colonne [!UICONTROL configurable_variations] non analysée si la valeur d’attribut contient une virgule'
description: Appliquez le correctif ACSD-48313 pour résoudre le problème Adobe Commerce où la colonne [!UICONTROL configurable_variations] n’est pas analysée si la valeur de l’attribut contient une virgule.
feature: Attributes, Configuration
role: Admin
exl-id: 1ce0c8dc-0d03-4ebd-b02a-08090b244190
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-48313 : colonne **[!UICONTROL configurable_variations]** non analysée si la valeur d’attribut contient une virgule

Le correctif ACSD-48313 résout le problème où la colonne **[!UICONTROL configurable_variations]** n’est pas analysée si la valeur d’attribut contient une virgule. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 est installé. L’ID de correctif est ACSD-48313. La version dans laquelle ce problème sera corrigé n’est pas encore disponible.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Après l’exportation de produits configurables, le fichier obtenu ne peut plus être importé en raison d’un problème de mise en forme avec l’attribut **[!UICONTROL configurable_variations]**. Cela se produit lorsqu’il existe des options d’attribut qui incluent une virgule.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** et créez un attribut _Size_ :
1. Type d’entrée de catalogue pour le propriétaire du magasin : **[!UICONTROL Dropdown]**.
1. Créez des options qui incluent une virgule, par exemple :
   * 10,2 cm
   * 15,5 cm
1. **[!UICONTROL Advanced Attribute Properties]** - Portée : _Global_.
1. Créez un produit configurable à l’aide de la fonctionnalité Créer des configurations .
1. Sélectionnez l’attribut _Size_ ci-dessus et les deux options qui incluent la virgule.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** et créez une exportation de produits (exécutez le cron pour déclencher la génération du fichier CSV).
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** et essayez de réimporter le même fichier CSV créé ci-dessus.

<u>Résultats attendus</u> :

L’utilisateur doit pouvoir importer un fichier.

<u>Résultats réels</u> :

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
