---
title: 'ACSD-54472 : les clients d’une société refusée peuvent toujours s’authentifier.'
description: Appliquez le correctif ACSD-54472 pour résoudre le problème Adobe Commerce en raison duquel les clients d’une société rejetée peuvent toujours s’authentifier, et les clients d’une société bloquée et rejetée peuvent toujours passer des commandes.
feature: B2B
role: Admin, Developer
exl-id: c0bd960f-609b-4253-9fc8-dc47fbbddc93
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-54472 : les clients d’une société refusée peuvent toujours s’authentifier.

Le correctif ACSD-54472 corrige le problème en raison duquel les clients d’une société rejetée peuvent toujours s’authentifier, et les clients d’une société bloquée et rejetée peuvent toujours passer des commandes. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 est installé. L’ID de correctif est ACSD-54472. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les clients d’une société refusée peuvent toujours s’authentifier, et les clients d’une société bloquée et rejetée peuvent toujours passer des commandes.

<u>Étapes à reproduire</u> :

1. Créez une société.
1. Ajoutez des produits au panier via [!DNL GraphQL].
1. Définissez l’état de la société sur *Blocked*.
1. Envoyez une requête [!DNL GraphQL] pour passer la commande et créer un guillemet négociable.
1. Définissez l’état de la société sur *Rejected*.
1. Envoyez une requête [!DNL GraphQL] pour obtenir le jeton d’autorisation utilisateur de l’entreprise.
1. Définissez l’état du client sur *Inactif*.
1. Envoyez une requête [!DNL GraphQL] pour obtenir le jeton d’autorisation utilisateur de l’entreprise.

<u>Résultats attendus</u> :

* La commande et le guillemet négociable ne sont pas placés par l’utilisateur de la société *Blocked*.
* Le jeton d’autorisation n’est pas obtenu pour l’utilisateur de la société *Rejected*.
* Le jeton d’autorisation n’est pas obtenu pour le client *Inactive*.

<u>Résultats réels</u> :

* La commande et le guillemet négociable sont placés par l’utilisateur de la société *Blocked*.
* Le jeton d’autorisation est obtenu pour l’utilisateur de la société *Rejected*.
* Le jeton d’autorisation est obtenu pour le client *Inactive*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
