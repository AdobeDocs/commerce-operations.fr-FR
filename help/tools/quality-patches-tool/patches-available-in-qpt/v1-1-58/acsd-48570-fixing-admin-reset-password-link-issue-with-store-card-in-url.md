---
title: 'ACSD-48570 : correction du problème de lien de réinitialisation du mot de passe de l’administrateur avec le code de magasin dans l’URL'
description: Appliquez le correctif ACSD-48570 pour résoudre le problème d’Adobe Commerce en raison duquel la page de réinitialisation du mot de passe n’était pas accessible via le lien Admin reset password lorsque la configuration de [!UICONTROL Add Store Code to URLs] était activée.
feature: Security, User Account
role: Admin, Developer
exl-id: 049a82ff-80e3-46a1-8472-ac74de0e365f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48570 : correction du problème de lien de réinitialisation du mot de passe de l’administrateur avec le code de magasin dans l’URL

Correctif ACSD-48570 pour résoudre le problème d’Adobe Commerce en raison duquel la page de réinitialisation du mot de passe n’était pas accessible via le lien Admin reset password lorsque la configuration de *[!UICONTROL Add Store Code to URLs]* était activée. Ce correctif est disponible lorsque la version 1.1.58 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-48570. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque le paramètre **[!UICONTROL Add Store Code to URLs]** est activé, la fonctionnalité de réinitialisation du mot de passe de l’administrateur ne fonctionne pas correctement.
Lorsqu’un utilisateur administrateur demande une réinitialisation de mot de passe et clique sur le lien de récupération dans l’e-mail, il est redirigé vers la page de connexion ou reçoit une erreur 404 au lieu d’être redirigé vers le formulaire de réinitialisation de mot de passe. Cela empêche les administrateurs de récupérer leurs comptes sans intervention manuelle.

<u>Procédure à suivre </u> :

1. Activez la configuration **[!UICONTROL Add Store Code to URLs]** sous **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL URL Options]**.
1. Déconnectez-vous du panneau d’administration et cliquez sur le lien **[!UICONTROL Forgot your password?]** sur la page de connexion d’administration.
1. Saisissez l’adresse e-mail de l’utilisateur administrateur, transmettez le captcha, puis cliquez sur **[!UICONTROL Retrieve Password]**.
1. Ouvrez l’e-mail de réinitialisation de mot de passe et cliquez sur le lien de récupération du mot de passe.

<u>Résultats attendus</u> :

Le formulaire de réinitialisation du mot de passe doit s’afficher.

<u>Résultats réels</u> :

La page de connexion ou une page d’erreur 404 s’affiche à la place du formulaire de réinitialisation du mot de passe.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
