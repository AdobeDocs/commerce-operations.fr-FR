---
title: 'MDVA-38827 : les clients reçoivent une erreur d’expédition de commande par e-mail'
description: 'Le correctif MDVA-38827 corrige le problème de réception par les clients d''un e-mail de livraison de commande contenant le message d''erreur suivant : *Nous sommes désolés, une erreur s''est produite lors de la génération de ce contenu*. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 est installé. L’ID du correctif est MDVA-38827. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.'
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ab522c9c-2983-4c2f-b341-4487bdbee34d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-38827 : les clients reçoivent une erreur d’expédition de commande par e-mail

Le correctif MDVA-38827 corrige le problème où les clients reçoivent un email d&#39;expédition de commande contenant le message d&#39;erreur suivant : *Nous sommes désolés, une erreur s&#39;est produite lors de la génération de ce contenu*. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 est installé. L’ID du correctif est MDVA-38827. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque l’option Notifier les clients par e-mail pour l’expédition est sélectionnée, les clients reçoivent un e-mail contenant le message d’erreur suivant : *Nous sommes désolés, une erreur s’est produite lors de la génération de ce contenu*.

<u>Procédure à suivre </u> :

1. Accédez à **Marketing** > **Communications** > **Modèles d’e-mail** et sélectionnez **Ajouter un nouveau modèle**.
   * Sélectionnez **Ventes Magento** > **Nouvelle expédition**.
   * Cliquez sur **Charger le modèle**.
   * Ajoutez un nom de modèle (par exemple, Modèle d&#39;expédition principal) et cliquez sur **Enregistrer**.
1. Accédez à **Boutique** > Paramètres > **Configuration** > **Ventes** > **E-mail de vente** :
   * Activez **Commentaires d&#39;expédition**.
   * Sélectionnez **Modèle d&#39;expédition principal** (reportez-vous à la partie « Ajouter un nom de modèle » de l&#39;étape 1) sous Modèle d&#39;e-mail de commentaire d&#39;expédition et Modèle d&#39;e-mail de commentaire d&#39;expédition pour les invités.
1. Passer une commande. Accédez au panneau d’administration > **Ventes** > **Commande**, cliquez sur **Afficher**, puis expédiez la commande.
1. L’état de la commande passe de En attente à Traitement.
1. Cliquez sur **Expéditions** dans le menu de la barre latérale gauche, puis sur **Afficher** pour afficher la commande.
1. Ajoutez un commentaire dans **Texte du commentaire** ci-dessous **Historique des expéditions** et cochez la case **Notifier le client par e-mail**.
1. Cliquez sur **Envoyer un commentaire**.

<u>Résultats attendus</u> :

Un e-mail de vente contenant des commentaires sur l’expédition est généré.

<u>Résultats réels</u> :

Le message d’erreur suivant est reçu dans l’e-mail : *Nous sommes désolés, une erreur s’est produite lors de la génération de ce contenu.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
