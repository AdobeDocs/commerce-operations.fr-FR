---
title: 'ACSD-49737 : le coupon est incorrectement marqué comme utilisé après un échec de paiement par carte'
description: Appliquez le correctif ACSD-49737 pour résoudre le problème d’Adobe Commerce en raison duquel le coupon est incorrectement marqué comme utilisé après un échec de paiement par carte.
feature: Orders, Payments
role: Admin
exl-id: 09060026-8d64-49f6-a85a-3230a52030fb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49737 : le coupon est incorrectement marqué comme *utilisé* après un échec de paiement par carte

Le correctif ACSD-49737 corrige le problème où le coupon est incorrectement marqué comme *utilisé* après un échec de paiement par carte. Ce correctif est disponible lorsque la version 1.1.30 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-49737. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le coupon est incorrectement marqué comme *utilisé* après un échec de paiement par carte.

<u>Conditions préalables</u> :

1. Configurez la méthode **[!UICONTROL Braintree sandbox payment]** .
1. Assurez-vous que le client [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en) est configuré et en cours d’exécution.

<u>Procédure à suivre </u> :

1. Créez un **[!UICONTROL Cart Price Rule]** avec des codes de coupon générés automatiquement.
1. Connectez-vous en tant que client.
1. Ajoutez un ou plusieurs produits au panier.
1. Appliquez un code de coupon généré automatiquement.
1. Essayez de passer une commande avec un paiement en échec.
1. Vérifiez l’utilisation des coupons dans la **[!UICONTROL Cart Price Rule]** sous l’onglet **[!UICONTROL Manage Coupon Codes]** .

<u>Résultats attendus</u> :

Le coupon ne doit pas être marqué comme *utilisé* si le paiement a échoué.

<u>Résultats réels</u> :

* Le code de coupon indique - Utilisé : *Oui*, Horaires utilisés : *1*
* Le code de coupon n’est valide que pour une utilisation unique.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Étapes supplémentaires requises après l’installation du correctif

(Cette section est facultative ; certaines étapes peuvent être nécessaires après l’application du correctif pour résoudre le problème.) 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
