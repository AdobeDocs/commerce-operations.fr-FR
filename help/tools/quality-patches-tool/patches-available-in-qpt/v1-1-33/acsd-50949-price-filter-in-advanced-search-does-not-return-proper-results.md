---
title: 'ACSD-50949 : Le filtre de prix dans la recherche avancée ne renvoie pas de résultats appropriés lorsqu’il est utilisé avec le filtre SKU.'
description: Appliquez le correctif ACSD-50949 pour résoudre le problème Adobe Commerce en raison duquel le filtre de prix dans la recherche avancée ne renvoie pas de résultats appropriés lorsqu’il est utilisé avec le filtre SKU.
feature: Orders, Search
role: Admin
exl-id: 89e54940-e763-4554-8641-a162516bcabd
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 1%

---

# ACSD-50949 : Le filtre de prix dans la recherche avancée ne renvoie pas de résultats corrects lorsqu’il est utilisé avec le filtre SKU.

Le correctif ACSD-50949 corrige le problème en raison duquel le filtre de prix dans la recherche avancée ne renvoyait pas de résultats appropriés lorsqu’il était utilisé avec le filtre SKU. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 est installé. L’ID de correctif est ACSD-50949. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr>). Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Problème

Le filtre de prix dans la recherche avancée ne renvoie pas les résultats appropriés lorsqu’il est utilisé avec le filtre SKU.

<u>Étapes à reproduire</u> :

1. Créez plusieurs produits, par exemple :

   | SKU | Nom | Prix | Quantité |
   |-----|-----------|-------|----------|
   | MJ1 | Produit 1 | 10 $ | 10 |
   | MJ2 | Product 2 | 15 $ | 10 |
   | MJ3 | Product 3 | 21 $ | 10 |
   | MJ4 | Product 4 | 32 $ | 10 |
   | MJ5 | Product 5 | 33 $ | 10 |
   | MJ6 | Product 6 | 34 $ | 10 |
   | MJ7 | Product 7 | 44 $ | 10 |

1. Ouvrez le **[!UICONTROL Advanced Search]** sur Storefront et effectuez une recherche par SKU : &quot;MJ&quot;.
1. Cliquez sur le lien **[!UICONTROL Modify your search]** .
1. Ajoutez une plage de prix aux critères de *1* à *21*, puis cliquez sur le bouton **[!UICONTROL Search]**.

<u>Résultats attendus</u> :

Seuls les produits dont les prix sont compris dans la plage définie sont renvoyés.

<u>Résultats réels</u> :

Les produits dont les prix sont supérieurs à *$21* sont renvoyés.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr>) dans le guide [!DNL Quality Patches Tool].
