---
title: 'ACSD-58828 : le message *l’adresse est requise* côté serveur s’affiche pour tout champ obligatoire vide, avec la validation côté client'
description: Appliquez le correctif ACSD-58828 pour résoudre le problème d’Adobe Commerce où le message de validation côté serveur *address est obligatoire* apparaît si un champ obligatoire reste vide, à côté du message de validation côté client.
feature: Shipping/Delivery, Checkout
role: Admin, Developer
exl-id: 6c19773d-cb75-409f-bbd7-78d285a0252a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-58828 : *adresse côté serveur est requise* un message s’affiche pour tout champ obligatoire vide, avec la validation côté client

Le correctif ACSD-58828 corrige le problème où le message de validation côté serveur *address est obligatoire* s’affiche si un champ obligatoire reste vide, à côté du message de validation côté client. Ce correctif est disponible lorsque la version 1.1.55 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-58828. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le message de validation côté serveur *adresse requise* s’affiche si un champ obligatoire reste vide, à côté du message de validation côté client.

Procédure à suivre :

1. Connectez-vous en tant que client.
1. Ajoutez un produit au panier.
1. Passer en caisse.
1. Laissez l’adresse de livraison inchangée.
1. Sélectionnez le **[!UICONTROL Flat rate]** et sélectionnez **[!UICONTROL Next]**.
1. Décochez **[!UICONTROL My billing and shipping address are the same]**.
1. Ajoutez une nouvelle adresse à partir de la liste déroulante.
1. Laissez tout champ obligatoire vide et sélectionnez **[!UICONTROL Update]**.

Résultats attendus :

Le message d’erreur décrit des informations manquantes ou incorrectes requises pour l’extraction.

Résultats réels :

L’erreur *address est requise. Saisissez , puis réessayez.* s’affiche.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
