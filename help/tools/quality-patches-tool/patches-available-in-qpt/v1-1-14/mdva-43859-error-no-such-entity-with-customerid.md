---
title: 'MDVA-43859 : erreur « Aucune entité de ce type avec customerId = » consignée lors de la suppression d’une connexion client.'
description: Le correctif MDVA-43859 corrige le problème où l’erreur *Aucune entité de ce type avec customerId =* n’est consignée lorsqu’un client supprimé tente de se connecter. Ce correctif est disponible lorsque l’[Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID du correctif est MDVA-43859. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Variables
role: Admin
exl-id: b8451b08-978a-44a2-8664-4369e832423b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# MDVA-43859 : erreur « Aucune entité de ce type avec customerId = » consignée lors de la suppression d’une connexion client.

Le correctif MDVA-43859 corrige le problème où l’erreur *Aucune entité de ce type avec customerId =* n’est consignée lorsqu’un client supprimé tente de se connecter. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID du correctif est MDVA-43859. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’erreur *Aucune entité de ce type avec customerId =* n’est consignée lorsqu’un client supprimé tente de se connecter.

<u>Procédure à suivre </u> :

1. Créez un compte client à partir du serveur frontal.
1. Déconnectez-vous et connectez-vous au compte client créé à l’étape 1.
1. Chargez le serveur principal dans un autre navigateur et accédez à la grille du client.
1. Supprimez le client créé à l’étape 1.
1. Revenez au premier navigateur et essayez de vous déconnecter.

<u>Résultats attendus</u> :

Le client est redirigé vers la page de connexion sans erreur.

<u>Résultats réels</u> :

Le client reçoit l’erreur suivante : *Aucune entité de ce type avec customerId =*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
