---
title: 'MDVA-42326 : les clients reçoivent une erreur lors du passage en caisse après la temporisation de la session'
description: Le correctif MDVA-42326 résout le problème où les clients obtiennent une erreur lors du passage en caisse après la temporisation de la session, même si le panier persistant est activé. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 est installé. L’ID du correctif est MDVA-42326. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Checkout, Orders
role: Admin
exl-id: f9ef6778-298b-4ff9-9c4b-b3f47bb04b67
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%
---
# MDVA-42326 : les clients reçoivent une erreur lors du passage en caisse après la temporisation de la session

Le correctif MDVA-42326 résout le problème où les clients obtiennent une erreur lors du passage en caisse après la temporisation de la session, même si le panier persistant est activé. Ce correctif est disponible lors de l’installation de l’outil [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) version 1.1.8. L’ID du correctif est MDVA-42326. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les clients reçoivent une erreur lors du passage en caisse après la temporisation de la session, même si le panier persistant est activé.

<u>Conditions préalables</u> :

1. Accédez à **Configuration** > **Général** > **Web** > **Paramètres de cookie par défaut** > **Durée de vie des cookies** et définissez sur **120**.
1. Accédez à **Configuration** > **Clients** > **Configuration client** > **Options des clients en ligne** et définissez les deux valeurs sur **2**.
1. Accédez à **Configuration** > **Clients** > **Panier persistant** et définissez sur **Activer**.
1. Accédez à **Config** > **Ventes** > **Modes de paiement** et désactivez tous les modes de paiement à l’exception de **Chèque/mandat** (cela doit être activé).

<u>Procédure à suivre </u> :

1. Connectez-vous en tant que client et ajoutez quelques produits au panier.
1. Vérifiez le panier.
1. Patientez deux minutes (défini dans les conditions préalables) ; la session doit expirer.
1. Cliquez sur **Accéder à l’extraction** et n’actualisez pas la page.
1. Effectuez la commande en tant qu&#39;invité, indiquez l&#39;adresse de livraison et choisissez une méthode de livraison.
1. Cliquez sur **Suivant**.
1. Sur la page **Vérification et paiements**, cliquez sur **Passer une commande**. Étant donné qu&#39;un seul mode de paiement est autorisé, le client devrait pouvoir passer la commande sans sélectionner le mode de paiement.

<u>Résultats attendus</u> :

Le client doit pouvoir passer la commande.

<u>Résultats réels</u> :

Le client ou la cliente reçoit l’erreur suivante : *Échec de la validation de l’adresse : le format de l’e-mail est incorrect*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
