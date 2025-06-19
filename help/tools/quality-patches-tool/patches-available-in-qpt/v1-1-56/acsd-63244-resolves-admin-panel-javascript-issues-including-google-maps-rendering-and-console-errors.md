---
title: 'ACSD-63244 : permet de résoudre les problèmes de JavaScript du panneau d’administration, notamment les erreurs  [!DNL Google Maps]  rendu et de console'
description: Le correctif ACSD-63244 corrige les nombreux problèmes de JavaScript dans le panneau d’administration, y compris les problèmes de rendu et  [!DNL Google Maps]  récurrence de « Uncaught TypeError this._each n’est pas une fonction&grave; erreurs dans la console du navigateur.
feature: Admin Workspace
role: Admin, Developer
exl-id: 1985c845-219e-4af4-8f70-62dd57722494
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-63244 : permet de résoudre les problèmes de JavaScript du panneau d’administration, notamment les erreurs de rendu [!DNL Google Maps] et de console

Le correctif ACSD-63244 corrige les nombreux problèmes de JavaScript dans le panneau d’administration, y compris les problèmes liés au rendu des [!DNL Google Maps] et les erreurs de `Uncaught TypeError: this._each is not a function` récurrentes dans la console du navigateur. Ce correctif est disponible avec la version 1.1.56 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). L’ID du correctif est ACSD-63244. Notez que le problème devait être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4, 2.4.4-p9, 2.4.6-p7, 2.4.7

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

* L’erreur `Uncaught TypeError: this._each is not a function` s’affiche dans la console du navigateur, interrompant la fonctionnalité de l’interface utilisateur d’administration.
* L’erreur JavaScript empêche le [!DNL Google Maps] de s’afficher correctement.

<u>Procédure à suivre </u> :

1. Chargez l’interface utilisateur d’administration d’Adobe Commerce.
1. Ouvrez la console du navigateur et exécutez le script suivant :

   ```
   Object.values([] || {}).forEach((function(e) {  
   e("dd")  
   }));  
   ```

<u>Résultats attendus</u> :

Les fonctions JavaScript disponibles dans la bibliothèque JS par défaut s’exécutent correctement sans erreurs.

<u>Résultats réels</u> :

Les erreurs JavaScript s’affichent dans la console du navigateur :

```
Uncaught TypeError: this._each is not a function
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
