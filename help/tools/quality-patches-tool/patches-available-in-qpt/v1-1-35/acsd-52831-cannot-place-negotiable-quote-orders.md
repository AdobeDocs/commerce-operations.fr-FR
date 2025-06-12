---
title: 'ACSD-52831 : impossible de passer des ordres de devis négociables lorsqu [!DNL Google reCAPTCHA v3 Invisible] activé'
description: Appliquez le correctif ACSD-52831 pour résoudre le problème Adobe Commerce en raison duquel vous ne pouvez pas passer d'ordres de devis négociables lorsque  [!DNL Google reCAPTCHA v3 Invisible]  est activé.
feature: Quotes, B2B, Checkout
role: Admin
exl-id: fa09e41f-f6c3-4cc7-a814-0e1ac5e9ea2e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-52831 : impossible de passer des ordres de devis négociables lorsqu&#39;[!DNL Google reCAPTCHA v3 Invisible] est activé

Le correctif ACSD-52831 corrige le problème en raison duquel vous ne pouvez pas passer d&#39;ordres de devis négociables lorsque [!DNL Google reCAPTCHA v3 Invisible] est activé. Ce correctif est disponible lorsque la version 1.1.35 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-52831. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Impossible de passer des ordres de devis négociables lorsque [!DNL Google reCAPTCHA v3 Invisible] est activé.

<u>Procédure à suivre </u> :

1. Activez la fonction de devis B2B.
1. Activez [!DNL Google reCAPTCHA v3 Invisible] sur le storefront pour activer le passage en caisse/le placement des commandes.
1. Établir un devis et passer à la caisse avec ce devis.
1. Vous ne pourrez pas passer de commande en raison de l’erreur CAPTCHA.

<u>Résultats attendus</u> :

Le devis passe en caisse.

<u>Résultats réels</u> :

Vous obtenez l’erreur *échec de la validation reCAPTCHA, veuillez réessayer*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
