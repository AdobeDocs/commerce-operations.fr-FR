---
title: 'MDVA-37592 : Le tri par prix ne fonctionne pas pour les produits dont le prix est nul'
description: Le correctif Adobe Commerce MDVA-37592 résout le problème en raison duquel le tri par prix ne fonctionne pas correctement pour les produits dont le prix est nul affecté à un catalogue partagé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0 est installé. L’ID de correctif est MDVA-37592. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
exl-id: 4d4a158c-2020-42a4-9b8b-14c9b48b4107
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-37592 : Le tri par prix ne fonctionne pas pour les produits dont le prix est nul

Le correctif Adobe Commerce MDVA-37592 résout le problème en raison duquel le tri par prix ne fonctionne pas correctement pour les produits dont le prix est nul affecté à un catalogue partagé. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0 est installé. L’ID de correctif est MDVA-37592. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur notre architecture cloud 2.4.0-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (tous les types de déploiement) 2.3.6-2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le tri par prix ne fonctionne pas correctement pour les produits dont le prix est nul affecté à un catalogue partagé.

<u>Conditions préalables</u> :

B2B est installé.

<u>Étapes à reproduire</u> :

1. Activez le catalogue partagé.
1. Créez quatre produits avec les prix suivants et attribuez-les à une catégorie : 50, 60, 70 et 80 USD.
1. Créez un catalogue partagé avec les produits ci-dessus.
1. Définissez le prix personnalisé sur zéro pour le produit dont le prix est de 70 $.
1. Créez maintenant un utilisateur de l’entreprise et affectez-le au catalogue partagé qui vient d’être créé.
1. Connectez-vous à l’aide du compte de l’entreprise et accédez à la catégorie à laquelle les produits sont affectés.
1. Essayez de trier par prix.

<u>Résultats attendus</u> :

Le produit dont le prix est nul est correctement trié.

<u>Résultats réels</u> :

Le produit dont le prix est zéro n’est PAS correctement trié. À la place, il est trié en fonction du prix d’origine.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
