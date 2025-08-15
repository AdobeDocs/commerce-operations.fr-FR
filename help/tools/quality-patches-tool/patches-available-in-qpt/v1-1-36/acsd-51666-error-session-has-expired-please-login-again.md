---
title: 'ACSD-51666 : erreur « La session a expiré, veuillez vous reconnecter ». après vous être connecté'
description: Appliquez le correctif ACSD-51666 pour résoudre le problème Adobe Commerce où l’erreur *La session a expiré, veuillez vous reconnecter.* se produit après votre tentative de connexion.
feature: Customers
role: Admin, Developer
exl-id: 8968b314-6625-45fa-9733-20560cca7089
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# ACSD-51666 : erreur *la session a expiré, veuillez vous reconnecter.* après vous être connecté

Le correctif ACSD-51666 corrige le problème où l’erreur *La session a expiré, veuillez vous reconnecter.* se produit après avoir tenté de vous connecter. Ce correctif est disponible lorsque la version 1.1.36 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51666. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le message d’erreur suivant s’affiche *La session a expiré, veuillez vous reconnecter.* lors de la tentative de connexion avec le nouveau mot de passe d’un appareil après la réinitialisation du mot de passe sur un autre appareil. Cela ne se produit que s’il existe une requête Ajax supplémentaire sur la page ajoutée par un module personnalisé.

<u>Procédure à suivre </u> :

1. Installez un module personnalisé qui ajoute une requête Ajax sur chaque page du storefront.
1. Créez un compte.
1. Déconnectez-vous et revenez à la page de connexion.
1. Ouvrez le lien *Mot de passe oublié* dans un autre navigateur et envoyez l’e-mail *Réinitialiser le mot de passe*.
1. Ouvrez l’e-mail de réinitialisation de mot de passe dans le premier navigateur et définissez le nouveau mot de passe.
1. Essayez de vous connecter dans le deuxième navigateur.

<u>Résultats attendus</u> :

La première tentative de connexion réussit.

<u>Résultats réels</u> :

* Le message *La session a expiré, veuillez vous reconnecter.Erreur de*.
* Vous n’êtes pas connecté et redirigé vers la page d’accueil.
* La deuxième tentative de connexion a réussi.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
