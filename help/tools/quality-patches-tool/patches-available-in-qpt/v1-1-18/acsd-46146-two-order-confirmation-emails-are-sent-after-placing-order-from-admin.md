---
title: 'ACSD-46146 : deux e-mails de confirmation de commande envoyés après avoir passé commande auprès de l’administrateur'
description: Le correctif ACSD-46146 résout le problème où deux e-mails de confirmation de commande sont envoyés après avoir passé une commande auprès de l’administrateur. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 est installé. L’ID du correctif est ACSD-46146. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.
feature: Admin Workspace, Communications, Orders
role: Admin
exl-id: 1db809d0-461d-45d4-9e1b-8209a014b7a1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-46146 : deux e-mails de confirmation de commande envoyés après avoir passé commande auprès de l’administrateur

Le correctif ACSD-46146 résout le problème où deux e-mails de confirmation de commande sont envoyés après avoir passé une commande auprès de l’administrateur. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) version 1.1.18 est installé. L’ID du correctif est ACSD-46146. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Deux e-mails de confirmation de commande sont envoyés après avoir passé une commande auprès de l’administrateur.

<u>Procédure à suivre </u> :

1. Ouvrez Commerce Admin > **Ventes** > **Commandes** > **Créer une commande**.
1. Passez une commande avec les paramètres de paiement par défaut (chèque/mandat) et d&#39;expédition (taux forfaitaire).

<u>Résultats attendus</u> :

Un seul email de confirmation de commande est envoyé.

<u>Résultats réels</u> :

Deux e-mails de confirmation de commande sont envoyés après avoir passé une commande auprès de l’administrateur.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
