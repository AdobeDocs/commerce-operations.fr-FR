---
title: 'MDVA-37592 : Le tri par prix ne fonctionne pas pour les produits dont le prix est égal à zéro'
description: Le correctif Adobe Commerce MDVA-37592 résout le problème où le tri par prix ne fonctionne pas correctement pour les produits dont le prix zéro est affecté à un catalogue partagé. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 est installé. L’ID du correctif est MDVA-37592. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
exl-id: 4d4a158c-2020-42a4-9b8b-14c9b48b4107
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-37592 : Le tri par prix ne fonctionne pas pour les produits dont le prix est égal à zéro

Le correctif Adobe Commerce MDVA-37592 résout le problème où le tri par prix ne fonctionne pas correctement pour les produits dont le prix zéro est affecté à un catalogue partagé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 est installé. L’ID du correctif est MDVA-37592. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur notre architecture cloud 2.4.0-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (tous les types de déploiement) 2.3.6-2.4.2-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le tri par prix ne fonctionne pas correctement pour les produits dont le prix zéro est affecté à un catalogue partagé.

<u>Conditions préalables</u> :

B2B est installé.

<u>Procédure à suivre </u> :

1. Activez le catalogue partagé.
1. Créez quatre produits aux prix suivants et affectez-les à une catégorie : 50 $, 60 $, 70 $ et 80 $.
1. Créez un catalogue partagé avec les produits ci-dessus.
1. Définissez le prix personnalisé sur zéro pour le produit au prix de 70 $.
1. Créez maintenant un utilisateur d&#39;entreprise et affectez-le au catalogue partagé qui vient d&#39;être créé.
1. Connectez-vous à l’aide du compte d’entreprise et accédez à la catégorie à laquelle les produits sont affectés.
1. Essayez de trier par prix.

<u>Résultats attendus</u> :

Le produit au prix zéro est trié correctement.

<u>Résultats réels</u> :

Le produit au prix zéro n&#39;est PAS trié correctement. Au lieu de cela, il est trié selon le prix d’origine.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
