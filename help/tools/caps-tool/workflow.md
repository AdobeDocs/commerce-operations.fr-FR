---
title: Présentation du workflow [!DNL Adobe Commerce Patching Automation]
description: Découvrez le processus  [!DNL Adobe Commerce Patching Automation]  workflow, notamment la terminologie, les phases de workflow et les opérations pour une gestion automatisée des correctifs.
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 0%

---

# Présentation du workflow [!DNL Adobe Commerce Patching Automation]

Cette rubrique présente de manière générale le fonctionnement des opérations de correctifs à l’aide de [!DNL Adobe Commerce Patching Automation].

## Terminologie

* **Opérations** - les principales actions effectuées par le service :
  * Appliquer
  * Rétablir
* **Phases** - les trois phases du workflow :
  * Vérification préliminaire
  * Application de correctifs
  * Validation
* **Environnement** : environnement Adobe Commerce Cloud dans lequel les correctifs sont appliqués.

## Opérations

[!DNL Patching Automation] prend en charge deux principales *opérations* pour gérer les correctifs dans votre environnement Adobe Commerce Cloud :

* **Opération d’application** - ajoute les modifications de correctif à votre base de code via un processus sécurisé et validé. Les correctifs sont appliqués en plaçant les fichiers de correctifs dans le dossier `m2-hotfixes`.

* **Rétablir l’opération** - supprime les correctifs précédemment appliqués de votre base de code en supprimant les fichiers de correctifs du dossier `m2-hotfixes`.

>[!IMPORTANT]
>
>Les opérations de restauration ne sont disponibles que pour les correctifs appliqués à l’origine via [!DNL Patching Automation]. Les correctifs appliqués manuellement ou par d’autres méthodes ne peuvent pas être rétablis à l’aide de ce service.

## Phases

Le workflow [!DNL Patching Automation] utilise trois *phases* qui sont toujours exécutées dans cet ordre pour s’assurer que les correctifs sont appliqués de manière sûre et fiable :

* **Vérification préliminaire** - Valide la compatibilité des correctifs et la préparation de l’environnement.
* **Application de correctifs** - applique ou rétablit le correctif dans un environnement d’intégration.
* **Validation** - valide l’application de correctif et effectue des contrôles d’intégrité.

## Détails de la phase

### Phase 1 : vérification préliminaire

La phase de vérification préliminaire confirme que le correctif peut être appliqué en toute sécurité à votre environnement.

**Que se passe-t-il**

* **Protection de l’environnement de production** (environnements de production uniquement) :
  * Vérifie si le magasin est en mode de maintenance
  * Vérifie que les tâches cron sont désactivées.
  * Bloque l’application de correctifs si les conditions ne sont pas remplies
  * Affiche la boîte de dialogue de confirmation si les conditions sont remplies
* **Validation du correctif** - vérifie que le fichier correctif est valide et compatible
* **Évaluation environnementale** - vérifie la préparation et les ressources en matière d&#39;environnement
* **Détection des conflits** - identifie les conflits potentiels avec le code existant
* **Vérification des dépendances** - valide la compatibilité des versions d’Adobe Commerce.

### Phase 2 : application de correctifs

La phase d&#39;application du correctif applique ou rétablit le correctif dans un environnement d&#39;intégration temporaire. Au cours de cette étape, le service crée un environnement d’intégration temporaire pour appliquer le correctif en toute sécurité, confirmer qu’il se déploie correctement et vérifier qu’il réussit un contrôle d’intégrité avant d’apporter des modifications à votre environnement réel.

Cette approche permet d’obtenir les éléments suivants :

* **Sécurité** : conserve votre environnement cible intact jusqu’à ce que l’environnement d’intégration se déploie avec succès et passe son contrôle d’intégrité
* **Fonction de restauration** - si des problèmes sont détectés
* **Isolation** - pour chaque opération de correctif

#### Étape 2a : création de l’environnement d’intégration

**Création de branche** - [!DNL Patching Automation] crée une branche d’environnement d’intégration temporaire nommée `{target-environment}-CAPS-{patch-id}`

**Configuration de l’environnement** - L’environnement d’intégration est créé en tant qu’enfant de votre environnement cible

**Synchronisation du code** - L’environnement d’intégration hérite de l’état exact du code de votre environnement cible (même base de code)

**Pas de clonage de données** - L’environnement d’intégration ne reçoit pas de copie des données de l’environnement cible (base de données, média ou autre contenu stocké). Seule la base de code est utilisée pour appliquer et vérifier le correctif

**Besoins en ressources** - La capacité de stockage totale de votre projet cloud est définie dans votre contrat. (Vérifiez sur la page ou la `magento-cloud subscription:info` de votre compte). L’allocation de disque de chaque environnement est configurée séparément, via la propriété `disk` dans `.magento.app.yaml`/`.magento/services.yaml`. Voir [Gérer l’espace disque](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space) pour plus d’informations. Si une opération de correctif échoue en raison de limitations de stockage, comparez l’utilisation du disque de votre environnement d’intégration (`magento-cloud db:size`/`magento-cloud mount:size`) à son allocation configurée.

#### Étape 2b : application de correctifs dans l’environnement d’intégration

**Test sécurisé** - Le correctif est appliqué à l’environnement d’intégration et non directement à votre environnement cible

