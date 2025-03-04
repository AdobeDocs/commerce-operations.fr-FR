---
title: 'ACSD-63454 : la valeur par défaut pour les attributs Menu déroulant et Sélection multiple n’est pas enregistrée correctement dans la base de données'
description: Appliquez le correctif ACSD-63454 pour résoudre le problème d’Adobe Commerce où la valeur par défaut d’un attribut Dropdown et Sélection multiple n’est pas enregistrée correctement dans la base de données.
feature: Attributes, Products
role: Admin, Developer
exl-id: fa79a3bb-e615-44cb-8d84-da892f924fd0
source-git-commit: cb73a5a346ec0e8acd59accf73605e25ef35c3ca
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-63454 : la valeur par défaut des attributs [!UICONTROL Dropdown] et [!UICONTROL Multiple Select] n’est pas enregistrée correctement dans la base de données

Le correctif ACSD-63454 corrige le problème en raison duquel la valeur par défaut d’un [!UICONTROL Dropdown] et des attributs de [!UICONTROL Multiple Select] n’est pas enregistrée correctement dans la base de données. Ce correctif est disponible lorsque la version 1.1.59 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63454. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La valeur par défaut des attributs [!UICONTROL Dropdown] et [!UICONTROL Multiple Select] n’est pas enregistrée correctement dans la base de données ; au lieu de mettre à jour la valeur par défaut, la nouvelle valeur est ajoutée à l’ancienne, séparée par une virgule.

<u>Procédure à suivre </u> :

1. Connectez-vous au serveur principal, accédez à **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Product]**.
1. Cliquez sur **[!UICONTROL Add New Attribute]**.
1. Dans l’onglet **[!UICONTROL Properties]** , définissez les éléments suivants :
   * **[!UICONTROL Default Label]** : *test*
   * **[!UICONTROL Catalog Input Type for Store Owner]** : *[!UICONTROL Multiple Select]*
   * **[!UICONTROL Manage Options]** : ajoutez deux options sans sélectionner de **[!UICONTROL Is Default]**.
1. Cliquez sur **[!UICONTROL Save Attribute]**.
1. Vérifiez dans la base que la colonne `default_value` est vide.

   `select attribute_code, default_value from eav_attribute where attribute_code = 'test';`

1. Revenez en arrière et définissez l’une des deux options comme **[!UICONTROL Is Default]**.
1. Vérifiez à nouveau la base de données pour vous assurer que `default_value` contient désormais l&#39;identifiant d&#39;option sélectionné.
1. Revenez en arrière et modifiez l’option par défaut en sélectionnant l’autre option.

<u>Résultats attendus</u> :

La nouvelle valeur par défaut doit remplacer l’ancienne valeur de la base de données.

<u>Résultats réels</u> :

Au lieu de remplacer la valeur par défaut par la nouvelle, il ajoute la nouvelle valeur à l’ancienne valeur, séparée par une virgule.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
