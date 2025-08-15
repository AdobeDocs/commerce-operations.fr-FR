---
title: 'ACSD-64113 : erreur d’administration lors du chargement d’une image d’une largeur inférieure à la hauteur via  [!DNL Media Gallery]'
description: Appliquez le correctif ACSD-64113 pour résoudre le problème d’Adobe Commerce en raison duquel des erreurs se produisent chez l’administrateur lors du chargement d’images présentant une largeur relativement faible par rapport à leur hauteur (ou inversement) via l’ [!DNL Media Gallery] .
feature: Page Content, Media, Admin Workspace
role: Admin, Developer
exl-id: aba9d875-1d5d-49c2-8071-ba0ce679d7cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64113 : erreur d’administration lors du chargement d’une image d’une largeur inférieure à la hauteur via [!DNL Media Gallery]

Le correctif ACSD-64113 corrige le problème où des erreurs se produisent dans l’administration lors du chargement d’images avec une largeur relativement faible par rapport à leur hauteur (ou vice versa) via le [!DNL Media Gallery]. Ce correctif est disponible lorsque la version 1.1.59 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64113. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Des erreurs se produisent dans l’administration lors du chargement d’images avec une largeur relativement faible par rapport à leur hauteur (ou vice versa) via le [!DNL Media Gallery].

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Media]** > **[!UICONTROL Media Gallery]** et sélectionnez le répertoire **[!UICONTROL wysiwyg]** .
1. Chargez l’image avec une largeur relativement faible par rapport à sa hauteur (ou vice versa).

<u>Résultats attendus</u> :

L’image est téléchargée sans erreur.

<u>Résultats réels</u> :

1. Le message d’erreur suivant est généré :

   *Un problème technique du serveur a provoqué une erreur. Réessayez pour continuer ce que vous étiez en train de faire. Si le problème persiste, réessayez plus tard.*
1. `var/log/exception.log` contient :

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($width) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

   ou

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($height) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
