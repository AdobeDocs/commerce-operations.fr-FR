---
title: 'ACSD-61799 : calcul de remise totale incorrect avec plusieurs règles de panier de remises fixes appliquées au devis'
description: Appliquez le correctif ACSD-61799 pour résoudre le problème d’Adobe Commerce en raison duquel la remise totale n’est pas correctement calculée lorsque plusieurs règles de panier avec des remises fixes sont appliquées au devis.
feature: Price Rules
role: Admin, Developer
exl-id: a87ec1cd-f141-43b9-bde1-eca354c12d4e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-61799 : calcul de remise totale incorrect avec plusieurs règles de panier de remises fixes appliquées au devis

Le correctif ACSD-61799 résout/corrige le problème où la remise totale est incorrectement calculée lorsque plusieurs règles de panier avec des remises fixes sont appliquées au devis. Ce correctif est disponible lorsque la version 1.1.54 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61799. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La remise totale n’est pas calculée correctement lorsque plusieurs règles de panier avec des *[!UICONTROL Fixed amount discount for the whole cart]* sont appliquées à un panier.

<u>Procédure à suivre </u> :

1. Créez quatre produits au prix de 1 000 $.
1. Créez trois règles de prix de panier sans aucune condition qui donnent une remise de 100 $ pour l’ensemble du panier.
1. Créez une autre règle de prix de panier qui accorde une remise de 100 $ pour l’ensemble du panier, avec une condition qui empêche l’application de la règle.
1. Désactivez la règle.
1. Ajoutez trois produits au panier et observez la réduction dans le panier.
1. Ajoutez des produits supplémentaires au panier et observez la réduction dans le panier.
1. Activez la règle de prix de panier désactivée.
1. Mettez à jour la page du panier et observez la réduction dans le panier.

<u>Résultats attendus</u> :

1. L’ajout de produits supplémentaires au panier ne modifie pas le montant de la remise.
1. L’activation de la règle de prix de panier avec une condition qui ne s’applique pas ne modifie pas le montant de la remise.

<u>Résultats réels</u> :

1. L’ajout de produits supplémentaires au panier modifie le montant de la remise.
1. L’activation de la règle de prix de panier avec une condition qui ne s’applique pas modifie le montant de la remise.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
