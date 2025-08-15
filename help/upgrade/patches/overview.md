---
title: Fonctionnement des correctifs
description: Découvrez les différents types de correctifs d’Adobe Commerce et leur fonctionnement.
exl-id: d7072ed4-7d51-41fe-881a-aae3b2000b55
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Fonctionnement des correctifs

>[!WARNING]
>
>Nous vous recommandons vivement de tester tous les correctifs dans un environnement d’évaluation ou de développement avant leur déploiement en production. Nous vous recommandons vivement de sauvegarder vos données avant d&#39;appliquer un correctif. Voir [Sauvegarder et restaurer le système de fichiers](../../installation/tutorials/backup.md).

Les fichiers Patch (ou diff) sont des fichiers texte qui notent :

- Le ou les fichiers à modifier.
- Le numéro de ligne à modifier et le nombre de lignes à modifier.
- Le nouveau code à permuter.

Lorsque le programme de correctifs est exécuté, ce fichier est lu dans et les modifications spécifiées sont apportées aux fichiers.

Il existe trois types de correctifs :

- **Correctifs** : correctifs qu’Adobe publie sur le [Centre de sécurité](https://magento.com/security/patches).
- **Correctifs individuels** : les correctifs créés et distribués par la prise en charge d’Adobe Commerce au cas par cas.
- **Correctifs personnalisés** : correctifs non officiels que vous pouvez créer à partir d’une validation Git.

## Correctifs

Les correctifs sont des correctifs de sécurité ou de qualité qui affectent de nombreux commerçants. Ces correctifs sont appliqués à la prochaine version de correctif pour la version mineure applicable. Adobe publie des correctifs si nécessaire.

Vous trouverez les correctifs dans le [Centre de sécurité](https://magento.com/security/patches). Suivez les instructions de la page pour télécharger le fichier de correctif, en fonction de votre version et de votre type d’installation. Utilisez la [ligne de commande](../patches/apply.md#) ou le [compositeur](../patches/apply.md) pour appliquer des correctifs de correctifs logiciels.

>[!NOTE]
>
>Les correctifs peuvent contenir des modifications rétrocompatibles.

## Correctifs individuels

Les correctifs individuels contiennent des correctifs de qualité à faible impact pour un problème spécifique. Ces correctifs sont appliqués à la version mineure la plus récemment prise en charge (par exemple, 2.4.x), mais peuvent être absents de la version mineure précédente prise en charge (par exemple, 2.3.x). Adobe publie des correctifs individuels selon les besoins.

Utilisez l’[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"} pour appliquer des correctifs individuels.

>[!NOTE]
>
>Les correctifs individuels ne contiennent pas de modifications rétrocompatibles.

## Correctifs personnalisés

Parfois, il faut un certain temps à l’équipe d’ingénierie Adobe pour inclure un correctif de bug réalisé sur GitHub dans une version du compositeur Adobe Commerce. En attendant, vous pouvez créer un correctif à partir de GitHub et utiliser le plug-in [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) pour l’appliquer à votre installation basée sur le compositeur.

Utilisez la [ligne de commande](apply.md#command-line) ou le [compositeur](apply.md#composer) pour appliquer des correctifs personnalisés.

Il existe de nombreuses façons de créer des fichiers de correctifs personnalisés. L’exemple suivant porte sur la création d’un correctif à partir d’une validation Git connue.

Pour créer un correctif personnalisé :

1. Créez un répertoire `patches/composer` dans votre projet local.
1. Identifiez la requête de validation ou d’extraction GitHub à utiliser pour le correctif. Cet exemple utilise la validation [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede), liée au problème GitHub [#6474](https://github.com/magento/magento2/issues/6474).
1. Ajoutez les extensions `.patch` ou `.diff` à l’URL de validation. Utilisez `.diff` pour une taille de fichier plus petite. Par exemple : [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. Enregistrez la page en tant que fichier dans le répertoire `patches/composer`. Par exemple, `github-issue-6474.diff`.
1. Modifiez le fichier et supprimez les `app/code/<VENDOR>/<PACKAGE>` de tous les chemins d’accès afin qu’ils soient relatifs au répertoire `vendor/<VENDOR>/<PACKAGE>`.

   >[!NOTE]
   >
   >Les éditeurs de texte qui suppriment automatiquement les espaces de fin ou ajoutent de nouvelles lignes peuvent rompre le patch. Utilisez un simple éditeur de texte pour effectuer ces modifications.

L’exemple suivant illustre le fichier DIFF mentionné précédemment après la suppression de toutes les instances de `app/code/Magento/Payment` :

```diff
diff --git a/view/frontend/web/js/view/payment/iframe.js b/view/frontend/web/js/view/payment/iframe.js
index c8a6fef58d31..7d01c195791e 100644
--- a/view/frontend/web/js/view/payment/iframe.js
+++ b/view/frontend/web/js/view/payment/iframe.js
@@ -154,6 +154,7 @@ define(
              */
             clearTimeout: function () {
                 clearTimeout(this.timeoutId);
+                this.fail();

                 return this;
             },
```

## Application de correctifs

Vous pouvez appliquer des correctifs à l’aide de l’une des méthodes suivantes :

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [Ligne de commande](/help/upgrade/patches/apply.md#command-line)
- [Compositeur](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>Pour appliquer un correctif à un projet d’infrastructure cloud d’Adobe Commerce, voir [Application de correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide _Commerce sur le cloud_.
