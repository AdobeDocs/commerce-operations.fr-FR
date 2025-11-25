---
title: Guide de dépannage d’[!DNL Cloud Automation Patching Service (CAPS)]
description: Résolution des problèmes courants et des messages d’erreur dans  [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 0%

---

# Guide de dépannage d’[!DNL Cloud Automation Patching Service (CAPS)]

Lors de l’utilisation de [!DNL CAPS] pour les opérations d’application de correctifs, vous pouvez rencontrer des messages d’erreur et des problèmes qui peuvent empêcher la réussite de l’application de correctifs ou la réversion. Ce guide fournit des solutions aux problèmes les plus courants.

## Étapes de dépannage rapide

### Si l’opération de correctif échoue

* Vérifiez le statut de l’opération pour identifier l’étape qui a échoué
* Consulter les messages d’erreur pour des raisons d’échec spécifiques
* Consultez les journaux d’erreurs pour obtenir des détails techniques
* Suivez les solutions fournies dans ce guide

### Durée des opérations de correctif

Pour la plupart des environnements, la chronologie suivante décrit la durée des opérations d’application de correctifs, mais elle peut être plus longue en fonction de la taille et de la complexité de l’environnement :

* **Pré-traitement :** 2-5 minutes
* **Application d’un correctif :** 5 à 15 minutes
* **Post-traitement :** 10 à 40 minutes
* **Total:** 15-60 minutes

### Annulation d’un correctif en cours

>[!WARNING]
>
>Une fois qu’une opération de correctif commence, elle doit être autorisée à se terminer. Le système comprend des procédures de nettoyage qui s’exécutent même en cas d’échec des opérations. L’interruption du processus peut laisser votre environnement dans un état incohérent.

## Messages de succès courants

* **« Traitement terminé avec succès »** - Le correctif a été appliqué/annulé avec succès sans problème.

* **« Le correctif a été appliqué »** - Vous essayez d’appliquer un correctif qui a déjà été appliqué. Le système a détecté que le correctif est déjà présent dans votre environnement. Aucune action n’est nécessaire.

* **« Correctif annulé »** - Vous essayez d’annuler un correctif qui a déjà été annulé. Le système a détecté que le correctif n&#39;est pas actuellement appliqué. Aucune action n’est nécessaire.

## Messages d’erreur courants et solutions

### Erreurs d’application de correctif

#### « Impossible d’appliquer le correctif, car [!DNL CAPS] a détecté ces problèmes avec votre base de code ou le fichier correctif. »

**Le cas échéant :** lors de la vérification préliminaire

**Cause :** le correctif est en conflit avec votre base de code actuelle OU il y a un problème avec le correctif lui-même

**Solutions:**

* Consultez les journaux d’erreurs détaillés fournis pour déterminer s’il s’agit d’un problème de base de code ou de correctif
* Rechercher les personnalisations en conflit dans votre code
* Vérifiez que le correctif est compatible avec votre version d’Adobe Commerce
* Pensez à résoudre les conflits manuellement ou contactez l’assistance

#### « Ce correctif n’a pas été géré par [!DNL CAPS]. Impossible d’annuler »

**Lorsque cela se produit :** pendant les opérations de restauration

**Cause :** vous essayez d’annuler un correctif qui n’a pas été appliqué via [!DNL CAPS]

**Solution :** utilisez la même méthode que celle utilisée pour appliquer le correctif à l’origine, ou contactez le support pour obtenir une assistance manuelle

### Erreurs d’environnement et de validation

#### « L’environnement n’est pas synchronisé avec le parent »

**Lorsque cela se produit :** lors de la validation

**Cause :** votre environnement d’intégration diffère de l’environnement parent

**Solutions:**

* Synchroniser votre environnement avec la branche parent
* Relancez l’opération de correctif
* Contactez l’assistance si les problèmes de synchronisation persistent

#### « Les mesures de protection de l’environnement de production ne sont pas respectées »

**Le cas échéant :** lors de la vérification préliminaire des environnements de production.

**Cause :** l’environnement de production ne répond pas aux conditions de sécurité requises

**Solutions:**

* Activation du mode de maintenance pour votre magasin de production
* Désactivation des tâches cron dans votre environnement de production
* Vérifiez que les deux conditions sont remplies avant de réessayer

>[!IMPORTANT]
>
> [!DNL CAPS] n’active pas automatiquement le mode de maintenance ou ne désactive pas les tâches cron. Vous devez effectuer ces tâches en externe

#### « Le correctif a été appliqué, mais le contrôle d’intégrité a échoué. Envisagez de revenir en arrière. »

**Le cas échéant :** après l’application du correctif pendant la validation

**Cause :** le correctif a été appliqué avec succès, mais les contrôles d’intégrité ont échoué

**Solutions:**

* Vérification des journaux d’application pour identifier les erreurs spécifiques
* Tester manuellement les fonctionnalités critiques
* Pensez à rétablir le correctif si les problèmes persistent
* Contactez l’assistance si vous avez besoin d’aide

### Erreurs d’authentification et d’accès

#### « Échec de l’authentification pour le référentiel Adobe Commerce »

**Le cas échéant :** à n’importe quelle étape

**Cause :** informations d’identification de référentiel Adobe Commerce non valides ou expirées

**Solutions:**

Il existe deux options recommandées pour résoudre ce problème :

**Option 1 : Correction de `env:COMPOSER_AUTH` variable au niveau de l’environnement (recommandée)**

* Vérifiez que vous avez configuré les informations d’identification appropriées pour `env:COMPOSER_AUTH`.
* Accédez à la configuration globale en cliquant sur l’icône d’engrenage en haut à gauche de l’interface utilisateur de votre projet cloud, puis sélectionnez l’onglet **Variables**.
* Veillez à sélectionner _Disponible au moment de la création_ et désélectionnez _Disponible au moment de l’exécution_.

Si l’option 1 ne résout pas votre problème, passez à l’option 2.

**Option 2 : créer et déployer `auth.json` fichier manuellement**

* SSH dans votre serveur.
* Récupérez le contenu de la variable de `env:COMPOSER_AUTH` actuelle à l’aide de :\
  `echo $COMPOSER_AUTH`
* Copiez tout le contenu de l’étape ci-dessus (au format JSON).
* Créez un fichier nommé `auth.json` avec ces contenus.
* Validez ce fichier `auth.json` nouvellement créé dans le répertoire racine de votre référentiel.
* Déclenchez un nouveau déploiement .

#### « Autorisations insuffisantes pour l’accès à l’environnement »

**Lorsque cela se produit :** lors de la création ou de l’accès à l’environnement

**Cause :** votre compte utilisateur ne dispose pas des autorisations nécessaires

**Solutions:**

* Vérifier le rôle et les autorisations de votre utilisateur
* Contactez votre administrateur système
* Vérification des autorisations de gestion de l’environnement
* Vérifiez que vous disposez des autorisations de déploiement

### Erreurs de ressource et de quota

#### « Quota d’environnement dépassé »

**Lorsque cela se produit :** lors de la création de l’environnement

**Cause :** vous avez atteint la limite de votre environnement.

**Solutions:**

* Désactiver les environnements inutilisés
* Nettoyage des anciennes branches et des anciens déploiements
* Contacter l’assistance pour demander une augmentation de quota
* Envisagez de mettre à niveau votre plan

#### « Ressources insuffisantes pour l’opération »

**Le cas échéant :** à n’importe quelle étape

**Cause :** votre environnement manque de CPU, de mémoire ou de stockage

**Solutions:**

* Vérifier l’utilisation des ressources de votre environnement
* Libérez des ressources en nettoyant les fichiers
* Attendre que les ressources soient disponibles
* Contactez l’assistance si les problèmes de ressources persistent

## Obtention d’aide

**Quand contacter l’assistance :**

Contactez l’assistance Adobe Commerce Cloud lorsque :

* Les messages d’erreur ne sont pas clairs ou ne sont pas suffisamment détaillés.
* Les opérations de correctif échouent systématiquement
* Vous avez besoin d’aide pour la résolution manuelle des conflits
* Les contrôles d’intégrité échouent, mais la cause n’est pas apparente
* Vous avez besoin d’aide pour résoudre les problèmes de synchronisation de l’environnement.

**Informations à fournir :**

Lorsque vous contactez l’assistance, fournissez les informations suivantes :

* **Identifiant de projet** - Identifiant de votre projet Adobe Commerce Cloud
* **Identifiant d’environnement** - Environnement spécifique dans lequel le problème s’est produit
* **Identifiant de l’opération** - Identifiant de l’opération [!DNL CAPS]
* **Détails de l’erreur** - Messages d’erreur complets et journaux
* **Procédure à suivre** - Que faisiez-vous lorsque l’erreur s’est produite ?
* **Tentatives précédentes** - Ce que vous avez déjà essayé de résoudre le problème

### Ressources supplémentaires

Pour obtenir des informations techniques plus détaillées :

* Consultez les journaux d’erreurs complets fournis avec les opérations ayant échoué
* Consultez la documentation Adobe Commerce pour obtenir des conseils spécifiques aux correctifs
* Contactez l’assistance Adobe Commerce Cloud pour les problèmes spécifiques à un environnement

### Rubriques connexes

* [Documentation Adobe Commerce Cloud](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/overview)
* [Guide d’installation d’Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/overview)
* [Présentation de CAPS](intro.md)
* [Accès](access.md)
* [Workflow](workflow.md)
* [Bonnes pratiques](best-practices.md)
