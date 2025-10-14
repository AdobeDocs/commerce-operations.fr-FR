---
title: 'ACSD-65983 : une erreur se produit lors de la reconfiguration du devis de produit groupé dans Admin'
description: Appliquez le correctif ACSD-65983 pour résoudre le problème d’Adobe Commerce où une erreur s’affiche lors de la tentative de configuration d’un produit groupé dans l’écran [!UICONTROL Sales] > [!UICONTROL Quotes] > [!UICONTROL Edit] sur le serveur principal.
feature: B2B, Quotes
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a8f2b273bcbcf135677ad7ca289398bf660e02e
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---


# ACSD-65983 : une erreur se produit lors de la reconfiguration du devis de produit groupé dans Admin

Le correctif ACSD-65983 corrige le problème où la reconfiguration d’un devis de produit groupé dans le serveur principal d’administration renvoie une erreur. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65983. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La reconfiguration d’un devis de produit groupé dans le serveur principal d’administration renvoie une erreur.

<u>Procédure à suivre </u> :

1. Accédez au panneau d’administration et activez le **[!UICONTROL B2B Feature]** : **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Feature]**.
1. Créez une offre groupée avec un montant fixe (par exemple : *$10*) et ajoutez trois produits simples ou plus avec un montant de *0*, *2* dans **Option 1** et *autre* dans **Option 2**.
1. Créez un compte d’entreprise à partir du serveur frontal.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]**, affectez la société et les produits créés au catalogue partagé nouveau/personnalisé.
1. Connectez-vous en tant qu’**utilisateur d’entreprise** sur le serveur frontal et ajoutez un produit simple au panier à partir du lot.
1. Ouvrez la page du panier et effectuez un envoi en tant que **Demander un devis**.
1. Accédez au serveur principal et modifiez le devis créé.
1. Dans la section **Citation**, cliquez sur le bouton **Configurer**.
1. Sélectionnez un autre produit simple dans l’**Option 2**.
1. Cliquez maintenant sur le bouton **OK** et le message d’erreur s’affiche.

<u>Résultats attendus</u> :

Normalement, vous pouvez configurer les éléments de devis demandés à partir de l&#39;administrateur, sans message d&#39;erreur affiché.

<u>Résultats réels</u> :

Le message d’erreur suivant s’affiche :

*Un problème technique du serveur a provoqué une erreur. Réessayez pour continuer ce que vous étiez en train de faire. Si le problème persiste, réessayez plus tard.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [&#x200B; Mises à niveau et correctifs > Appliquer des correctifs &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
