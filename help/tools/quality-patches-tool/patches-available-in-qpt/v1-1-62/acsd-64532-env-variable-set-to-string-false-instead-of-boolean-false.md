---
title: 'ACSD-64532 : la variable ENV définie sur *false* est traitée comme une chaîne *false* au lieu d’une BOOLÉENNE *FALSE*'
description: Appliquez le correctif ACSD-64532 pour résoudre le problème d’Adobe Commerce où une variable « ENV » définie sur « false » est traitée comme une chaîne « false » au lieu d’une variable « BOOLEAN » « FALSE ».
feature: Variables
role: Admin, Developer
source-git-commit: 603b4f92ab3bbf4702d5373bd02dfdd770f57d5b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# ACSD-64532 : la variable ENV définie sur « false » est traitée comme une chaîne « false » au lieu d’une valeur BOOLÉENNE FALSE

Le correctif ACSD-64532 corrige le problème où la variable `ENV` définie sur *false* est traitée comme une chaîne *false* au lieu d’une `BOOLEAN` *FALSE*. Ce correctif est disponible lorsque la version 1.1.62 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64532. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p8

**Compatible avec les versions d’Adobe Commerce :**
Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`ENV` variable définie sur *false* est traitée comme une chaîne *false* au lieu d’une `BOOLEAN` *FALSE*.

<u>Procédure à suivre </u> :
1. Ajoutez des `env:MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK` avec la valeur *false* aux variables d’environnement sur Adobe Commerce sur l’infrastructure cloud.
1. Attendez le redéploiement.
1. Exécutez le script en vérifiant la valeur :

   ```php
   <?php
   require '../app/bootstrap.php';
   $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
   $objectManager = $bootstrap->getObjectManager();
   $deploymentConfig = $objectManager->get('Magento\Framework\App\DeploymentConfig');
   $useAppLock = $deploymentConfig->get('indexer/use_application_lock');
   
   var_dump($useAppLock);
   
   $configParsedValue = $deploymentConfig->get('indexer/use_application_lock') ?: false;
   
   var_dump($configParsedValue); 
   ```

<u>Résultats attendus</u> :
`$configParsedValue`, qui est le résultat de la méthode `isUseApplicationLock()`, doit renvoyer une valeur négative pour être correctement interprétée dans la méthode `\Magento\Indexer\Model\Mview\View\State::getStatus()`.

<u>Résultats réels</u> :
`$configParsedValue` a une valeur de *`string(5) false`*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :
* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
