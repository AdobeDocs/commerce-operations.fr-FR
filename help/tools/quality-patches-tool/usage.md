---
title: Utilisation
description: Découvrez comment utiliser l’outil de correctifs de la qualité pour appliquer et gérer des correctifs pour Adobe Commerce. Découvrez les techniques de test, d’application et de gestion des correctifs.
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
type: Troubleshooting
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Utilisation

Le [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) fournit des correctifs individuels développés par Adobe et la communauté Magento Open Source. Il vous permet d’appliquer, d’annuler et d’afficher des informations générales sur tous les correctifs individuels disponibles pour la version installée d’Adobe Commerce. Vous pouvez appliquer des correctifs à des projets Adobe Commerce, quelle que soit la personne qui les a développés. Par exemple, vous pouvez appliquer un correctif développé par la communauté aux projets Adobe Commerce.

Regardez cette [vidéo technique](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) et découvrez comment utiliser l’outil de correctifs de qualité pour Adobe Commerce.

>[!INFO]
>
>Voir [ Application de correctifs individuels ](#apply-individual-patches) pour obtenir des instructions sur l’application de correctifs à vos projets Adobe Commerce. Voir [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) pour consulter la liste complète des correctifs publiés.

>[!WARNING]
>
>Il n’est pas recommandé d’utiliser le [!DNL Quality Patches Tool] pour appliquer un grand nombre de correctifs, car cela augmente la complexité de votre code et rend la mise à niveau vers une nouvelle version plus difficile.

## Installer

>[!INFO]
>
>S’il n’est pas déjà installé, vous devez installer [[!DNL Git]](https://github.com/git-guides/install-git) ou [Patch](https://man7.org/linux/man-pages/man1/patch.1.html) avant d’installer le [!DNL Quality Patches Tool]. Ajoutez le package `magento/quality-patches` Composer à votre fichier `composer.json` :

```bash
composer require magento/quality-patches
```

## Affichage des correctifs individuels

Pour afficher la liste des correctifs individuels disponibles pour votre version d’Adobe Commerce :

```bash
./vendor/bin/magento-patches status
```

Une sortie similaire à celle-ci s’affiche :

| Id | Titre | Type | Statut | Détails |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC est désactivé pendant les déploiements | Facultatif | Non appliqué | Composants affectés : <br> - magento/module-page-cache |
| MCLOUD-5650 | Conserver la configuration de déploiement après lecture du fichier | Facultatif | Non appliqué | Composants concernés : <br> - Magento/framework |
| MCLOUD-5684 | La pagination ne fonctionne pas - product_list_limit=all | Facultatif | Non appliqué | Composants concernés : - Magento/module-elasticsearch |
| MCLOUD-5837 | Correction du problème de répartition de charge | Obsolète | Appliqué | Remplacement recommandé : MC-1 <br> Composants affectés : - magento/framework |
| BUNDLE-2554 | Définir le bug des informations de paiement | Facultatif | Non appliqué | Composants concernés : <br>- amzn/amazon-pay-module |
| MC-1 | Correction du problème 1 | Facultatif | Appliqué | Composants concernés : <br> - magento/module-cms |
| MC-2 | Correction du problème 2 | Facultatif | Non appliqué | Composants concernés : <br> - magento/module-cms |
| MC-3 | Correction du problème 3. | Facultatif | Non appliqué | Correctifs requis :<br> - MC-2 <br>Composants concernés : <br>- magento/module-cms |
| MC-3-V2 | Mise à jour du correctif pour le problème 3, remplace le correctif MC-3 | Facultatif | S.O. | Composants concernés : <br>-magento/module-cms |

Adobe Commerce 2.3.5.

Le tableau de statut comprend les éléments suivants :

- **Type** :
   - `Optional` — Tous les correctifs du [!DNL Quality Patches Tool] et du package [Guide de Commerce sur les infrastructures cloud > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) sont facultatifs pour les installations Adobe Commerce.
   - `Deprecated` — Adobe a rendu obsolète le correctif individuel. Si vous avez appliqué le correctif, nous vous recommandons de le rétablir. L’opération de rétablissement supprime également le correctif de la table des statuts.

- **Statut** :
   - `Applied` — Le correctif a été appliqué.
   - `Not applied` — Le correctif n&#39;a pas été appliqué.
   - `N/A` — Impossible de définir l&#39;état du correctif en raison de conflits.

- **Détails** :
   - `Affected components` — Liste des modules concernés.
   - `Required patches` : liste des patchs à appliquer pour qu&#39;un patch indiqué fonctionne correctement (dépendances).
   - `Recommended replacement` — Correctif qui est un remplacement recommandé pour un correctif obsolète.

>[!INFO]
>
>Après la mise à niveau vers une nouvelle version d’Adobe Commerce, vous devez réappliquer les correctifs si ceux-ci ne sont pas inclus dans la nouvelle version. Voir [Réappliquer les correctifs après une mise à niveau](#re-apply-patches-after-an-upgrade).

## Application de correctifs individuels {#apply-individual-patches}

>[!WARNING]
>
>Il est recommandé de tester tous les correctifs dans un environnement d’évaluation ou de développement avant de les déployer en production. Il est également recommandé de sauvegarder vos données avant d’appliquer un correctif. Voir [ Sauvegarde et restauration du système de fichiers, du support et de la base de données](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Pour appliquer un seul correctif, exécutez la commande suivante où `MAGETWO-XXXX` correspond à l’identifiant de correctif spécifié dans le tableau d’état :

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

Vous pouvez également appliquer plusieurs correctifs en même temps en séparant chaque identifiant de correctif supplémentaire par un espace :

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

Vous devez nettoyer le cache après l’application des correctifs pour afficher les modifications dans l’application Adobe Commerce :

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>Pensez à conserver une liste de correctifs appliqués à un emplacement distinct. Vous devrez peut-être réappliquer certaines d’entre elles après la mise à niveau vers une nouvelle version d’Adobe Commerce. Voir [Réappliquer les correctifs après une mise à niveau](#re-apply-patches-after-an-upgrade).

## Rétablissement de correctifs individuels

>[!WARNING]
>
>Il est recommandé de tester tous les correctifs dans un environnement d’évaluation ou de développement avant de les déployer en production. Il est également recommandé de sauvegarder vos données avant d’appliquer un correctif. Voir [ Sauvegarde et restauration du système de fichiers, du support et de la base de données](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Pour rétablir un seul correctif, exécutez la commande suivante où `MAGETWO-XXXX` correspond à l’identifiant de correctif spécifié dans le tableau d’état :

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

Vous pouvez également rétablir plusieurs correctifs en même temps en séparant chaque identifiant de correctif supplémentaire par un espace :

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

Pour rétablir tous les correctifs appliqués :

```bash
./vendor/bin/magento-patches revert --all
```

Vous devez nettoyer le cache après le rétablissement des correctifs pour afficher les modifications dans l’application Adobe Commerce :

```bash
./bin/magento cache:clean
```

## Obtenir des mises à jour

Adobe Commerce publie régulièrement de nouveaux correctifs individuels. Vous devez mettre à jour le [!DNL Quality Patches Tool] pour obtenir de nouveaux correctifs individuels :

```bash
composer update magento/quality-patches
```

Affichez les correctifs ajoutés :

>[!TIP]
>
>Les nouveaux correctifs ajoutés s’affichent au bas du tableau.

```bash
./vendor/bin/magento-patches status
```

## Réappliquer les correctifs après une mise à niveau {#re-apply-patches-after-an-upgrade}

Lorsque vous effectuez une mise à niveau vers une nouvelle version d’Adobe Commerce, vous devez réappliquer les correctifs si ceux-ci ne sont pas inclus dans la nouvelle version.

Pour appliquer à nouveau les correctifs :

1. Mettez à jour le [!DNL Quality Patches Tool] :

   ```bash
   composer update magento/quality-patches.
   ```

1. Ouvrez la liste des correctifs précédemment appliqués, ce qui a été recommandé dans [Appliquer des correctifs individuels](#apply-individual-patches).

1. Appliquez les correctifs suivants :

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
   >Lorsque vous exécutez la commande `status`, les correctifs qui étaient inclus dans la nouvelle version ne s&#39;affichent plus dans le tableau des correctifs disponibles.

## Journalisation

Le [!DNL Quality Patches Tool] consigne toutes les opérations dans le fichier `<Magento_root>/var/log/patch.log`.
