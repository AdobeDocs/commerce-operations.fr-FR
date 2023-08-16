---
title: Utilisation
description: Découvrez comment utiliser le [!DNL Quality Patches Tool].
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---

# Utilisation

La variable [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) fournit des correctifs individuels développés par Adobe et la communauté Magento Open Source. Il vous permet d’appliquer, de rétablir et d’afficher des informations générales sur tous les correctifs individuels disponibles pour la version installée d’Adobe Commerce ou de Magento Open Source. Vous pouvez appliquer des correctifs aux projets Adobe Commerce et Magento Open Source, quel que soit le développeur du correctif. Par exemple, vous pouvez appliquer un correctif développé par la communauté aux projets Adobe Commerce.


Regardez ceci : [video technique](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) et découvrez comment utiliser l’outil de correctifs de qualité pour Adobe Commerce et Magento Open Source.

>[!INFO]
>
>Voir [Application de correctifs individuels](#apply-individual-patches) pour obtenir des instructions sur l’application de correctifs à vos projets Adobe Commerce ou Magento Open Source. Voir [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) pour consulter la liste complète des correctifs publiés.

>[!WARNING]
>
>Il n’est pas recommandé d’utiliser la variable [!DNL Quality Patches Tool] pour appliquer un grand nombre de correctifs, car cela augmente la complexité de votre code et rend la mise à niveau vers une nouvelle version plus difficile.

## Installer

>[!INFO]
>
>S’il n’est pas déjà installé, vous devez installer [[!DNL Git]](https://github.com/git-guides/install-git) ou [Correctif](https://man7.org/linux/man-pages/man1/patch.1.html) avant d’installer le [!DNL Quality Patches Tool]. Ajoutez la variable `magento/quality-patches` Module de compositeur `composer.json` fichier :

```bash
composer require magento/quality-patches
```

## Affichage des correctifs individuels

Pour afficher la liste des correctifs individuels disponibles pour votre version d’Adobe Commerce ou de Magento Open Source :

```bash
./vendor/bin/magento-patches status
```

Vous verrez une sortie similaire à celle-ci :

| Id | Titre | Type | État | Détails |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC est désactivé pendant les déploiements | Facultatif | Non appliqué | Composants concernés :<br> - magento/module-page-cache |
| MCLOUD-5650 | Conserver la configuration de déploiement après lecture du fichier | Facultatif | Non appliqué | Composants concernés :<br> - magento/framework |
| MCLOUD-5684 | La pagination ne fonctionne pas - product_list_limit=all | Facultatif | Non appliqué | Composants concernés : - magento/module-élasticsearch |
| MCLOUD-5837 | Correction du problème de l’équilibreur de charge | Obsolète | Appliqué | Remplacement recommandé : MC-1 <br> Composants concernés : - magento/framework |
| BUNDLE-2554 | Bogue Définir les informations de paiement | Facultatif | Non appliqué | Composants concernés : <br>- amzn/amazon-pay-module |
| MC-1 | Correction du problème 1 | Facultatif | Appliqué | Composants concernés : <br> - magento/module-cms |
| MC-2 | Correction du problème 2 | Facultatif | Non appliqué | Composants concernés : <br> - magento/module-cms |
| MC-3 | Correction du problème 3 | Facultatif | Non appliqué | Correctifs requis :<br> - MC-2 <br>Composants concernés : <br>- magento/module-cms |
| MC-3-V2 | Correctif mis à jour pour le problème 3, qui remplace le correctif MC-3 | Facultatif | N/A | Composants concernés :  <br>- magento/module-cms |

Adobe Commerce 2.3.5.

Le tableau d’état comprend :

- **Type**:
   - `Optional` — Tous les correctifs de l’événement [!DNL Quality Patches Tool] et la variable [Guide d’infrastructure de Commerce on Cloud > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Les packages sont facultatifs pour les installations Adobe Commerce et Magento Open Source.
   - `Deprecated` — Adobe a abandonné le correctif individuel. Si vous avez appliqué le correctif, nous vous recommandons de le rétablir. L’opération de rétablissement supprime également le correctif de la table des statuts.

- **État**:
   - `Applied` — Le correctif a été appliqué.
   - `Not applied` — Le correctif n&#39;a pas été appliqué.
   - `N/A` — Le statut du correctif ne peut pas être défini en raison de conflits.

- **Détails**:
   - `Affected components` — Liste des modules affectés.
   - `Required patches` — Liste des correctifs qui doivent être appliqués pour qu’un correctif indiqué fonctionne correctement (dépendances).
   - `Recommended replacement` — Correctif recommandé pour remplacer un correctif obsolète.

>[!INFO]
>
>Après la mise à niveau vers une nouvelle version d’Adobe Commerce ou de Magento Open Source, vous devez réappliquer les correctifs si ceux-ci ne sont pas inclus dans la nouvelle version. Voir [Réappliquer des correctifs après une mise à niveau](#re-apply-patches-after-an-upgrade).

## Application de correctifs individuels {#apply-individual-patches}

>[!WARNING]
>
>Il est recommandé de tester tous les correctifs dans un environnement d’évaluation ou de développement avant de les déployer en production. Il est également recommandé de sauvegarder vos données avant d’appliquer un correctif. Voir [Sauvegarde et restauration du système de fichiers, du média et de la base de données](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Pour appliquer un seul correctif, exécutez la commande suivante lorsque `MAGETWO-XXXX` est l’identifiant du correctif spécifié dans le tableau d’état :

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

Vous pouvez également appliquer plusieurs correctifs en même temps en séparant chaque ID de correctif supplémentaire par un espace :

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

Vous devez nettoyer le cache après avoir appliqué des correctifs pour voir les modifications apportées à l’application Adobe Commerce :

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>Envisagez de conserver une liste des correctifs appliqués à un emplacement distinct. Vous devrez peut-être réappliquer certaines d’entre elles après la mise à niveau vers une nouvelle version d’Adobe Commerce ou de Magento Open Source. Voir [Réappliquer des correctifs après une mise à niveau](#re-apply-patches-after-an-upgrade).

## Rétablissement de correctifs individuels

>[!WARNING]
>
>Il est recommandé de tester tous les correctifs dans un environnement d’évaluation ou de développement avant de les déployer en production. Il est également recommandé de sauvegarder vos données avant d’appliquer un correctif. Voir [Sauvegarde et restauration du système de fichiers, du média et de la base de données](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Pour rétablir un seul correctif, exécutez la commande suivante où `MAGETWO-XXXX` est l’identifiant du correctif spécifié dans le tableau d’état :

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

Vous pouvez également rétablir plusieurs correctifs en même temps en séparant chaque ID de correctif supplémentaire par un espace :

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

Pour annuler tous les correctifs appliqués :

```bash
./vendor/bin/magento-patches revert --all
```

Vous devez nettoyer le cache après avoir restauré les correctifs pour voir les modifications apportées à l’application Adobe Commerce :

```bash
./bin/magento cache:clean
```

## Obtenir des mises à jour

Adobe Commerce publie régulièrement de nouveaux correctifs individuels. Vous devez mettre à jour la variable [!DNL Quality Patches Tool] pour obtenir de nouveaux correctifs individuels :

```bash
composer update magento/quality-patches
```

Affichez les correctifs ajoutés :

>[!TIP]
>
>De nouveaux correctifs s’affichent au bas du tableau.

```bash
./vendor/bin/magento-patches status
```

## Réappliquer des correctifs après une mise à niveau {#re-apply-patches-after-an-upgrade}

Lorsque vous effectuez une mise à niveau vers une nouvelle version d’Adobe Commerce ou de Magento Open Source, vous devez réappliquer les correctifs si ceux-ci ne sont pas inclus dans la nouvelle version.

Pour réappliquer des correctifs :

1. Mettez à jour le [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. Ouvrez la liste des correctifs précédemment appliqués, qui a été recommandée dans [Application de correctifs individuels](#apply-individual-patches).

1. Appliquez les correctifs :

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   La bonne pratique consiste à appliquer les correctifs un par un.

1. Nettoyez le cache :

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >Lorsque vous exécutez le `status` , les correctifs inclus dans la nouvelle version ne sont plus affichés dans le tableau des correctifs disponibles.

## Journalisation

La variable [!DNL Quality Patches Tool] consigne toutes les opérations dans la variable `<Magento_root>/var/log/patch.log` fichier .
