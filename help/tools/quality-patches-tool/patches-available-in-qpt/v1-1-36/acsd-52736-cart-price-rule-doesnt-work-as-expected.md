---
title: 'ACSD-52736 : [!UICONTROL Cart Price Rule] ne fonctionne pas comme prévu'
description: Appliquez le correctif ACSD-52736 pour résoudre le problème d’Adobe Commerce lorsqu’un [!UICONTROL Cart Price Rule] qui inclut les exigences de quantité de produit configurable ne fonctionne pas comme prévu.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 80c3b14e-62ce-4cfc-b1ff-968e70e3a6f8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-52736 : [!UICONTROL Cart Price Rule] ne fonctionne pas comme prévu

Le correctif ACSD-52736 corrige le problème en raison duquel un [!UICONTROL Cart Price Rule] qui inclut les exigences relatives à la quantité de produits configurable ne fonctionne pas comme prévu. Ce correctif est disponible lorsque la version 1.1.36 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-52736. Notez que le problème a été résolu dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un [!UICONTROL Cart Price Rule] qui inclut les exigences relatives à la quantité de produit configurable ne fonctionne pas comme prévu.

<u>Procédure à suivre </u> :

1. Créez une règle de panier :
   * [!UICONTROL Apply] = pourcentage de remise sur le prix du produit
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Appliquez la règle uniquement aux articles du panier correspondant aux conditions suivantes : La quantité dans le panier est 1
2. Ajoutez au panier un produit dont le [!UICONTROL Qty] est = 2.
3. Vérifiez les prix du panier.

<u>Résultats attendus</u> :

La règle n’est pas appliquée, car la quantité de produits dans le panier est de *2*.

<u>Résultats réels</u> :

La remise est appliquée.

<u> Étapes supplémentaires requises après l’installation du correctif </u> :

Après application du correctif, les conditions des règles du panier utilisant l’attribut *Quantité* doivent être supprimées et ajoutées à nouveau.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
