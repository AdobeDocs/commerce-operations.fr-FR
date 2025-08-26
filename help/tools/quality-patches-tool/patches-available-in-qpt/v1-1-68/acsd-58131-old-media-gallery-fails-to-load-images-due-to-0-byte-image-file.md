---
title: 'ACSD-58131 : l’ancienne galerie de médias ne parvient pas à charger les images en raison du fichier image de 0 octet'
description: Appliquez le correctif ACSD-58131 pour résoudre le problème d’Adobe Commerce en raison duquel l’ancienne galerie de médias ne parvient pas à effectuer le rendu des images lorsqu’une image de 0 octet est présente dans le répertoire.
feature: Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: b09749a1e56ab6a7b613135ca252fd69757669d0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-58131 : l’ancienne galerie de médias ne parvient pas à charger les images en raison du fichier image de 0 octet

Le correctif ACSD-58131 corrige le problème où l’ancienne galerie de médias ne parvient pas à effectuer le rendu des images lorsqu’une image de 0 octet est présente dans le répertoire. Ce correctif est disponible lorsque la version 1.1.68 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-58131. Notez que ce problème doit être résolu dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsqu’une image de 0 octet est placée dans le répertoire de la galerie multimédia, l’ancienne galerie multimédia ne parvient pas à effectuer le rendu des images. Le système mis à jour ignore désormais les fichiers 0 octet non valides, affiche les images valides comme prévu et consigne un avertissement pour chaque fichier non valide.

```
[2024-05-02T14:00:39.616459+00:00] report.WARNING: The image empty2.jpg is invalid and cannot be displayed in the gallery. [] []
```

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]**.
1. Définissez **[!UICONTROL Enable Old Media Gallery]** sur *Oui*.
1. Placez quelques images dans le répertoire `pub/media/wysiwyg`.
1. Créez une image de 0 octet dans le même répertoire à l’aide de `touch pub/media/wysiwyg/empty_image.png`.
1. Ajoutez une image à partir du répertoire `wysiwyg` via Page Builder sous n’importe quel contenu (par exemple, un bloc CMS) :
   1. Créez un bloc. Accédez à **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Blocks]** et cliquez sur **[!UICONTROL Add New Block]**.
   1. Modifiez la section de contenu à l’aide de Page Builder.
   1. Sous **[!UICONTROL Layout]**, faites glisser un nouveau **[!UICONTROL Row]** sur la scène.
   1. Développez **[!UICONTROL Media]** et faites glisser un espace réservé **[!UICONTROL Image]** dans la ligne.
   1. Cliquez sur **[!UICONTROL Select from Gallery]**.
   1. Sélectionnez le répertoire `wysiwyg` s’il n’est pas sélectionné par défaut.

<u>Résultats attendus</u> :

La galerie de médias reste fonctionnelle même si une image de 0 octet (ou tout autre fichier) existe.

<u>Résultats réels</u> :

La galerie de médias ne parvient pas à charger les images du répertoire `wysiwyg` en raison d’une erreur critique consignée `var/log/system.log` :

```
[2024-03-22T05:00:55.100934+00:00] report.CRITICAL: Exception: Notice: getimagesizefromstring(): Error reading from ! in /app/project/vendor/magento/module-cms/Model/Wysiwyg/Images/Storage.php on line 426 in /app/project/vendor/magento/framework/App/ErrorHandler.php:62
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
