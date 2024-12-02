---
title: 'ACSD-60632 : adresse enregistrée avec chaque tentative de commande'
description: Appliquez le correctif ACSD-60632 pour résoudre le problème Adobe Commerce en raison duquel une nouvelle adresse est enregistrée avec chaque tentative de placement de commande, que la commande ait été créée ou non avec succès.
feature: Orders, Products
role: Admin, Developer
exl-id: 9b623a1c-594f-47ed-82b4-d11ba20f3a58
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-60632 : adresse enregistrée avec chaque tentative de commande

Le correctif ACSD-60632 corrige le problème d’enregistrement d’une nouvelle adresse à chaque tentative de placement de commande, que la commande ait été créée ou non avec succès. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 est installé. L’ID de correctif est ACSD-60632. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p8 - 2.4.7-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Chaque fois qu’un emplacement de commande est tenté, une nouvelle entrée d’adresse est enregistrée dans le système, que la commande ait été créée ou non.

<u>Étapes à reproduire</u> :

1. Activez le mode de paiement **[!DNL PayPal Payflow Link]** :
   * Sur un ordinateur local, le système ne peut pas recevoir d’appels d’API de [!DNL PayPal Payflow Link] sans une adresse IP réelle.
1. Créez un produit simple.
1. Créez un client enregistré sans adresse.
1. Ajoutez le produit au panier.
1. Passez à la Passage en caisse.
1. Renseignez l&#39;adresse. Vérifiez que la première adresse est créée à cette étape.
1. Sur la page *[!UICONTROL Review and Payments]*, sélectionnez le bouton radio **[!UICONTROL Credit Card (Payflow Link)]**.
1. Cliquez sur **[!UICONTROL Continue]** :
   * La page de passage en caisse revient à l’étape *[!UICONTROL Review and Payments]* avec l’adresse prérenseignée et le message d’erreur attendu.
1. Sélectionnez à nouveau le bouton radio *[!UICONTROL Credit Card (Payflow Link)]*.
1. Cliquez sur **[!UICONTROL Continue]**.

<u>Résultats attendus</u> :

Une nouvelle adresse n’est pas créée lors de la deuxième tentative de placement de commande.

<u>Résultats réels</u> :

Une nouvelle adresse est créée après chaque tentative de placement de commande.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
