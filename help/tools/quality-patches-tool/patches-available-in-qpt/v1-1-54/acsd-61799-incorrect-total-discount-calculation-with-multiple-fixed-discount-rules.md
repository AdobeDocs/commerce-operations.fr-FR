---
title: "ACSD-61799 : calcul de la remise totale incorrect avec plusieurs règles de panier de remise fixe appliquées au devis"
description: Appliquez le correctif ACSD-61799 pour corriger le problème Adobe Commerce où la remise totale est incorrectement calculée lorsque plusieurs règles de panier avec remises fixes sont appliquées au guillemet.
feature: Price Rules
role: Admin, Developer
source-git-commit: 0b4c46e0db3dbd7ce5914490ae20471709be261d
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# ACSD-61799 : Calcul incorrect de la remise totale avec plusieurs règles de panier de remise fixe appliquées au devis

Le correctif ACSD-61799 résout/corrige le problème en raison duquel la remise totale est incorrectement calculée lorsque plusieurs règles de panier avec remises fixes sont appliquées au guillemet. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 est installé. L’ID de correctif est ACSD-61799. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La remise totale est incorrectement calculée lorsque plusieurs règles de panier avec *[!UICONTROL Fixed amount discount for the whole cart]* sont appliquées à un panier.

<u>Étapes à reproduire</u> :

1. Créez quatre produits au prix de 1 000 $.
1. Créez trois règles de prix de panier sans conditions qui accordent une remise de 100 € pour l’ensemble du panier.
1. Créez une autre règle de prix de panier qui accorde une remise de 100 € pour l’ensemble du panier, avec une condition qui empêche l’application de la règle.
1. Désactivez la règle.
1. Ajoutez trois produits au panier et observez la remise dans le panier.
1. Ajoutez des produits supplémentaires au panier et observez la remise dans le panier.
1. Activez la règle de prix du panier désactivée.
1. Mettez à jour la page du panier et observez la remise dans le panier.

<u>Résultats attendus</u> :

1. L’ajout de produits supplémentaires au panier ne modifie pas le montant de la remise.
1. L’activation de la règle de prix du panier avec une condition qui ne s’applique pas ne modifie pas le montant de la remise.

<u>Résultats réels</u> :

1. L’ajout de produits supplémentaires au panier modifie le montant de la remise.
1. L’activation de la règle de prix du panier avec une condition qui ne s’applique pas modifie le montant de la remise.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.

