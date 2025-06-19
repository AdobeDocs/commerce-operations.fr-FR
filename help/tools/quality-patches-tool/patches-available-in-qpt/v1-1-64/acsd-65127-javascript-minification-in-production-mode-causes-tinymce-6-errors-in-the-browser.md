---
title: 'ACSD-65127 : la minimisation de JavaScript en mode de production provoque des erreurs  [!DNL TinyMCE] 6 dans le navigateur'
description: Appliquez le correctif ACSD-65127 pour résoudre le problème d’Adobe Commerce où l’activation de la minimisation de JavaScript en mode production provoquait des erreurs dans la console du navigateur [!DNL TinyMCE] 6, ce qui affectait les fonctionnalités et l’expérience utilisateur.
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: c878d5a4-8059-4bfc-93a8-0a9606e866fc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-65127 : la minimisation de JavaScript en mode de production provoque des erreurs [!DNL TinyMCE] 6 dans le navigateur

Le correctif ACSD-65127 corrige le problème en raison duquel l’activation de la minimisation de JavaScript en mode de production entraînait des erreurs dans la console du navigateur [!DNL TinyMCE] 6, ce qui affectait les fonctionnalités et l’expérience utilisateur. Ce correctif est disponible lorsque la version 1.1.64 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65127. Ce problème a été résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’activation de la minimisation de JavaScript en mode production a provoqué la génération d’erreurs dans la console du navigateur par [!DNL TinyMCE] 6, ce qui a eu une incidence sur les fonctionnalités et l’expérience utilisateur.

<u>Procédure à suivre </u> :

1. Définissez la configuration en exécutant les commandes ci-dessous :

```
bin/magento config:set --lock-config dev/js/minify_files 1
bin/magento config:set --lock-config dev/js/enable_js_bundling 1
bin/magento config:set --lock-config dev/js/merge_files 1
```

1. Activez le mode de production.

```
bin/magento deploy:mode:set production
```

1. Dans la barre latérale d’administration, accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]**. Cliquez sur **[!UICONTROL Edit]** sur un produit répertorié et faites défiler l’écran vers le bas pour **[!UICONTROL Content]** et sélectionnez **[!UICONTROL Show Editor]**.

<u>Résultats attendus</u> :

Aucune erreur JS dans la console du navigateur.

<u>Résultats réels</u> :

Erreurs *404* dans la console du navigateur pour le `tiny_mce_6/plugins/help/js/i18n/keynav/en.js` js.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
