---
title: 'ACSD-50949 : le filtre de prix dans la recherche avancée ne renvoie pas les bons résultats lorsqu’il est utilisé avec le filtre de SKU'
description: Appliquez le correctif ACSD-50949 pour résoudre le problème d’Adobe Commerce en raison duquel le filtre de prix dans la recherche avancée ne renvoie pas les résultats appropriés lorsqu’il est utilisé avec le filtre de SKU.
feature: Orders, Search
role: Admin
exl-id: 89e54940-e763-4554-8641-a162516bcabd
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 1%

---

# ACSD-50949 : le filtre Prix dans la recherche avancée ne renvoie pas les bons résultats lorsqu’il est utilisé avec le filtre SKU

Le correctif ACSD-50949 corrige le problème où le filtre de prix dans la recherche avancée ne renvoie pas les bons résultats lorsqu’il est utilisé avec le filtre de SKU. Ce correctif est disponible lorsque la version 1.1.33 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-50949. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Problème

Le filtre de prix dans la recherche avancée ne renvoie pas les bons résultats lorsqu’il est utilisé avec le filtre de SKU.

<u>Procédure à suivre </u> :

1. Créez plusieurs produits, par exemple :

   | SKU | Nom | Prix | Quantité |
   |-----|-----------|-------|----------|
   | MJ1 | Produit 1 | 10 $ | 10 |
   | MJ2 | Produit 2 | 15 $ | 10 |
   | MJ3 | Produit 3 | 21 $ | 10 |
   | MJ4 | Produit 4 | 32 $ | 10 |
   | MJ5 | Produit 5 | 33 $ | 10 |
   | MJ6 | Produit 6 | 34 $ | 10 |
   | MJ7 | Produit 7 | 44 $ | 10 |

1. Ouvrez le **[!UICONTROL Advanced Search]** sur la vitrine et effectuez une recherche par SKU : « MJ ».
1. Cliquez sur le lien **[!UICONTROL Modify your search]**.
1. Ajoutez une plage de prix aux critères de *1* à *21*, puis cliquez sur le bouton **[!UICONTROL Search]**.

<u>Résultats attendus</u> :

Seuls les produits dont les prix se situent dans la plage définie sont renvoyés.

<u>Résultats réels</u> :

Les produits dont les prix sont supérieurs à 21 $** sont retournés.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le guide de [!DNL Quality Patches Tool].
