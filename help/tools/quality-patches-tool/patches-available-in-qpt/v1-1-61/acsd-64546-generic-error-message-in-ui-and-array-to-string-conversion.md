---
title: 'ACSD-64546 : message d’erreur générique dans l’interface utilisateur et exception de conversion de tableau en chaîne lors de la création de l’étiquette UPS'
description: Appliquez le correctif ACSD-64546 pour résoudre le problème Adobe Commerce où un message d’erreur générique apparaît dans l’interface utilisateur et où l’exception de conversion de tableau en chaîne est enregistrée lors de la création de l’étiquette UPS. Le correctif garantit que l’erreur correcte est affichée dans l’interface utilisateur et les journaux.
feature: Shipping/Delivery
role: Admin, Developer
source-git-commit: f50da09cec35b3a72208f17b6832e3068de9c874
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---


# ACSD-64546 : Message d’erreur générique dans l’interface utilisateur et *exception de conversion* de tableau en chaîne lors de la création d’étiquettes UPS

Le correctif ACSD-64546 corrige le problème où un message d’erreur générique s’affiche dans l’interface utilisateur et où l’exception *Conversion de tableau en chaîne* est consignée lors de la création du libellé de l’onduleur, en s’assurant que l’erreur correcte s’affiche dans l’interface utilisateur et dans les journaux. Ce correctif est disponible lorsque la version 1.1.61 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64546. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le `magento/quality-patches` package vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool]page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) : Search des correctifs. Utilisez l’identifiant du correctif comme mot-clé de recherche pour localiser le correctif.

## Émettre

Un message d’erreur générique s’affiche dans l’interface utilisateur et l’exception de conversion *de tableau en chaîne se produit lors de la* création de l’étiquette UPS.

<u>Procédure à suivre </u> :

1. Créez un compte client avec une adresse valide.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL GENERAL]** > **[!UICONTROL General]** > **[!UICONTROL Store Information]** et ajoutez une adresse valide.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Shipping settings]** > **[!UICONTROL Origin]** et ajoutez une adresse valide.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Delivery methods]** > **[!UICONTROL UPS]** et configurez l’onduleur.
1. Passez une commande en utilisant [!UICONTROL UPS].
1. Supprimez l’ID utilisateur et le mot de passe UPS de la base de `core_config_data` données.
1. Nettoyer le cache de configuration.
1. Ouvrez la commande créée dans le **[!UICONTROL Admin]** fichier .
1. Créez un envoi.
   1. Cochez la **[!UICONTROL Create Shipping Label]** case.
   1. Cliquez sur **[!UICONTROL Submit shipment]**.
   1. Ajouter le produit à un package. Spécifiez la taille du package (longueur, largeur et hauteur).
   1. Cliquez sur **[!UICONTROL Save]**.

<u>Résultats attendus</u> :

Le message d’erreur réel s’affiche dans l’interface utilisateur et dans les journaux.

<u>Résultats réels</u> :

* L’erreur suivante s’affiche dans l’interface utilisateur :
  *Une erreur s’est produite lors de la création de l’étiquette d’expédition.*
* L’exception *de conversion* de tableau en chaîne empêche l’affichage ou le stockage du message d’erreur réel dans les journaux.

## Appliquez le patch

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :
* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : mises à niveau et correctifs > Appliquer des correctifs dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :
* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
