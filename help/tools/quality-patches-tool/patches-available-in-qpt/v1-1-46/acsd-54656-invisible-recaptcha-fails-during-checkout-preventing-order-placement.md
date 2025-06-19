---
title: Invisible [!DNL reCAPTCHA] échoue lors du passage en caisse, ce qui empêche le placement de la commande
description: Appliquez le correctif ACSD-54656 pour résoudre le problème d’Adobe Commerce en raison duquel l [!DNL reCAPTCHA] invisible ne fonctionne pas correctement lors de l’extraction, ce qui empêche le placement d’une commande.
feature: Checkout, Gift
role: Admin, Developer
exl-id: 08850189-2e1b-4132-8d63-ce447b1f1211
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-54656 : le [!DNL reCAPTCHA] invisible ne fonctionne pas correctement lors de l’extraction, ce qui empêche le placement d’une commande.

Le correctif ACSD-54656 corrige le problème en raison duquel le [!DNL reCAPTCHA] invisible ne fonctionne pas correctement lors du passage en caisse, ce qui empêche le placement d’une commande. Ce correctif est disponible lorsque la version 1.1.46 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54656. Notez que le problème a été résolu dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le [!DNL reCAPTCHA] invisible ne fonctionne pas correctement lors de l’extraction, ce qui empêche le placement d’une commande.

<u>Procédure à suivre </u> :

1. Activez n’importe quel type de [!DNL reCAPTCHA] pour la carte cadeau sur la page [!UICONTROL Checkout].
1. Ajoutez le produit au panier et accédez à la page **[!UICONTROL Checkout]**.
1. Développez le formulaire de carte cadeau et remplissez un coupon de carte cadeau valide.
1. Cliquez sur **[!UICONTROL See balance and apply]** bouton.

<u>Résultats attendus</u> :

La carte cadeau a été appliquée.

<u>Résultats réels</u> :

Un message d’erreur s’affiche : échec de la validation du *[!DNL reCAPTCHA]. Réessayez*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
