---
title: 'ACSD-58383 : Duplication des crédits de demandes de remboursement simultanées via [!DNL REST API]'
description: Appliquez le correctif ACSD-58383 pour corriger le problème Adobe Commerce en raison duquel émettre un remboursement via le  [!DNL REST API] avec deux demandes identiques exécutées simultanément, crée des notes de crédit en double.
feature: REST, Payments, Returns
role: Admin, Developer
exl-id: 962970d5-22e7-4bdc-afa0-70e1fa21ecec
source-git-commit: 28390659fe180180c9b2c8d16239008a1f8a510b
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Correctif Adobe Commerce ACSD-58383 : duplication de crédits de demandes simultanées de remboursement via [!DNL REST API]

Le correctif ACSD-58383 corrige le problème en raison duquel l’émission d’un remboursement via l’ [!DNL REST API] avec deux demandes identiques exécutées simultanément entraîne la duplication de notes de crédit.

Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 est installé. L’ID de correctif est ACSD-58383. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les avoirs en double résultent de deux remboursements créés simultanément.

<u>Étapes à reproduire</u> :

1. Configurez [!DNL Paypal Express] dans Commerce [!UICONTROL Admin].
1. Définissez l’action de paiement sur *Sale*.
1. Configurez l’ [!DNL PayPal] IPN (Instant payment Notification) sur le site web [!DNL PayPal] Sandbox.
1. Remboursement des problèmes sur le site Web [!DNL PayPal] Sandbox.
1. Émulez un message IPN de [!DNL PayPal] à l’aide des outils de développement. IPN doit créer une note de crédit.
1. Créez un second mémo de crédit à l’aide d’un appel [!DNL API].

<u>Résultats attendus</u> :

Une seule note de crédit est créée pour le même article.


<u>Résultats réels</u> :

Deux notes de crédit sont créées pour le même article.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
