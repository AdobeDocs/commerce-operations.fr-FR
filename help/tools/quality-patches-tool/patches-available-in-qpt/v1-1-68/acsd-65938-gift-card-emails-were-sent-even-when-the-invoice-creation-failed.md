---
title: 'ACSD-65938 : e-mails de carte cadeau envoyés même lorsque la création de la facture a échoué'
description: Appliquez le correctif ACSD-65938 pour résoudre le problème d’Adobe Commerce en raison duquel des e-mails de carte cadeau ont été envoyés avant que la facture ne soit enregistrée et validée, en veillant à ce que les e-mails soient déclenchés une fois la facture correctement enregistrée.
feature: Orders, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: b688875cd0a7bfc07dba77254605e7055ae7cca4
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# ACSD-65938 : e-mails de carte cadeau envoyés même lorsque la création de la facture a échoué

Le correctif ACSD-65938 résout un problème en raison duquel des e-mails de carte cadeau étaient envoyés avant que la facture ne soit enregistrée et validée. Avec ce correctif, les e-mails ne sont désormais déclenchés qu’une fois la facture enregistrée avec succès. Ce correctif est disponible lorsque la version 1.1.68 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65938. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Des e-mails de carte cadeau ont été envoyés avant de confirmer que la facture a bien été créée et enregistrée, ce qui entraîne l’envoi d’e-mails même lorsque la création de la facture a échoué.

<u>Procédure à suivre </u> :

1. Connectez-vous au panneau **[!UICONTROL Admin]**.
2. Accédez à **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Cards]** > **[!UICONTROL Gift Card General Settings]**, puis définissez **[!UICONTROL Generate Gift Card Account when Order Item is]** sur *Facturé*.
3. Créez un nouveau produit de carte cadeau.
4. Ajoutez un produit de panier cadeau au panier et passez à l’**[!UICONTROL checkout]**. Vous pouvez utiliser **[!UICONTROL Check/Money Order]** comme mode de paiement.
5. Passez la commande.
6. Modifiez le `OrderRepository` pour simuler une exception lors du placement de la commande.
7. Envoyez une requête POST à `rest/default/V1/order/<ORDER_ID>/invoice` avec la payload suivante :

   ```
   {
     "capture": true,
     "notify": true
   }
   ```


<u>Résultats attendus</u> :

Aucun e-mail de carte cadeau ne doit être envoyé si la création de facture échoue.

<u>Résultats réels</u> :

L’e-mail de carte cadeau est envoyé même si la création de la facture a échoué.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
