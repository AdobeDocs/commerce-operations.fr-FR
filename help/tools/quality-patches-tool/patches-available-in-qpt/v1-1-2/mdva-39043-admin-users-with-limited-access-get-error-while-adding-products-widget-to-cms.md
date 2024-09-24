---
title: "MDVA-39043 : les utilisateurs administrateurs reçoivent une erreur lors de l’ajout d’un widget à la page CMS"
description: Le correctif MDVA-39043 corrige le problème en raison duquel les utilisateurs administrateurs disposant d’un accès limité obtiennent une erreur lors de l’ajout du widget "Produits" à la page CMS. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID de correctif est MDVA-39043. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: Admin Workspace, CMS, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-39043 : les utilisateurs administrateurs reçoivent une erreur lors de l’ajout du widget à la page CMS.

Le correctif MDVA-39043 corrige le problème en raison duquel les utilisateurs administrateurs disposant d’un accès limité obtiennent une erreur lors de l’ajout du widget &quot;Produits&quot; à la page CMS. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID de correctif est MDVA-39043. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs administrateurs disposant d’un accès limité reçoivent une erreur lors de l’ajout du widget &quot;Produits&quot; à la page CMS.

<u>Étapes à reproduire</u> :

1. Connectez-vous au serveur principal à l’aide de l’administrateur avec accès uniquement pour modifier le contenu.
1. Accédez à **Contenu** > **Pages**.
1. Ouvrez une page à modifier.
1. Modifiez le contenu avec **Page Builder**.
1. Ajoutez le widget **Product** de la section **Ajouter du contenu** .
1. Cliquez sur **Configurer** sur le widget **Produit** .

<u>Résultats attendus</u> :

Aucune erreur ne s’affiche.

<u>Résultats réels</u> :

Le message d’erreur suivant est reçu :

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
