---
title: 'ACSD-48773 : modèle d’e-mail de points de récompense provenant d’un mauvais magasin'
description: Appliquez le correctif ACSD-48773 pour résoudre le problème d’Adobe Commerce où le modèle d’e-mail de points de récompense est extrait du mauvais magasin.
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
exl-id: db8b6196-3e13-4c1b-8ae8-040487180817
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-48773 : modèle d’e-mail de points de récompense provenant d’un mauvais magasin

Le correctif ACSD-48773 corrige le problème en raison duquel le modèle d’e-mail de points de récompense est extrait du mauvais magasin. Ce correctif est disponible lorsque la version 1.1.26 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48773. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La réindexation du prix du produit ne fonctionne pas si le produit groupé n’est affecté à aucun site web.

<u>Procédure à suivre </u> :

1. Créez 2 sites web, 2 magasins et 2 affichages de magasin.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** et activez **[!UICONTROL Reviews]**.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**.
Passez à l’adresse **[!DNL default website scope]** et définissez l’adresse **[!UICONTROL Customer Support Sender Email]**, (par exemple : *support_base@example.com*).
Passez à l’**[!DNL second website scope]** et définissez l’adresse **[!UICONTROL Customer Support Sender Email]** sur une autre valeur (par exemple : *support_second@example.com*).
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]**, puis définissez **[!UICONTROL Share Customer Accounts]** = *Par site web*.
1. Sous **[!UICONTROL Reward Points]**, définissez les éléments suivants :
   **[!UICONTROL Enable Reward Points Functionality]** = *Oui*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *Oui*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** et définir **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** et définir **[!UICONTROL Email Sender]** = *Service clientèle*
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** et configurez les taux de change pour le deuxième site web pour **[!UICONTROL Points/Currency]** et **[!UICONTROL Currency/Points]**.
1. Créez un compte client sur le deuxième site web.
1. Connectez-vous en tant que client sur le deuxième site web.
1. Veillez à activer **[!UICONTROL Subscribe]** pour **[!UICONTROL Balance Updates]**.
1. Soumettre une révision de produit.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**.
1. Modifiez le statut de la nouvelle révision en ***[!UICONTROL Approved]*** et **[!UICONTROL Save]**.
1. Attendez que l’e-mail arrive.

<u>Résultats attendus</u> :

L’e-mail de mise à jour des points de récompense aurait dû être envoyé par l’expéditeur de l’e-mail configuré sur la seconde portée du site web.

<u>Résultats réels</u> :

L’e-mail de mise à jour des points de récompense a été envoyé par l’expéditeur de l’e-mail configuré sur la portée par défaut du site web.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
