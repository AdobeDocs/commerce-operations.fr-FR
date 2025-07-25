---
title: 'ACSD-44591 : erreurs lors de la commande sans confirmation CAPTCHA'
description: Le correctif ACSD-44591 résout le problème où l'utilisateur obtient des erreurs lors de la tentative de passer une commande sans confirmation CAPTCHA.
feature: Orders
role: Admin
exl-id: 4b8a8090-a2ba-428c-9a04-7c0842e94a6f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-44591 : erreurs lors de la commande sans confirmation CAPTCHA

Le correctif ACSD-44591 résout le problème où l&#39;utilisateur obtient des erreurs lors de la tentative de passer une commande sans confirmation CAPTCHA.
Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID du correctif est ACSD-44591. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur reçoit des erreurs lors de la tentative de passation d’une commande sans confirmation CAPTCHA.

<u>Procédure à suivre </u> :

1. Configurez le Google ReCaptcha v2 (je ne suis pas un robot).
1. Activez ReCaptcha pour l’extraction.
1. Essayez de passer une commande sans cliquer sur le reCaptcha.
1. Une fois que vous recevez le message d’erreur concernant un ReCaptcha manquant (*la validation de ReCaptcha a échoué, veuillez réessayer*), cliquez sur **ReCaptcha** puis essayez de passer une commande.

<u>Résultats attendus</u> :

La commande ne sera pas passée avec un ReCaptcha incorrect.

<u>Résultats réels</u> :

Vous obtenez les erreurs suivantes :

* Échec de la validation de *ReCaptcha). Réessayez*
* *Aucun panier de ce type avec l’ID = 1*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
