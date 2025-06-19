---
title: 'ACSD-54472 : les clients d’une société rejetée peuvent toujours s’authentifier'
description: Appliquez le correctif ACSD-54472 pour résoudre le problème d’Adobe Commerce où les clients d’une société refusée peuvent toujours s’authentifier et où les clients d’une société bloquée et refusée peuvent toujours passer des commandes.
feature: B2B
role: Admin, Developer
exl-id: c0bd960f-609b-4253-9fc8-dc47fbbddc93
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-54472 : les clients d’une société rejetée peuvent toujours s’authentifier

Le correctif ACSD-54472 corrige le problème en raison duquel les clients d’une société refusée peuvent toujours s’authentifier, et les clients d’une société bloquée et refusée peuvent toujours passer des commandes. Ce correctif est disponible lorsque la version 1.1.40 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54472. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les clients d’une société refusée peuvent toujours s’authentifier, et les clients d’une société bloquée et refusée peuvent toujours passer des commandes.

<u>Procédure à suivre </u> :

1. Créez une entreprise.
1. Ajoutez des produits au panier via [!DNL GraphQL].
1. Remplacez le statut de la société par *Bloqué*.
1. Envoyez une demande de [!DNL GraphQL] pour passer la commande et créer un devis négociable.
1. Remplacez le statut de la société par *Refusé*.
1. Envoyez une demande de [!DNL GraphQL] pour obtenir le jeton d’autorisation utilisateur de l’entreprise.
1. Définissez le statut du client sur *Inactif*.
1. Envoyez une demande de [!DNL GraphQL] pour obtenir le jeton d’autorisation utilisateur de l’entreprise.

<u>Résultats attendus</u> :

* La commande et le devis négociable ne sont pas passés par l&#39;utilisateur de la société *Bloquée*.
* Le jeton d’autorisation n’est pas obtenu pour l’utilisateur de la société *Refusé*.
* Le jeton d’autorisation n’est pas obtenu pour le client *Inactif*.

<u>Résultats réels</u> :

* La commande et le devis négociable sont passés par l&#39;utilisateur de la société *Bloquée*.
* Le jeton d’autorisation est obtenu pour l’utilisateur de la société *Refusé*.
* Obtention du jeton d’autorisation pour le client *Inactif*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
