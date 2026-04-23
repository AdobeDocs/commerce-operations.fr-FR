---
title: 'ACSD-64111 : corrige l’erreur *InvalidArgumentException: La classe n’existe pas* lors de la définition de conditions imbriquées pour un composant de produit dans  [!DNL Page Builder]'
feature: Products, Page Builder
role: Admin, Developer
exl-id: dc39c65b-fb78-4105-b0e8-92a78b49adaf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-64111 : corrige l’erreur *InvalidArgumentException: la classe n’existe pas* lors de la définition de conditions imbriquées pour un composant Product dans [!DNL Page Builder]

Le correctif ACSD-64111 corrige le problème où *InvalidArgumentException: Class n’existe pas* une erreur se produit dans `vendor/magento/module-rule/Model/ConditionFactory.php:50` lors de la définition de conditions imbriquées pour un composant Product dans [!DNL Page Builder]. Ce correctif est disponible lorsque la version 1.1.60 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64111. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement)  2.4.6-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur *InvalidArgumentException : la classe n’existe pas dans /app/&lt;project id\>/vendor/magento/module-rule/Model/ConditionFactory.php* est générée lors de l’ajout d’une *[!UICONTROL Conditions Combination]* dans [!DNL Page Builder] condition de widget Produits.

<u>Procédure à suivre </u> :

1. Connectez-vous à l’administration d’Adobe Commerce.
1. Accédez à **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**.
1. Ajoutez une nouvelle page (ou modifiez une page existante).
1. Développez la section **[!UICONTROL Content]** et cliquez sur **[!UICONTROL Edit with Page Builder]**.
1. Ajoutez une nouvelle ligne, puis le widget **[!UICONTROL Products]**.
1. Configurez le widget **[!UICONTROL Products]**.
1. Sélectionnez le **[!UICONTROL Condition]** sous **[!UICONTROL Select Products By]**.
1. Ajoutez une nouvelle condition et sélectionnez **[!UICONTROL Conditions Combination]** dans la liste déroulante.

<u>Résultats attendus</u> :

Aucune erreur dans les journaux.

<u>Résultats réels</u> :

L’exception ci-dessous est enregistrée dans les journaux :

*report.CRITICAL : InvalidArgumentException : la classe n’existe pas dans vendor/magento/module-rule/Model/ConditionFactory.php:50*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
