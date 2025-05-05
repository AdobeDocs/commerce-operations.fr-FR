---
title: 'ACSD-56246 : la planification des mises à jour de produit effacent les valeurs d’attribut multi-select'
description: Appliquez le correctif ACSD-56246 pour résoudre le problème Adobe Commerce en raison duquel la planification des mises à jour de produit efface les valeurs d’attribut multi-select.
feature: Products, Attributes, Staging
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-56246 : la planification des mises à jour de produit efface les valeurs d’attributs à sélection multiple

Le correctif ACSD-56246 corrige le problème en raison duquel la planification des mises à jour de produit efface les valeurs d’attributs à sélection multiple. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 est installé. L’ID de correctif est ACSD-56246. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les mises à jour de produit planifiées effacent les valeurs d’attribut multi-select.

<u>Étapes à reproduire</u> :

1. Installez Adobe Commerce.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** et créez l’attribut suivant :

   * Libellé par défaut : Programme
   * Type d’entrée de catalogue pour le propriétaire du magasin : sélection multiple
   * Gérer les options (valeurs de votre attribut) : choix, paysage, Safetybouc
   * Code d’attribut : customer_program
   * Portée : globale
   * Ajouter aux options de colonne : Non
   * Utiliser dans les options de filtre : Non
   * Propriétés Storefront
   * Position : *333*
   * Autoriser les balises d’HTML sur Storefront : Non

1. Exécuter
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Exécuter
   `bin/magento setup:upgrade`.
1. Accédez à **[!UICONTROL Admin]** > Sélectionner un produit simple > Sélectionner tous les éléments dans l’attribut de programme > Cliquez sur **[!UICONTROL Save the product]**.
1. Planifiez une mise à jour de ce produit à la minute suivante, puis exécutez la commande ci-dessous pour que l’évaluation de contenu fonctionne :
   `for i in {1..100}; do bin/magento cron:run; done`.

<u>Résultats attendus</u> :

L’attribut **[!UICONTROL program]** du produit ne doit pas changer.

<u>Résultats réels</u> :

L’attribut **[!UICONTROL program]** du produit est effacé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
