---
title: 'ACSD-60267 : FPT s’applique incorrectement lorsque des produits sont ajoutés via des options de produit configurables'
description: Appliquez le correctif ACSD-60267 pour résoudre le problème d’Adobe Commerce où la taxe fixe sur les produits (FPT) s’applique correctement lors de l’ajout direct de produits simples au panier, mais échoue lors de la sélection des mêmes produits par le biais d’options de produits configurables.
feature: Taxes
role: Admin, Developer
exl-id: 919b3b96-1995-4faf-aaf1-b5cbb20e46bf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-60267 : FPT s’applique incorrectement lorsque des produits sont ajoutés via des options de produit configurables

Le correctif ACSD-60267 corrige le problème en raison duquel la taxe fixe sur les produits (FPT) s’applique correctement lors de l’ajout direct de produits simples au panier, mais échoue lors de la sélection des mêmes produits par le biais d’options de produits configurables. Ce correctif est disponible lorsque la version 1.1.54 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) est installée. L’ID du correctif est ACSD-60267. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La taxe sur les produits fixe (FPT) fonctionne correctement lorsque des produits simples avec FPT sont ajoutés au panier, mais FPT n’est pas ajouté lorsque des produits sont ajoutés via une sélection de produits configurable.

<u>Procédure à suivre </u> :

1. Définissez *[!UICONTROL Enable FPT]* sur *Oui* en accédant à *Admin* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > **[!UICONTROL Fixed Product Taxes]**.
1. Créez un attribut FPT et affectez-le à un *[!UICONTROL Attribute Set]*.
1. Ouvrez **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Par *[!UICONTROL Default Label]*, saisissez un libellé qui identifie l’attribut.
1. Définissez *[!UICONTROL Catalog Input for Store Owner]* sur *[!UICONTROL Fixed Product Tax]*.
1. Créez une taxe et une zone et affectez-les à une nouvelle *[!UICONTROL Tax Rule]*.
1. Créez un produit configurable avec deux produits simples.
1. Attribuez maintenant deux valeurs FPT différentes à ces produits simples.
1. Réindexez et vérifiez les prix sur le storefront.
1. Ajoutez les produits au panier et vérifiez les sous-totaux.

<u>Résultats attendus</u> :

* La page *[!UICONTROL Catalog]* affiche les prix FPT inclus.
* Les sous-totaux du panier incluent FPT.

<u>Résultats réels</u> :

* La page *[!UICONTROL Catalog]* n’affiche pas les prix, y compris la valeur FPT.
* Les sous-totaux et le résumé ne sont pas valides.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
