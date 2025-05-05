---
title: "MDVA-38666 : L’utilisateur administrateur ne peut pas modifier les options de produit configurables"
description: Le correctif MDVA-38666 résout le problème où l’utilisateur administrateur ne peut pas modifier les options de produit configurables dans le panier du client. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID de correctif est MDVA-38666. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Admin Workspace, Configuration, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-38666 : L’utilisateur administrateur ne peut pas modifier les options de produit configurables.

Le correctif MDVA-38666 résout le problème où l’utilisateur administrateur ne peut pas modifier les options de produit configurables dans le panier du client. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID de correctif est MDVA-38666. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur administrateur ne peut pas modifier les options de produit configurables dans le panier du client.

<u>Étapes à reproduire</u> :

1. Définissez la portée du compte client sur Global.
1. Créez deux sites web avec des magasins.
1. Créez deux produits configurables et affectez-les à chaque site web.
1. Créez un compte client dans le front-end et connectez-vous.
1. Ajoutez un produit au panier et effectuez un passage en caisse (ceci afin de rendre les ID de guillemet différents sur chaque site web).
1. Ajoutez un produit au panier et laissez-le.
1. Passez au deuxième site web et ajoutez le produit au panier (la même connexion doit fonctionner puisque la portée du compte client est définie sur Global).
1. Ouvrez le client à partir de l’administrateur et accédez à l’onglet Panier.
1. Basculez le magasin dans la liste déroulante et essayez de modifier la configuration.

<u>Résultats attendus</u> :

L’utilisateur obtient une fenêtre contextuelle avec des options configurables.

<u>Résultats réels</u> :

Aucun formulaire contextuel ne s’affiche. L’utilisateur ne peut pas modifier la configuration.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
