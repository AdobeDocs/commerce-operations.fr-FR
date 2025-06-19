---
title: 'ACSD-62475 : corrige les problèmes de fusion des cartes-cadeaux dans le panier'
description: Appliquez le correctif ACSD-62475 pour résoudre le problème d’Adobe Commerce en raison duquel les produits de carte cadeau avec des détails différents sont fusionnés de manière incorrecte en un seul élément de ligne dans le panier.
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: fc97c3c0-dc1b-4546-aad0-ef3b4b6a3415
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62475 : corrige les problèmes de fusion des cartes-cadeaux dans le panier

Le correctif ACSD-62475 corrige le problème où les produits de carte cadeau avec des détails différents sont incorrectement fusionnés en un seul élément de ligne dans le panier. Ce correctif est disponible lorsque la version 1.1.56 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62475. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits de carte cadeau ajoutés au panier avec des détails d’expéditeur ou de destinataire uniques sont incorrectement fusionnés en un seul élément de ligne, ce qui entraîne des incohérences au niveau des données.

<u>Procédure à suivre </u> :

1. Créez un produit [!UICONTROL Gift Card] avec les paramètres suivants :
   * **[!UICONTROL Card Type]** : [!UICONTROL Virtual]
   * **[!UICONTROL Amount]** : 10

1. Sur le storefront, créez un nouvel utilisateur et connectez-vous.

1. Ajoutez le produit Carte cadeau au panier avec les détails suivants :
   * **[!UICONTROL Sender Name]** : Expéditeur 1
   * **[!UICONTROL Sender Email**] : sender1@test.com
   * **[!UICONTROL Recipient Name**] : Destinataire 1
   * **[!UICONTROL Recipient Email**] : recipient1@test.com


1. Déconnexion

1. Ajoutez le même produit de carte cadeau au panier avec les détails suivants :
   * **[!UICONTROL Sender Name]** : Expéditeur 2
   * **[!UICONTROL Sender Email**] : sender2@test.com
   * **[!UICONTROL Recipient Name**] : Destinataire 2
   * **[!UICONTROL Recipient Email**] : recipient2@test.com

1. Connectez-vous à nouveau et vérifiez le panier.

<u>Résultats attendus</u> :

Les deux cartes-cadeaux doivent apparaître sous la forme de deux lignes distinctes avec leurs détails respectifs.

<u>Résultats réels</u> :

Les cartes-cadeaux sont fusionnées en un seul élément de ligne avec une quantité de 2, en conservant les détails de la première carte-cadeau.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
