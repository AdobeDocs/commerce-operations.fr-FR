---
title: 'ACSD-63469 : les remises sur panier à montant fixe ne sont pas appliquées correctement avec plusieurs règles'
description: Appliquez le correctif ACSD-63469 pour résoudre le problème d’Adobe Commerce en raison duquel les remises forfaitaires pour l’ensemble du panier ne s’appliquent pas correctement lorsque plusieurs règles sont appliquées.
feature: Price Rules
role: Admin, Developer
source-git-commit: 3699a9f64198558fcf1ffe53753f035d22c2d301
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---


# ACSD-63469 : les remises sur panier à montant fixe ne sont pas appliquées correctement avec plusieurs règles

Le correctif ACSD-63469 corrige le problème où les remises fixes pour l’ensemble du panier ne s’appliquent pas correctement lorsque plusieurs règles sont appliquées. Ce correctif est disponible lorsque la version 1.1.59 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63469. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque plusieurs règles de **[!UICONTROL Fixed amount discount for whole cart]** sont appliquées simultanément et que les produits ont des prix réduits ou spéciaux, la valeur de remise est calculée de manière incorrecte.

<u>Procédure à suivre </u> :

1. Créez deux produits au prix de 850 $ et 85 $, et définissez leurs prix spéciaux à 765 $ et 68 $, respectivement.
1. Créez deux **[!UICONTROL Cart Price Rules]** comme suit :
   * Règle 1
      * **[!UICONTROL Conditions]** : pour le produit de 850 $, définissez *Qté* sur *égal ou supérieur à 2*
      * **[!UICONTROL Actions]** : Appliquer une **[!UICONTROL Fixed amount discount for whole cart]** de *$153*
   * Règle 2
      * **[!UICONTROL Conditions]** : pour le produit à 85 $, définissez *Qté* sur *égal ou supérieur à 2*
      * **[!UICONTROL Actions]** : Appliquer une **[!UICONTROL Fixed amount discount for whole cart]** de *$14*
1. Ajoutez les deux produits au panier, chacun avec une quantité de 2.

<u>Résultats attendus</u> :

La remise appliquée dans le panier est de 167 $.

<u>Résultats réels</u> :

La remise appliquée dans le panier est de 41 $.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Étapes supplémentaires requises après l’installation du correctif

(Cette section est facultative ; certaines étapes peuvent être nécessaires après l’application du correctif pour résoudre le problème.) 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .

