---
title: 'ACSD-60632 : adresse enregistrée à chaque tentative de commande'
description: Appliquez le correctif ACSD-60632 pour résoudre le problème d’Adobe Commerce où une nouvelle adresse est enregistrée à chaque tentative de passage de commande, que la commande soit créée avec succès ou non.
feature: Orders, Products
role: Admin, Developer
exl-id: 9b623a1c-594f-47ed-82b4-d11ba20f3a58
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-60632 : adresse enregistrée à chaque tentative de commande

Le correctif ACSD-60632 corrige le problème où une nouvelle adresse est enregistrée à chaque tentative de placement de commande, que la commande soit créée avec succès ou non. Ce correctif est disponible lorsque la version 1.1.51 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-60632. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p8 - 2.4.7-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Chaque fois qu’un placement de commande est tenté, une nouvelle entrée d’adresse est enregistrée dans le système, que la commande soit créée ou non.

<u>Procédure à suivre </u> :

1. Activer **[!DNL PayPal Payflow Link]** mode de paiement :
   * Sur un ordinateur local, le système ne peut pas recevoir d’appels API de [!DNL PayPal Payflow Link] sans adresse IP réelle.
1. Créez un produit simple.
1. Créez un client enregistré sans adresse.
1. Ajoutez le produit au panier.
1. Passer en caisse.
1. Renseignez l&#39;adresse. Assurez-vous que la première adresse est créée à cette étape.
1. Sur la page *[!UICONTROL Review and Payments]*, sélectionnez le bouton radio **[!UICONTROL Credit Card (Payflow Link)]**.
1. Cliquez **[!UICONTROL Continue]** :
   * La page de passage en caisse revient à l’étape *[!UICONTROL Review and Payments]* avec l’adresse préremplie et le message d’erreur attendu.
1. Sélectionnez à nouveau *[!UICONTROL Credit Card (Payflow Link)]* bouton radio.
1. Cliquez sur **[!UICONTROL Continue]**.

<u>Résultats attendus</u> :

Aucune nouvelle adresse n&#39;est créée lors de la deuxième tentative de placement de commande.

<u>Résultats réels</u> :

Une nouvelle adresse est créée après chaque tentative de placement de commande.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
