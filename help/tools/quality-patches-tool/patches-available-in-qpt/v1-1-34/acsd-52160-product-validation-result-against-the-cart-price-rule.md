---
title: 'ACSD-52160 : résultat de la validation du produit par rapport à la règle de prix du panier'
description: Appliquez le correctif ACSD-52160 pour résoudre le problème d’Adobe Commerce en raison duquel le résultat de la validation du produit par rapport à la règle de prix du panier n’est pas correctement évalué en fonction de la condition de règle *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.
exl-id: 8f8799c9-850a-4c8f-bde4-68df64e46c85
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52160 : le résultat de la validation du produit par rapport à la règle de prix de panier n’est pas correctement évalué

Le correctif ACSD-52160 corrige le problème où le résultat de validation du produit par rapport à la règle de prix de panier n’est pas correctement évalué en fonction de la condition de règle *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*. Ce correctif est disponible lorsque la version 1.1.34 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-52160. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le résultat de validation du produit par rapport à la règle de prix de panier n’est pas correctement évalué en fonction de la condition de règle *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.

<u>Procédure à suivre </u> :

1. Créez deux produits affectés à deux catégories différentes.
1. Créez un **[!UICONTROL Cart Price Rule]** avec des conditions telles que :

   * **SKU 1** dans le paramètre *[!UICONTROL FOUND]*
   * **SKU 2** dans le paramètre *[!UICONTROL NOT FOUND]*

1. Ajoutez les deux produits au panier.
1. Appliquez le code de coupon.

<u>Résultats attendus</u>

Le code de coupon n’est pas appliqué, car le panier contient des produits de la catégorie restreinte .

<u>Résultats réels</u>

Le code de coupon est appliqué.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr>) dans le guide de [!DNL Quality Patches Tool].
