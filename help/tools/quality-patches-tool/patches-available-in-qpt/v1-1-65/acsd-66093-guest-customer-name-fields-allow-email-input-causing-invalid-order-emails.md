---
title: 'ACSD-66093 : les champs de nom du client invité autorisent la saisie d’e-mails, ce qui entraîne des e-mails de commande non valides'
description: Appliquez le correctif ACSD-66093 pour résoudre le problème Adobe Commerce où il est possible de saisir des adresses e-mail dans les champs client invité **[!UICONTROL First Name]** et **[!UICONTROL Last Name]** et d’envoyer des e-mails de confirmation de commande non valides.
feature: Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 30790492-330e-4810-8069-fce87b40ebb2
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-66093 : les champs de nom du client invité autorisent la saisie d’e-mails, ce qui entraîne des e-mails de commande non valides

Le correctif ACSD-66093 corrige le problème où les adresses e-mail pouvaient être saisies dans les champs **[!UICONTROL First Name]** et **[!UICONTROL Last Name]** du client invité, ce qui entraînait des e-mails de confirmation de commande non valides. Ce correctif est disponible lorsque la version 1.1.65 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66093. Notez que le problème a été résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p11

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Des adresses électroniques ont pu être saisies dans les champs **[!UICONTROL First Name]** et **[!UICONTROL Last Name]** du client invité, ce qui a entraîné la création d’e-mails de confirmation de commande non valides.

<u>Procédure à suivre </u> :

1. Ajoutez des produits au panier en tant que client invité.
2. Accédez au passage en caisse.
3. Renseignez l’adresse e-mail avec « test1@gmail.co ».
4. Remplissez **[!UICONTROL First Name]** avec « <test2@gmail.co> ».
5. Remplissez **[!UICONTROL Last Name]** avec « <test3@gmail.co> ».
6. Renseignez les autres champs obligatoires.
7. Passer une commande.

<u>Résultats attendus</u> :

Des messages de validation doivent apparaître pour indiquer que les champs **[!UICONTROL First Name]** et **[!UICONTROL Last Name]** ne sont pas valides, comme *Prénom n’est pas valide ! et le nom de famille n’est pas valide.* et la commande ne doivent pas être passées.

<u>Résultats réels</u> :

La commande est passée.
Les champs **[!UICONTROL First Name]** et **[!UICONTROL Last Name]** sont enregistrés tels qu’ils ont été saisis.
Un e-mail de confirmation de commande est envoyé aux trois adresses e-mail : test1@gmail.co, test2@gmail.co et test3@gmail.co.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
