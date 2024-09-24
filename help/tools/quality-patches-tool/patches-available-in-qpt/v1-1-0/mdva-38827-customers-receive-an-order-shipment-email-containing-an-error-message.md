---
title: 'MDVA-38827 : les clients reçoivent une erreur de livraison de commande par email'
description: "Le correctif MDVA-38827 corrige le problème en raison duquel les clients reçoivent un email d’expédition de commande contenant le message d’erreur suivant : *Nous sommes désolés, une erreur s’est produite lors de la génération de ce contenu*. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0 est installé. L’ID de correctif est MDVA-38827. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4."
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-38827 : les clients reçoivent une erreur d’expédition de commande par courrier électronique

Le correctif MDVA-38827 corrige le problème en raison duquel les clients reçoivent un email d’expédition de commande contenant le message d’erreur suivant : *Nous sommes désolés, une erreur s’est produite lors de la génération de ce contenu*. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0 est installé. L’ID de correctif est MDVA-38827. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque l’option Avertir les clients par courrier électronique pour l’envoi est sélectionnée, les clients reçoivent un courrier électronique contenant le message d’erreur suivant : *Nous sommes désolés, une erreur s’est produite lors de la génération de ce contenu*.

<u>Étapes à reproduire</u> :

1. Accédez à **Marketing** > **Communications** > **Modèles d’e-mail** et sélectionnez **Ajouter un nouveau modèle**.
   * Sélectionnez **Ventes de Magento** > **Nouvel expédition**.
   * Cliquez sur **Charger le modèle**.
   * Ajoutez un nom de modèle (par exemple, modèle d’expédition principal) et cliquez sur **Enregistrer**.
1. Accédez à **Magasin** > Paramètres > **Configuration** > **Ventes** > **Courrier électronique de vente** :
   * Activez **Commentaires d’expédition**.
   * Sélectionnez **Modèle d’expédition principal** (voir la partie &quot;Ajouter un nom de modèle&quot; de l’étape 1) sous Modèle d’email de commentaire d’envoi et Modèle d’email de commentaire d’envoi pour l’invité.
1. passé une commande ; Accédez au panneau d’administration > **Ventes** > **Commande**, cliquez sur **Afficher**, puis envoyez la commande.
1. L’état de la commande passe de En attente à Traitement.
1. Cliquez sur **Expéditions** dans le menu de la barre latérale gauche, puis cliquez sur **Afficher** pour afficher la commande.
1. Ajoutez un commentaire dans **Texte de commentaire** sous **Historique des envois** et cochez la case **Avertir le client par courrier électronique**.
1. Cliquez sur **Submit Comment**.

<u>Résultats attendus</u> :

Un courrier électronique de vente contenant des commentaires d’expédition est généré.

<u>Résultats réels</u> :

Le message d&#39;erreur suivant est reçu dans l&#39;email : *Nous sommes désolés, une erreur s&#39;est produite lors de la génération de ce contenu.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
