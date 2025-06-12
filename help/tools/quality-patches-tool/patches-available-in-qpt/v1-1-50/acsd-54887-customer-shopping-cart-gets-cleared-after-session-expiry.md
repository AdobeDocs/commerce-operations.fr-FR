---
title: 'ACSD-54887 : le panier du client est effacé après expiration de la session du client'
description: Appliquez le correctif ACSD-54887 pour résoudre le problème d’Adobe Commerce en raison duquel le panier du client est effacé après l’expiration de la session client avec le [!UICONTROL Persistent Shopping Cart] activé.
feature: Shopping Cart
role: Admin, Developer
exl-id: de2a96b2-48ce-4b9b-93bc-f7b64c37463a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-54887 : le panier du client est effacé après expiration de la session du client

Le correctif ACSD-54887 corrige le problème d’effacement du panier du client après l’expiration de la session client avec le [!UICONTROL Persistent Shopping Cart] activé. Ce correctif est disponible lorsque la version 1.1.50 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54887. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p8, 2.4.5-p3 - 2.4.5-p7 et 2.4.6-p1 - 2.4.6-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le panier du client est effacé après l’expiration de la session client avec [!UICONTROL Persistent Shopping Cart] activé.

<u>Procédure à suivre </u> :

1. Activez [!UICONTROL Persistent Shopping Cart]. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** = *Oui*.

   Connectez-vous avec la persistance activée (Remarque : elle n’est pas disponible sur l’autorisation de la fenêtre contextuelle, mais uniquement sur la page de [!UICONTROL Sign in] directe).

1. Ajoutez un produit au panier.
1. Passez en caisse et sélectionnez un mode de paiement.
1. Faire expirer la session (supprimer `PHPSESSID`).
1. Actualisez la page. Notez que le devis est immédiatement converti en devis invité car un mode de paiement est déjà sélectionné et le cookie [!UICONTROL Persistent Cart] est supprimé.
1. Faire expirer la session (supprimer `PHPSESSID`).
1. Actualisez la page. Vérifiez que le panier est vide.
1. Reconnectez-vous.

<u>Résultats attendus</u> :

Le panier contient le produit lorsque vous vous reconnectez.

<u>Résultats réels</u> :

Le panier est vide lors d’une nouvelle connexion.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
