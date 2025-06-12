---
title: 'ACSD-48204 : la règle de prix de catalogue créée en fonction de l’attribut *Oui/Non* ne prend pas en compte la portée sélectionnée'
description: Appliquez le correctif ACSD-48204 pour résoudre le problème d’Adobe Commerce en raison duquel la règle de prix de catalogue créée en fonction de l’attribut *Oui/Non* ne prend pas en compte la portée sélectionnée.
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
exl-id: 69f2b35c-856e-4f96-ae2f-fb0c64d5eb94
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-48204 : la règle de prix de catalogue créée en fonction de l’attribut *Oui/Non* ne prend pas en compte la portée sélectionnée

Le correctif ACSD-48204 corrige le problème en raison duquel la règle de prix de catalogue créée en fonction de l’attribut *Oui/Non* ne prend pas en compte la portée sélectionnée. Ce correctif est disponible lorsque la version 1.1.28 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48204. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La règle de prix catalogue créée en fonction de l&#39;attribut *Oui/Non* ne prend pas en compte la portée sélectionnée.

<u>Procédure à suivre </u> :

1. Créez deux sites web (par défaut et W2).
1. Créez un attribut de produit de type *Oui/Non*.
   * Définir [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Créez un produit configurable basé sur n’importe quel attribut avec deux variations (V1 et V2).
   * Ajoutez l’attribut *Oui/Non* au jeu d’attributs de variations configurables
   * Pour l’une des variations (V1), définissez la valeur sur *[!UICONTROL Yes]* sur le site web non par défaut (W2)
1. Créez une règle de catalogue :
   * Appliqué aux deux sites web
   * Condition : *Oui/Non* la valeur de l’attribut est *[!UICONTROL Yes]*
   * Remise = 50 %
1. Ouvrez le produit configurable sur le site web autre que le site web par défaut (W2).
1. Vérifiez que la réduction de 50 % est appliquée à la variation V1.
1. Ouvrez la variation V1 dans Adobe Commerce Admin.
   * Passer au site web par défaut
   * N’effectuez aucune modification et enregistrez le produit
1. Actualisez la page du storefront des produits configurables.

<u>Résultats attendus</u> :

La réduction de 50 % est toujours appliquée à la variation V1, car aucune modification n’a été apportée.

<u>Résultats réels</u> :

La remise disparaît.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
