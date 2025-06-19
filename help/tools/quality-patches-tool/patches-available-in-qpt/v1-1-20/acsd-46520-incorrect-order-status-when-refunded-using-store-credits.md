---
title: 'ACSD-46520 : statut de commande incorrect lors du remboursement à l’aide de crédits de magasin'
description: Cet article fournit une solution au problème où les utilisateurs obtiennent un statut de commande incorrect lorsqu’ils sont remboursés à l’aide de crédits de boutique.
feature: Orders, Returns
role: Admin
exl-id: 67740003-a71e-41bf-afda-ca3e32290115
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-46520 : statut de commande incorrect lors du remboursement à l’aide de crédits de magasin

Le correctif ACSD-46520 résout le problème où les utilisateurs obtiennent un statut de commande incorrect lorsqu&#39;ils sont remboursés à l&#39;aide de crédits de magasin. Ce correctif est disponible lorsque la version 1.1.20 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-46520. Notez que le problème a été résolu dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 et 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs obtiennent un statut de commande incorrect lorsqu’ils sont remboursés à l’aide de crédits de magasin.

<u>Procédure à suivre </u> :

1. Créer un compte client sur le storefront et se connecter.
1. Attribuez des crédits de magasin au client à partir de l’administrateur. Les crédits de magasin doivent couvrir l&#39;ensemble de la commande.
1. Passez une commande en utilisant les crédits du magasin.
1. Facture la commande.
1. Créez un avoir pour rembourser le montant total de la commande.
Cochez la case **[!UICONTROL Refund to store credit]** .
1. Vérifiez le statut de la commande.

<u>Résultats attendus</u> :

Le statut de la commande est *Fermé*.

<u>Résultats réels</u> :

Le statut de la commande est *Terminé*, mais il n’est pas correct.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou [!DNL Magento Open Source] On-premise : [Outils de correctifs de qualité > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de l’outil de correctifs de qualité.
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
