---
title: 'MDVA-41399 : impossible d’accéder à la fonction Gérer le panier si un client ajoute un produit à une liste de souhaits.'
description: Le correctif MDVA-41399 résout le problème en raison duquel les utilisateurs administrateurs ne peuvent pas accéder à la page Gérer le panier si un client ajoute un produit à la liste des souhaits. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID de correctif est MDVA-41399. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: 81a128b5-0c38-4f8f-b297-1f264952d431
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-41399 : impossible d’accéder à la fonction Gérer le panier si un client ajoute un produit à une liste de souhaits.

Le correctif MDVA-41399 résout le problème en raison duquel les utilisateurs administrateurs ne peuvent pas accéder à la page Gérer le panier si un client ajoute un produit à la liste des souhaits. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID de correctif est MDVA-41399. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs administrateurs ne peuvent pas accéder à la page Gérer le panier si un client ajoute un produit à la liste des souhaits.

<u>Conditions préalables</u> :

1. Créez plusieurs produits.
1. Créez un client.
1. Activez le mode Développeur .

<u>Étapes à reproduire</u> :

1. Accédez à Storefront et connectez-vous en tant que client à partir des conditions préalables.
1. Ajoutez un produit à la liste de souhaits.
1. Dans le panneau Admin, accédez à la page d’édition du client créée, puis cliquez sur le bouton **Gérer le panier** .

<u>Résultats attendus</u> :

L’utilisateur administrateur peut gérer le panier.

<u>Résultats réels</u> :

L’utilisateur administrateur reçoit un message d’erreur : *Une erreur s’est produite. Voir le journal des erreurs pour plus de détails.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
