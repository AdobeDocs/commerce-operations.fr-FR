---
title: "ACSD-61522 : les adresses électroniques dans les champs *Prénom et Nom* envoient des confirmations de commande non valides"
description: Appliquez le correctif ACSD-61522 pour résoudre le problème Adobe Commerce en raison duquel il est possible de saisir des adresses électroniques dans les champs *[!UICONTROL First Name]* et *[!UICONTROL Last Name]* d’un client invité, ce qui entraîne l’envoi d’emails de confirmation de commande non valides.
feature: Checkout, Customers
role: Admin, Developer
source-git-commit: d56f4fda007c1499bdba82ac3db9ac5ea1d34b0e
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# ACSD-61522 : Les adresses électroniques dans les champs *Prénom et nom* envoient des confirmations de commande non valides

Le correctif ACSD-61522 corrige le problème lorsqu’il est possible de saisir des adresses email dans les champs *[!UICONTROL First Name]* et *[!UICONTROL Last Name]* d’un client invité, ce qui entraîne l’envoi d’emails de confirmation de commande non valides. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 est installé. L’ID de correctif est ACSD-61522. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p9

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le système permet de saisir des adresses électroniques dans les champs *[!UICONTROL First Name]* et *[!UICONTROL Last Name]* d’un client invité, ce qui entraîne l’envoi d’emails de confirmation de commande non valides.

<u>Étapes à reproduire</u> :

1. Ajoutez n’importe quel produit au panier en tant que client invité.
1. Accédez à **[!UICONTROL Checkout]**.
1. Renseignez le champ *[!UICONTROL Email Address]* avec *test1@example.com*.
1. Renseignez le champ *[!UICONTROL First Name]* avec *<test2@example.com>*.
1. Remplissez *[!UICONTROL Last Name]* avec *<test3@example.com>*.
1. Renseignez les autres champs obligatoires.
1. Placez la commande.

<u>Résultats attendus</u> :

Il n’est pas possible d’utiliser des adresses électroniques dans les champs *[!UICONTROL First Name]* et *[!UICONTROL Last Name]* .

<u>Résultats réels</u> :

1. La commande est passée.
1. Les champs *[!UICONTROL First Name]* et *[!UICONTROL Last Name]* sont enregistrés comme renseignés.
1. Les trois emails de confirmation de commande sont envoyés.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
