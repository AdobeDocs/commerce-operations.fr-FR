---
title: "ACSD-48204 : la règle de prix du catalogue créée à partir de l’attribut *Oui/Non* ne considère pas la portée sélectionnée"
description: Appliquez le correctif ACSD-48204 pour résoudre le problème Adobe Commerce en raison duquel la règle de prix du catalogue créée à partir de l’attribut *Oui/Non* ne prend pas en compte la portée sélectionnée.
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-48204 : La règle de prix du catalogue créée à partir de l’attribut *Oui/Non* ne considère pas la portée sélectionnée.

Le correctif ACSD-48204 corrige le problème en raison duquel la règle de prix du catalogue créée à partir de l’attribut *Oui/Non* ne prend pas en compte la portée sélectionnée. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 est installé. L’ID de correctif est ACSD-48204. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La règle de prix du catalogue créée à partir de l’attribut *Oui/Non* ne prend pas en compte la portée sélectionnée.

<u>Étapes à reproduire</u> :

1. Créez deux sites web (par défaut et W2).
1. Créez un attribut de produit de type *Oui/Non*.
   * Set [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Créez un produit configurable basé sur n’importe quel attribut comportant deux variantes (V1 et V2).
   * Ajoutez l’attribut *Yes/No* au jeu d’attributs de variations configurables.
   * Pour l’une des variations (V1), définissez la valeur sur *[!UICONTROL Yes]* sur le site web autre que le site par défaut (W2).
1. Créez une règle de catalogue :
   * Application sur les deux sites web
   * Condition : *Oui/Non* la valeur de l’attribut est *[!UICONTROL Yes]*
   * Remise = 50 %
1. Ouvrez le produit configurable sur le site web non-default (W2).
1. Vérifiez que la remise de 50 % est appliquée à la variation V1.
1. Ouvrez la variante V1 dans l’administrateur Adobe Commerce.
   * Basculer vers le site web par défaut
   * N’effectuez aucune modification et enregistrez le produit
1. Actualisez la page de storefront des produits configurables.

<u>Résultats attendus</u> :

La remise de 50 % est toujours appliquée à la variation V1, car aucune modification n’a été apportée.

<u>Résultats réels</u> :

La remise disparaît.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
