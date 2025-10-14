---
title: 'ACSD-56858 : incohérence des autorisations de rôle dans l’administration d’entreprise B2B'
description: Appliquez le correctif ACSD-56858 pour résoudre le problème d’Adobe Commerce où les autorisations de rôle s’affichent incorrectement pour un administrateur d’entreprise restreint dans l’environnement B2B.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: 28f90c8b-5d8b-4444-99ef-c91cfb5d6081
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-56858 : incohérence des autorisations de rôle dans l’administration d’entreprise B2B

Le correctif ACSD-56858 corrige le problème d’affichage incorrect des autorisations de rôle pour un administrateur d’entreprise restreint dans l’environnement B2B. Ce correctif est disponible lorsque la version 1.1.47 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-56858. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les autorisations de rôle pour un administrateur d’entreprise restreint dans l’environnement B2B s’affichent de manière incorrecte.

<u>Procédure à suivre </u> :

1. Commencez par configurer une entreprise, en ajoutant un administrateur d’entreprise et des utilisateurs d’entreprise.
1. Connectez-vous en tant qu’administrateur d’entreprise sur le storefront et créez différents rôles pour différents utilisateurs.
1. Attribuez ces rôles selon les besoins, par exemple en limitant l’accès à certaines tâches tout en autorisant un accès complet à d’autres.
1. Attribuez ces rôles avec un accès complet à un utilisateur autre que l’administrateur de la société.
1. Connectez-vous à un utilisateur administrateur qui n’est pas une entreprise, par exemple un company_manager.
1. Accédez à **[!UICONTROL Roles and permission]** et modifiez le rôle.
1. Notez que les autorisations affichées ne correspondent pas aux autorisations définies dans la base de données de l’entreprise pour cet ID de rôle.

<u>Résultats attendus</u> :

Les rôles et les autorisations s’affichent correctement pour l’utilisateur administrateur non-société.

<u>Résultats réels</u> :

Les rôles ne s’affichent pas correctement pour l’utilisateur administrateur non-société d’après les enregistrements de base de données dans la table des autorisations.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [&#x200B; Mises à niveau et correctifs > Appliquer des correctifs &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool]
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
