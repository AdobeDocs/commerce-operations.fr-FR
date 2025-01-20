---
title: 'ACSD-62758 : résolution du problème de rendu vidéo sur les pages de produits configurables'
description: Appliquez le correctif ACSD-62758 pour résoudre le problème d’Adobe Commerce en raison duquel les vidéos de produits sur les pages de détails de produits configurables ne s’affichent pas correctement lorsque les URL contiennent des options d’échantillon présélectionnées.
feature: Catalog Management
role: Admin, Developer
exl-id: 084b497d-4471-4458-bc1d-2a452bfe2662
source-git-commit: e18a41c5abb1cc8b407ff6c188acdeed0e8a7659
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-62758 : résolution du problème de rendu vidéo sur les pages de produits configurables

Le correctif ACSD-62758 corrige le problème en raison duquel les vidéos de produit sur les pages de détails de produit configurables ne s’affichent pas correctement lorsque les URL contiennent des options d’échantillon présélectionnées. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62758. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le rendu des vidéos de produit n’est pas correct sur les pages de détails de produit configurables lorsque l’URL inclut des options d’échantillon présélectionnées, ce qui entraîne l’affichage d’une image statique à la place de la vidéo.

<u>Procédure à suivre </u> :

1. Accédez à [!UICONTROL Stores] > [!UICONTROL Attributes] > [!UICONTROL Product].
1. Sélectionnez l’attribut **[!UICONTROL Color]** et modifiez-le.
1. Mettez à jour les paramètres suivants :
   1. Définissez [!UICONTROL Catalog Input Type for Store Owner] sur [!UICONTROL Visual Swatch].
   1. Définissez **[!UICONTROL Update Product Preview Image]** sur **[!UICONTROL Yes]**.
1. Créez quelques options pour cet attribut.
1. Créez une catégorie et ajoutez-y un nouveau produit configurable à l’aide de l’attribut **[!UICONTROL Color]** .
1. Ajoutez une seule image aléatoire au produit parent.
1. Modifiez les produits enfants configurables nouvellement créés et ajoutez une vidéo à leur galerie multimédia :
   1. Cliquez sur **[!UICONTROL Add Video]** et utilisez l’URL de la vidéo de test : https://vimeo.com/12860646.
1. Enregistrez le produit, effacez le cache et réindexez le magasin.
1. Ouvrez le produit nouvellement créé dans le storefront, sélectionnez l’une des options d’échantillon et vérifiez que la vidéo se charge correctement avec le bouton du lecteur affiché.
1. La vidéo doit se charger comme prévu et le bouton du lecteur doit s’afficher.
1. Cliquez ensuite avec le bouton droit sur l’une des options de l’échantillon, sélectionnez **[!UICONTROL Inspect]** et recherchez l’ID d’attribut et l’ID d’option. Copiez l’URL du produit et ajoutez ce qui suit à sa fin : `www.product-url.com/producit-test#attribute_id=option_id`. Cette opération présélectionne l’option d’échantillon. Ouvrez l’URL mise à jour dans une nouvelle fenêtre.

<u>Résultats attendus</u> :

La vidéo doit se charger correctement, comme lorsqu’une option d’échantillon est sélectionnée manuellement.

<u>Résultats réels</u> :

Une image statique s’affiche à la place de la vidéo. Les erreurs de console sont consignées, indiquant un échec de l’initialisation de la vidéo.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .

