---
title: 'ACSD-55339 : résolution du problème de rognage de SKU dans les devis négociables pour Adobe Commerce'
description: Appliquez le correctif ACSD-55339 pour résoudre le problème d’Adobe Commerce où les SKU de produit avec des zéros au début sont tronqués, provoquant des erreurs de négociation.
feature: B2B, Quotes
role: Admin, Developer
source-git-commit: 5153eadfe0d90c256bf6d294fcebb1dd8c0a7093
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-55339 : résolution du problème de rognage de SKU dans les devis négociables pour Adobe Commerce

Le correctif ACSD-55339 corrige le problème où les SKU de produit avec des zéros de début sont tronqués, entraînant des erreurs pendant le processus de négociation. Ce correctif est disponible lorsque la version 1.1.56 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-55339. Notez que le problème est planifié pour être corrigé dans Adobe Commerce B2B 1.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les SKU de produit numériques avec des zéros de début sont tronqués lorsqu&#39;ils sont utilisés dans des devis négociables, ce qui entraîne des erreurs qui empêchent la mise à jour des quantités ou la définition de prix.

<u>Procédure à suivre </u> :

1. Accédez à la section de création de produit dans le panneau d’administration.
1. Définissez la [!UICONTROL SKU] du produit sur 01910.
1. Connectez-vous au storefront et effectuez les opérations suivantes :
   1. Ajoutez le produit au panier.
   1. Affichez et modifiez le panier.
   1. Demandez un devis.
1. Accédez à [!UICONTROL admin] > [!UICONTROL Quote] > [!UICONTROL View] et [!UICONTROL Add Products by SKU] - 01910.

**Remarque :** le SKU s’affiche en *1910* au lieu de *01910*. Cette incohérence empêche l’utilisateur de mettre à jour la quantité ou de définir les prix, car aucun produit avec le SKU 1910 n’existe dans le catalogue.

<u>Résultats attendus</u> :

Le devis négociable doit être mis à jour sans erreur.

<u>Résultats réels</u> :

Un message d’avertissement s’affiche indiquant que le produit n’existe pas.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
