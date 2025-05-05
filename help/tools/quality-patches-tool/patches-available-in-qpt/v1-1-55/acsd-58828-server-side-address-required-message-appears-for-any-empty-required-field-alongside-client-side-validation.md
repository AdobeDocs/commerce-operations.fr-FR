---
title: 'ACSD-58828 : un message indiquant que l’adresse côté serveur est requise s’affiche pour tout champ obligatoire vide, avec une validation côté client.'
description: Appliquez le correctif ACSD-58828 pour résoudre le problème Adobe Commerce en raison duquel le message de validation côté serveur *address is required* s’affiche si un champ obligatoire est vide, avec le message de validation côté client.
feature: Shipping/Delivery, Checkout
role: Admin, Developer
source-git-commit: 3b47046d31a6f71f8c366fb468f435633832c039
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# ACSD-58828 : le message *address côté serveur est requis* s’affiche pour tout champ obligatoire vide, avec la validation côté client.

Le correctif ACSD-58828 corrige le problème en raison duquel le message de validation côté serveur *address is required* s’affiche si un champ obligatoire est vide, avec le message de validation côté client. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 est installé. L’ID de correctif est ACSD-58828. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le message *address de validation côté serveur est requis* s’affiche si un champ obligatoire est vide, en plus du message de validation côté client.

Étapes à reproduire :

1. Connectez-vous en tant que client.
1. Ajoutez un produit au panier.
1. Passez à la caisse.
1. Laissez l’adresse de livraison inchangée.
1. Sélectionnez le **[!UICONTROL Flat rate]** et **[!UICONTROL Next]**.
1. Décochez **[!UICONTROL My billing and shipping address are the same]**.
1. Ajoutez une nouvelle adresse dans la liste déroulante.
1. Laissez le champ requis vide et sélectionnez **[!UICONTROL Update]**.

Résultats attendus :

Le message d’erreur décrit les informations manquantes ou incorrectes requises pour l’extraction.

Résultats réels :

L&#39;adresse d&#39;erreur *est requise. Saisissez et réessayez.* s’affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
