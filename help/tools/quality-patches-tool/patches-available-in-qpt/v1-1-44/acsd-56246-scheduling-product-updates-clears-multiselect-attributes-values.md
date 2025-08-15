---
title: 'ACSD-56246 : planification des mises à jour de produits effacer les valeurs d’attribut multiselect'
description: Appliquez le correctif ACSD-56246 pour résoudre le problème d’Adobe Commerce où la planification des mises à jour de produits efface les valeurs d’attributs à sélection multiple.
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: 1751a03d-2610-423f-be2f-b9d060452904
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-56246 : la planification des mises à jour de produits efface les valeurs d’attributs à sélection multiple

Le correctif ACSD-56246 corrige le problème où la planification des mises à jour de produits efface les valeurs d’attributs à sélection multiple. Ce correctif est disponible lorsque la version 1.1.44 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-56246. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les mises à jour de produit planifiées effacent les valeurs d’attribut multiselect.

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** et créez l’attribut suivant :

   * Libellé par défaut : Program
   * Type d’entrée de catalogue pour le propriétaire de la boutique : sélection multiple
   * Gérer les options (valeurs de votre attribut) : Choix, Paysage de soleil, Safetyshield
   * Code d’attribut : customer_program
   * Portée : globale
   * Ajouter aux options de colonne : non
   * Utiliser dans les options de filtre : non
   * Propriétés du storefront
   * Position : *333*
   * Autoriser les balises HTML sur Storefront : non

1. Exécuter
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Exécuter
   `bin/magento setup:upgrade`.
1. Accédez à **[!UICONTROL Admin]** > Choisir un produit simple > Sélectionner tous les éléments dans l’attribut de programme > Cliquer sur le **[!UICONTROL Save the product]**.
1. Planifiez une mise à jour pour ce produit dans la minute qui suit et exécutez la commande ci-dessous pour que l’évaluation de contenu fonctionne :
   `for i in {1..100}; do bin/magento cron:run; done`.

<u>Résultats attendus</u> :

L’attribut **[!UICONTROL program]** du produit ne doit pas changer.

<u>Résultats réels</u> :

L’attribut **[!UICONTROL program]** du produit est effacé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
