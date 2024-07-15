---
title: Fonctionnement des correctifs
description: Découvrez les différents types de correctifs pour Adobe Commerce et leur fonctionnement.
exl-id: d7072ed4-7d51-41fe-881a-aae3b2000b55
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Fonctionnement des correctifs

>[!WARNING]
>
>Nous vous recommandons vivement de tester tous les correctifs dans un environnement d’évaluation ou de développement avant de les déployer en production. Nous vous recommandons également vivement de sauvegarder vos données avant d’appliquer un correctif. Voir [Sauvegarde et restauration du système de fichiers](../../installation/tutorials/backup.md).

Les fichiers de correctif (ou diff) sont des fichiers texte qui font remarquer :

- Le ou les fichiers à modifier.
- Numéro de la ligne à modifier et nombre de lignes à modifier.
- Le nouveau code à échanger.

Lorsque le programme de correctifs est exécuté, ce fichier est lu et les modifications spécifiées sont apportées au ou aux fichiers.

Il existe trois types de correctifs :

- **Correctifs** : correctifs publiés par l’Adobe sur le [Centre de sécurité](https://magento.com/security/patches).
- **Correctifs individuels** : correctifs que le support Adobe Commerce crée et distribue sur une base individuelle.
- **Correctifs personnalisés** : correctifs non officiels que vous pouvez créer à partir d’une validation Git.

## Correctifs

Les correctifs sont des correctifs qui contiennent des correctifs de sécurité ou de qualité à fort impact et qui affectent de nombreux commerçants. Ces correctifs sont appliqués à la prochaine version de correctif pour la version mineure applicable. Adobe publie des correctifs si nécessaire.

Vous trouverez des correctifs dans le [Centre de sécurité](https://magento.com/security/patches). Suivez les instructions de la page pour télécharger le fichier de correctif, en fonction de votre version et de votre type d’installation. Utilisez la [ligne de commande](../patches/apply.md#) ou le [compositeur](../patches/apply.md) pour appliquer les correctifs de correctifs.

>[!NOTE]
>
>Les correctifs peuvent contenir des modifications incompatibles récurrentes.

## Correctifs individuels

Les correctifs individuels contiennent des correctifs de qualité à faible impact pour un problème spécifique. Ces correctifs sont appliqués à la dernière version mineure prise en charge (par exemple, 2.4.x), mais peuvent ne pas figurer dans la version mineure prise en charge précédente (par exemple, 2.3.x). Adobe publie les correctifs individuels si nécessaire.

Utilisez [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"} pour appliquer des correctifs individuels.

>[!NOTE]
>
>Les correctifs individuels ne contiennent pas de modifications rétrocompatibles.

## Correctifs personnalisés

Parfois, il faut un certain temps à l’équipe d’ingénierie d’Adobe pour inclure un correctif de bogue créé sur GitHub dans une version du compositeur d’Adobe Commerce. En attendant, vous pouvez créer un correctif à partir de GitHub et utiliser le plug-in [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) pour l’appliquer à votre installation basée sur le compositeur.

Utilisez la [ligne de commande](apply.md#command-line) ou le [compositeur](apply.md#composer) pour appliquer des correctifs personnalisés.

Il existe de nombreuses façons de créer des fichiers correctifs personnalisés. L’exemple suivant se concentre sur la création d’un correctif à partir d’une validation Git connue.

Pour créer un correctif personnalisé :

1. Créez un répertoire `patches/composer` dans votre projet local.
1. Identifiez la validation ou la requête d’extraction GitHub à utiliser pour le correctif. Cet exemple utilise la validation [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede), liée au problème GitHub [#6474](https://github.com/magento/magento2/issues/6474).
1. Ajoutez les extensions `.patch` ou `.diff` à l’URL de validation. Utilisez `.diff` pour une taille de fichier plus petite. Par exemple : [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. Enregistrez la page en tant que fichier dans le répertoire `patches/composer`. Par exemple, `github-issue-6474.diff`.
1. Modifiez le fichier et supprimez `app/code/<VENDOR>/<PACKAGE>` de tous les chemins afin qu&#39;ils soient relatifs au répertoire `vendor/<VENDOR>/<PACKAGE>`.

   >[!NOTE]
   >
   >Les éditeurs de texte qui suppriment automatiquement les espaces de fin ou qui ajoutent de nouvelles lignes peuvent rompre le correctif. Utilisez un simple éditeur de texte pour effectuer ces modifications.

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
>Pour appliquer un correctif à un projet d’infrastructure cloud Adobe Commerce, reportez-vous à la section [Application de correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) du _guide Commerce on Cloud_.
