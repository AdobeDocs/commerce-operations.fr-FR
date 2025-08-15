---
title: 'ACSD-61522 : les adresses e-mail dans les champs *Prénom et Nom* envoient des confirmations de commande non valides'
description: Appliquez le correctif ACSD-61522 pour résoudre le problème d’Adobe Commerce en raison duquel il est possible de saisir des adresses e-mail dans les champs *[!UICONTROL First Name]* et *[!UICONTROL Last Name]* d’un client invité, ce qui entraîne l’envoi d’e-mails de confirmation de commande non valides.
feature: Checkout, Customers
role: Admin, Developer
exl-id: e1ed7a57-4054-44db-bc17-9b9056096fce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-61522 : les adresses e-mail dans les champs *Prénom et Nom* envoient des confirmations de commande non valides

Le correctif ACSD-61522 corrige le problème de saisie des adresses e-mail dans les champs *[!UICONTROL First Name]* et *[!UICONTROL Last Name]* d’un client invité, entraînant l’envoi d’e-mails de confirmation de commande non valides. Ce correctif est disponible lorsque la version 1.1.54 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61522. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p9

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le système permet de saisir des adresses e-mail dans les champs *[!UICONTROL First Name]* et *[!UICONTROL Last Name]* d’un client invité, ce qui entraîne l’envoi d’e-mails de confirmation de commande non valides.

<u>Procédure à suivre </u> :

1. Ajoutez n’importe quel produit au panier en tant que client invité.
1. Accédez à **[!UICONTROL Checkout]**.
1. Remplissez le champ *[!UICONTROL Email Address]* avec *test1@example.com*.
1. Remplissez le champ *[!UICONTROL First Name]* avec *<test2@example.com>*.
1. Remplissez *[!UICONTROL Last Name]* avec *<test3@example.com>*.
1. Renseignez les autres champs obligatoires.
1. Passez la commande.

<u>Résultats attendus</u> :

Il n’est pas possible d’utiliser des adresses e-mail dans les champs *[!UICONTROL First Name]* et *[!UICONTROL Last Name]* .

<u>Résultats réels</u> :

1. La commande est passée.
1. Les champs *[!UICONTROL First Name]* et *[!UICONTROL Last Name]* sont enregistrés tels qu’ils ont été saisis.
1. Les e-mails de confirmation de commande sont envoyés aux trois e-mails.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
