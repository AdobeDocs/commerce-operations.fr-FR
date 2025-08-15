---
title: 'ACSD-43887 : détails incorrects affichés sur la page de paiement de la commande'
description: Le correctif ACSD-43887 corrige le problème d’affichage de détails incorrects sur la page de paiement de la commande lorsque les bons de commande pour les entreprises sont activés. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID du correctif est ACSD-43887. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
exl-id: e150f093-9f1a-4ba5-bdcf-90e7f42a29c3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# ACSD-43887 : détails incorrects affichés sur la page de paiement de la commande

Le correctif ACSD-43887 corrige le problème d’affichage de détails incorrects sur la page de paiement de la commande lorsque les bons de commande pour les entreprises sont activés. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID du correctif est ACSD-43887. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Des détails incorrects s’affichent sur la page de paiement de la commande lorsque les commandes fournisseur pour les sociétés sont activées.

<u>Conditions préalables</u> :

1. Les modules B2B sont installés.
1. Activer la société est défini sur _Oui_. Accédez à **Magasins** > **Configurations** > **Général** > **Fonctionnalités B2B** > **Activer la société** > **Yes**.
1. Activer les commandes fournisseur est défini sur _Oui_. Accédez à **Configuration de l&#39;approbation des commandes** > **Activer les commandes** > **Oui**.
1. PayPal Express est configuré comme mode de paiement.

<u>Procédure à suivre </u> :

1. Créez un produit virtuel.
1. Enregistrez un compte d’entreprise du serveur frontal auprès d’un administrateur d’entreprise.
1. Approuvez le compte de la société à partir du serveur principal et définissez **Activer les commandes** sur _Oui_ lors de l&#39;approbation de la société.
1. Accédez au serveur frontal et connectez-vous à l’aide du compte administrateur de la société créé à l’étape 2.
1. Créez un « utilisateur par défaut » pour la société. Accédez à **Utilisateur de la société** > **Ajouter un nouvel utilisateur**.
1. Créez une « Règle d’approbation » pour la société. Accédez à **Règles d’approbation** > **Ajouter une nouvelle règle**.

   * Type de règle : Total de la commande
   * Total de la commande : est supérieur ou égal à 1 $
   * Nécessite l&#39;approbation de : Administrateur d&#39;entreprise

1. Déconnectez-vous et connectez-vous à l’aide du compte « Utilisateur par défaut ».
1. Ajoutez au panier le produit virtuel créé à l’étape 1 et passez en caisse.
1. Sélectionnez PayPal Express comme mode de paiement et cliquez sur **Passer commande**.
1. Déconnectez-vous et connectez-vous à l’aide du compte administrateur de la société.
1. Accédez à **Mes commandes** et dans **Commandes d’entreprise**, cliquez sur **Afficher** pour la commande créée à l’étape 9.
1. Validez la commande fournisseur. Le statut de la commande fournisseur doit être « Approuvé : Paiement en attente ».
1. Déconnectez-vous et connectez-vous à l’aide du compte « Utilisateur par défaut » de l’entreprise.
1. Accédez à **Mes commandes** > **Afficher** > **Passer une commande**.
1. Vérifiez le **récapitulatif de la commande**.

<u>Résultats attendus</u> :

La synthèse des commandes affiche des valeurs correctes non nulles.

<u>Résultats réels</u> :

La valeur totale du résumé de la commande est zéro.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
