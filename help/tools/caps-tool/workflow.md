---
title: Fonctionnement  [!DNL Cloud Automation Patching Service (CAPS)]  workflow
description: Découvrez le processus  [!DNL Cloud Automation Patching Service (CAPS)]  workflow, notamment la terminologie, les phases de workflow et les opérations pour une gestion automatisée des correctifs.
hide: true
hidefromtoc: true
source-git-commit: eff8c0ae9e1d9db6b46ba7cfbb915685ab5b194d
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 0%

---

# Fonctionnement du workflow [!DNL Cloud Automation Patching Service (CAPS)]

Cette rubrique présente de manière générale le fonctionnement des opérations de correctifs à l’aide de [!DNL CAPS (Cloud Automation Patching Service)].

## Terminologie

* **Opérations** - principales actions effectuées par [!DNL CAPS] :
   * Appliquer
   * Rétablir
* **Phases** - les trois phases du workflow :
   * Vérification préliminaire
   * Application de correctifs
   * Validation
* **Environnement** : environnement Adobe Commerce Cloud dans lequel les correctifs sont appliqués.

## Opérations

[!DNL CAPS] prend en charge deux principales *opérations* pour gérer les correctifs dans votre environnement Adobe Commerce Cloud :

* **Opération d’application** - ajoute les modifications de correctif à votre base de code via un processus sécurisé et validé. Les correctifs sont appliqués en plaçant les fichiers de correctifs dans le dossier « m2-hotfix ».

* **Rétablir l’opération** - supprime les correctifs précédemment appliqués de votre base de code en supprimant les fichiers de correctifs du dossier « m2-hotfixes ».

>[!IMPORTANT]
>
>Les opérations de restauration ne sont disponibles que pour les correctifs appliqués à l’origine via [!DNL CAPS]. Les correctifs appliqués manuellement ou par d’autres méthodes ne peuvent pas être rétablis à l’aide de ce service.

## Phases

Le workflow [!DNL CAPS] utilise trois *phases* qui sont toujours exécutées dans cet ordre pour s’assurer que les correctifs sont appliqués de manière sûre et fiable :

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

La phase d&#39;application du correctif applique ou rétablit le correctif dans un environnement d&#39;intégration temporaire à des fins de test. Au cours de cette étape, [!DNL CAPS] crée un environnement de test temporaire pour appliquer et tester en toute sécurité le correctif avant d’apporter des modifications à votre environnement réel.

Cette approche permet d’obtenir les éléments suivants :

* **Sécurité** - maintient votre environnement cible intact jusqu’à ce que le patch soit validé
* **Tests** - dans un environnement réel avant d’affecter la production
* **Fonction de restauration** - si des problèmes sont détectés
* **Isolation** - pour chaque opération de correctif

#### Étape 2a : création de l’environnement d’intégration

**Création de branche** - [!DNL CAPS] crée une branche d’environnement d’intégration temporaire nommée `{target-environment}-CAPS-{patch-id}`

**Configuration de l’environnement** - L’environnement d’intégration est créé en tant qu’enfant de votre environnement cible

**Synchronisation du code** - L’environnement d’intégration hérite de l’état exact de votre environnement cible

**Besoins en ressources** - [!DNL CAPS] crée un environnement temporaire à l’aide de la base de code de votre environnement cible. Selon la documentation Adobe Commerce Cloud, chaque environnement (y compris les environnements d’intégration) dispose d’une allocation de stockage distincte en fonction de votre plan de stockage sous-traité. La quantité de stockage sous-traitée représente le stockage total pour chaque environnement. Dans la plupart des cas, vous ne rencontrerez aucun problème lié aux limitations de ressources. Si vous rencontrez une erreur liée aux limitations de ressources, vérifiez la taille de votre application et le stockage sous contrat dans votre forfait.

#### Étape 2b : application de correctifs dans l’environnement d’intégration

**Test sécurisé** - Le correctif est appliqué à l’environnement d’intégration et non directement à votre environnement cible

**Gestion des fichiers** - Les fichiers correctifs sont placés dans le répertoire `m2-hotfixes/`

**Opérations Git** - Les modifications sont validées et transmises à la branche de l’environnement d’intégration

**Activation de l’environnement** - L’environnement d’intégration est activé pour déployer le code corrigé

#### Étape 2c : fusion vers l’environnement cible

**Extraction de l’environnement** - Extrait [!DNL CAPS] votre environnement cible localement

**Opération de fusion** - La branche d’environnement d’intégration est fusionnée dans l’environnement cible

**Résolution des conflits** - Si des conflits se produisent, ils sont résolus automatiquement lorsque cela est possible

**Déploiement** - Les modifications fusionnées sont déployées dans votre environnement cible

**Vérification** - [!DNL CAPS] vérifie que la fusion a réussi et que les environnements sont synchronisés

**Nettoyage de l’environnement** - L’environnement d’intégration temporaire est supprimé pour libérer des ressources

## Cycle de vie de l’environnement d’intégration

Les environnements d’intégration ont un cycle de vie spécifique pendant l’étape d’application des correctifs :

* **Création** - Créé au début de l’étape d’application des correctifs
* **Période d’activité** - Restez actif pendant l’application du correctif et les tests
* **Nettoyage** - Supprimé automatiquement après une fusion réussie ou si l’opération échoue

### Phase 3 : validation

La phase de validation garantit le bon fonctionnement de l’application de correctifs et effectue des contrôles d’intégrité.

**Que se passe-t-il**

* **Contrôle de l’intégrité de l’application** - vérifie que l’application démarre et s’exécute correctement
* **Nettoyage** - supprime l’environnement temporaire, met à jour les journaux et notifie l’achèvement de l’opération.

## Indicateurs de succès

**Appliquer l’opération :**

* « Traitement terminé avec succès » - Correctif appliqué sans problème
* « Correctif appliqué » - Le correctif était déjà présent (aucune action n’est nécessaire).
* Le fichier correctif a été placé dans le dossier « m2-hotfixes ».
* Tous les contrôles de validation réussissent
* Vérification de l’intégrité de l’application réussie

**Rétablir l’opération :**

* « Traitement terminé avec succès » - Correctif rétabli sans problème
* « Le correctif a été rétabli » - Le correctif a déjà été rétabli (aucune action nécessaire)
* Fichier de correctif supprimé avec succès du dossier « m2-hotfix »
* Tous les contrôles de validation réussissent
* Vérification de l’intégrité de l’application réussie

## Sauvegardes de l’environnement de production

[!DNL CAPS] comprend des mesures de protection spécifiques pour les environnements de production afin d&#39;éviter les interruptions accidentelles et de s&#39;assurer que les correctifs sont validés en toute sécurité au préalable.

### Conditions préalables pour l’application de correctifs en production

Avant d’appliquer des correctifs aux environnements de production, [!DNL CAPS] vérifie deux conditions critiques :

* **Mode de maintenance** - Le magasin doit être en mode de maintenance.
* **Tâches Cron désactivées** - Les tâches Cron doivent être désactivées

Si l’une de ces conditions n’est pas remplie, l’application du correctif est bloquée et l’utilisateur en est informé.

## Rubriques connexes

* [Présentation de CAPS](intro.md)
* [Accès](access.md)
* [Bonnes pratiques](best-practices.md)
* [Dépannage](troubleshooting.md)