**Gestion des fichiers** - Les fichiers correctifs sont placés dans le dossier `m2-hotfixes`

**Opérations Git** - Les modifications sont validées et transmises à la branche de l’environnement d’intégration

**Activation de l’environnement** - L’environnement d’intégration est activé pour déployer le code corrigé

**Contrôle de l’intégrité** - Une fois activé, [!DNL Patching Automation] confirme ce qui suit avant de poursuivre la fusion : l’environnement d’intégration déployé avec succès et est intègre, l’application démarre et ses connexions de base de données et de cache sont accessibles.

>[!NOTE]
>
>Si votre projet utilise un référentiel GitHub externe, le service gère automatiquement l’authentification à l’aide de l’application [[!DNL Patching Automation] GitHub](github-integration.md). Aucune information d’identification supplémentaire n’est requise, hormis l’installation de l’application.

#### Étape 2c : fusion vers l’environnement cible

**Vérification de la synchronisation** - Avant la fusion, le service confirme que l’environnement d’intégration est toujours actif, synchronisé avec l’environnement cible et intègre. Si la cible a changé lors de l&#39;application du correctif, l&#39;opération s&#39;arrête ici au lieu de fusionner

**Extraction d’environnement** - Le service extrait votre environnement cible localement

**Opération de fusion** - La branche d’environnement d’intégration est fusionnée dans l’environnement cible

**Gestion des conflits** - Si un conflit de fusion se produit, l’opération échoue et est signalée comme une erreur - elle n’est pas résolue automatiquement

**Déploiement** - Les modifications fusionnées sont déployées dans votre environnement cible

**Vérification** - Le service vérifie que la fusion a réussi et que les environnements sont synchronisés

### Cycle de vie de l’environnement d’intégration

Les environnements d’intégration ont un cycle de vie spécifique pendant l’étape d’application des correctifs :

* **Création** - Créé au début de l’étape d’application des correctifs
* **Période d’activité** - Restez actif pendant l’application du correctif et les tests
* **Nettoyage** - Supprimé immédiatement si l’opération échoue pendant la phase d’application du correctif, avant la fusion. Sinon, supprimé pendant la phase de validation, après la fusion, que la validation soit réussie ou non

### Phase 3 : validation

La phase de validation confirme que l’application corrigée démarre correctement et passe avec succès un contrôle d’intégrité.

**Que se passe-t-il**

* **Contrôle de l’intégrité de l’application** : vérifie que l’application démarre et s’exécute correctement, et que ses connexions de base de données et de cache sont accessibles
* **Nettoyage** - supprime l’environnement d’intégration temporaire et met à jour le statut de la tâche pour refléter l’achèvement de la tâche. L’activité de l’environnement reste visible dans le flux d’activités de votre projet.

>[!IMPORTANT]
>
>Contrairement aux phases 1 et 2, ce contrôle d’intégrité s’exécute *après* la fusion du correctif dans votre environnement cible. En cas d’échec, la fusion n’est pas automatiquement restaurée. Votre environnement cible peut rester dans un état endommagé et une intervention manuelle (comme la restauration du correctif) est nécessaire pour le restaurer. Voir [Dépannage](troubleshooting.md) pour savoir comment procéder si cela se produit.

## Indicateurs de succès

**Appliquer l’opération :**

* « Traitement terminé avec succès » - Correctif appliqué sans problème
* « Correctif appliqué » - Le correctif était déjà présent (aucune action n’est nécessaire).
* Fichier de correctif placé dans `m2-hotfixes` dossier
* Tous les contrôles de validation réussissent
* Vérification de l’intégrité de l’application réussie

**Rétablir l’opération :**

* « Traitement terminé avec succès » - Correctif rétabli sans problème
* « Le correctif a été rétabli » - Le correctif a déjà été rétabli (aucune action nécessaire)
* Fichier de correctif supprimé du dossier `m2-hotfixes`
* Tous les contrôles de validation réussissent
* Vérification de l’intégrité de l’application réussie

## Sauvegardes de l’environnement de production

L’application ou la restauration de correctifs sur un environnement de production comporte plus de risques que sur d’autres environnements. Par conséquent, [!DNL Patching Automation] comprend deux mesures de protection spécifiques à la production.

### Confirmation avant de commencer

Avant qu’une opération d’application ou de restauration ne commence dans un environnement de production, vous êtes invité à confirmer l’opération dans une boîte de dialogue. Cette étape de confirmation vous protège contre le démarrage accidentel d’une tâche en production.

### Conditions préalables recommandées

Adobe recommande d’activer le mode de maintenance et de désactiver les tâches cron avant d’appliquer les correctifs à un environnement de production. Par défaut, [!DNL Patching Automation] vérifie que les deux conditions sont remplies et bloque l’opération avec une notification si l’une des conditions n’est pas remplie. Si vous comprenez les risques de continuer sans le mode de maintenance ou avec les tâches cron activées, cochez la case de remplacement dans l’interface utilisateur pour contourner cette vérification.

* **Mode de maintenance** - Activation recommandée
* **Tâches cron** - Désactivation recommandée

## Rubriques connexes

* [Présentation de l&#39;automatisation des correctifs](intro.md)
* [Accès](access.md)
* [Intégration de GitHub](github-integration.md)
* [Bonnes pratiques](best-practices.md)
* [Dépannage](troubleshooting.md)
