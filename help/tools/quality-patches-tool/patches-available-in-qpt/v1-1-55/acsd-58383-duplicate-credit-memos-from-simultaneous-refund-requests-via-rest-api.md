---
title: 'ACSD-58383 : dupliquer des avoirs à partir de demandes de remboursement simultanées via  [!DNL REST API]'
description: Appliquez le correctif ACSD-58383 pour résoudre le problème d’Adobe Commerce en raison duquel l’émission d’un remboursement via le avec deux demandes identiques exécutées simultanément crée  [!DNL REST API]  avoirs en double.
feature: REST, Payments, Returns
role: Admin, Developer
exl-id: 962970d5-22e7-4bdc-afa0-70e1fa21ecec
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-58383 : dupliquer des avoirs à partir de demandes de remboursement simultanées via [!DNL REST API]

Le correctif ACSD-58383 corrige le problème en raison duquel l’émission d’un remboursement via le [!DNL REST API] avec deux demandes identiques exécutées simultanément entraîne des avoirs en double.

Ce correctif est disponible lorsque la version 1.1.55 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-58383. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les avoirs en double résultent de deux remboursements créés simultanément.

<u>Procédure à suivre </u> :

1. Configurez [!DNL Paypal Express] dans le [!UICONTROL Admin] Commerce.
1. Définissez l&#39;action de paiement sur *Vente*.
1. Configurez l’[!DNL PayPal] IPN (Instant Payment Notification) sur le site web [!DNL PayPal] Sandbox.
1. Émettez un remboursement sur le site Web [!DNL PayPal] Sandbox.
1. Émulez un message IPN à partir de [!DNL PayPal] à l’aide d’outils de développement. IPN doit créer un avoir.
1. Créez un deuxième avoir à l&#39;aide d&#39;un appel [!DNL API].

<u>Résultats attendus</u> :

Un seul avoir est créé pour le même article.


<u>Résultats réels</u> :

Deux avoirs sont créés pour le même article.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
