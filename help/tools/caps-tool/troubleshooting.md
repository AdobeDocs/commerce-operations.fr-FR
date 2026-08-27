---
title: Guide de dépannage d’[!DNL Adobe Commerce Patching Automation]
description: Résolution des problèmes courants et des messages d’erreur dans  [!DNL Adobe Commerce Patching Automation]
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 0%

---

# Guide de dépannage d’[!DNL Adobe Commerce Patching Automation]

Lors de l’utilisation de [!DNL Patching Automation] pour les opérations d’application de correctifs, vous pouvez rencontrer des messages d’erreur et des problèmes qui peuvent empêcher la réussite de l’application de correctifs ou la réversion. Ce guide fournit des solutions aux problèmes les plus courants.

## Étapes de dépannage rapide

### Si l’opération de correctif échoue

* Vérifiez le statut de l’opération pour identifier l’étape qui a échoué
* Consulter les messages d’erreur pour des raisons d’échec spécifiques
* Consultez les journaux d’erreurs pour obtenir des détails techniques
* Suivez les solutions fournies dans ce guide

>[!TIP]
>
>Dans la console cloud, les journaux de déploiement sont disponibles à partir du flux d’activités de votre projet, même après la suppression d’un environnement d’intégration temporaire.

### Durée des opérations de correctif

Pour la plupart des environnements, la chronologie suivante décrit la durée des opérations d’application de correctifs, mais elle peut être plus longue en fonction de la taille et de la complexité de l’environnement :

* **Pré-traitement :** 2-5 minutes
* **Application d’un correctif :** 5 à 15 minutes
* **Post-traitement :** 10 à 40 minutes
* **Total:** 15-60 minutes

>[!NOTE]
>
>Le temps de post-traitement est estimé à partir de l’historique de déploiement de votre environnement. Il peut donc se situer en dehors de la plage ci-dessus pour les environnements à déploiement inhabituellement rapide ou lent.

### Annulation d’un correctif en cours

>[!WARNING]
>
>Une fois qu’une opération de correctif commence, elle doit être autorisée à se terminer. Le système comprend des procédures de nettoyage qui s’exécutent même en cas d’échec des opérations. L’interruption du processus peut laisser votre environnement dans un état incohérent.

## Messages de succès courants

* **« Traitement terminé avec succès »** - Le correctif a été appliqué/annulé avec succès sans problème.

* **« Le correctif a été appliqué »** - Vous essayez d’appliquer un correctif qui a déjà été appliqué. Le système a détecté que le correctif est déjà présent dans votre environnement. Aucune action n’est nécessaire.

* **« Correctif annulé »** - Vous essayez d’annuler un correctif qui a déjà été annulé. Le système a détecté que le correctif n&#39;est pas actuellement appliqué. Aucune action n’est nécessaire.

## Messages d’erreur courants et solutions

>[!NOTE]
>
>Toutes les erreurs possibles ne sont pas répertoriées ci-dessous. Un échec non répertorié lors de la vérification préliminaire apparaît comme une « Erreur lors de la vérification préliminaire » générique ; un échec non répertorié lors de la validation apparaît comme une « Erreur lors du post-traitement » générique ; contactez l’assistance avec le texte exact de l’erreur dans les deux sens. Lors de l&#39;application de correctifs, un échec inattendu affiche directement le message d&#39;erreur sous-jacent brut au lieu de l&#39;un des secours génériques.

### Erreurs de préparation à l’environnement

#### « Le dernier déploiement n’a pas réussi. Assurez-vous que l’environnement est stable avant d’appliquer ou de rétablir les correctifs. »

**Le cas échéant :** au début de la vérification préliminaire, avant toute validation spécifique au correctif

**Cause :** le déploiement le plus récent de votre environnement cible ne s’est pas terminé correctement

**Solution :** redéployez votre environnement cible et vérifiez que le déploiement est terminé (vérifiez son journal de déploiement dans la console Cloud) avant de retenter l’opération de correctif.

### Erreurs d’application de correctif

#### « Impossible d’appliquer le correctif, car [!DNL Patching Automation] a détecté ces problèmes avec votre base de code ou le fichier correctif. »

**Le cas échéant :** lors de la vérification préliminaire

**Cause :** le correctif est en conflit avec votre base de code actuelle OU il y a un problème avec le correctif lui-même

**Solutions:**

* Consultez les journaux d’erreurs détaillés fournis pour déterminer s’il s’agit d’un problème de base de code ou de correctif
* Rechercher les personnalisations en conflit dans votre code
* Vérifiez que le correctif est compatible avec votre version d’Adobe Commerce
* Pensez à résoudre les conflits manuellement ou contactez l’assistance

#### « Vous essayez d’annuler un correctif qui n’a pas été appliqué via [!DNL Patching Automation]. Il est probable que le correctif ait été appliqué manuellement. »

**Lorsque cela se produit :** pendant les opérations de restauration

**Cause :** vous essayez d’annuler un correctif qui n’a pas été appliqué via [!DNL Patching Automation]

**Solution :** utilisez la même méthode que celle utilisée pour appliquer le correctif à l’origine, ou contactez le support pour obtenir une assistance manuelle

### Erreurs d’environnement et de validation

#### « L’environnement n’est pas synchronisé avec le parent »

**Le cas échéant :** lors de la validation, dans la vérification de la synchronisation avant la fusion, avant la fusion de l’environnement d’intégration dans votre environnement cible

**Cause :** votre environnement d&#39;intégration diffère de l&#39;environnement parent, généralement parce que l&#39;environnement cible a changé pendant le test du correctif

**Solutions:**

* Réessayez l’opération de correctif une fois que l’environnement cible est stable
* Évitez d’apporter des modifications à l’environnement cible lorsqu’une opération de correction est en cours
* Contactez l’assistance si les problèmes de synchronisation persistent

#### « Échec de la vérification après fusion : les environnements ne sont pas synchronisés après la fusion. »

**Le cas échéant :** lors de la validation, une fois que l’environnement d’intégration a déjà été fusionné dans votre environnement cible

**Cause :** le code des deux environnements ne correspond pas après la fusion, généralement un délai de propagation temporaire de l’API Platform.sh plutôt qu’un véritable conflit

**Solutions:**

* Patientez quelques minutes et vérifiez à nouveau le statut de l’environnement. Ce problème se résout souvent tout seul
* Si les environnements ne correspondent toujours pas après quelques minutes, contactez l’assistance Adobe.

#### « Impossible de créer une tâche de correction dans un environnement de production lorsque cron est activé et que le mode de maintenance est désactivé. Veuillez activer le mode de maintenance et désactiver les tâches cron avant d’appliquer les correctifs. »

**Le cas échéant :** lors de la vérification préliminaire des environnements de production.

**Cause :** l’environnement de production ne répond pas aux conditions de sécurité requises

**Solutions:**

* Activation du mode de maintenance pour votre magasin de production
* Désactivation des tâches cron dans votre environnement de production
* Vérifiez que les deux conditions sont remplies avant de réessayer
* Vous pouvez également cocher la case de remplacement dans l’interface utilisateur pour ignorer ces vérifications et continuer quand même. N’utilisez l’option de remplacement que si vous comprenez le risque lié à l’application de correctifs à la production sans ces mesures de protection en place

>[!IMPORTANT]
>
> [!DNL Patching Automation] n’active pas automatiquement le mode de maintenance ou ne désactive pas les tâches cron. Vous devez effectuer ces tâches en externe

#### « L’opération de correction est terminée, mais le contrôle de l’intégrité de l’environnement a échoué. Cela indique des problèmes potentiels liés au déploiement d’. Vérifiez le statut de l’environnement et envisagez d’annuler la modification. »

**Le cas échéant :** après l’application du correctif ou la réversion, pendant la validation

**Cause :** le correctif a été appliqué ou annulé avec succès, mais la vérification d’intégrité suivante a échoué

**Solutions:**

* Testez les workflows d’extraction et d’administration de storefront et critical pour vérifier si les clients sont réellement affectés
* Dans la console cloud, examinez le statut de l’environnement et examinez les journaux d’application et de déploiement dans le flux de projets **Activité**. Recherchez les erreurs associées à l’opération ou au déploiement des correctifs.
* Déclenchez un redéploiement manuel pour déterminer si l’échec du contrôle de l’intégrité a été causé par un problème transitoire de déploiement ou d’infrastructure.
* Si le problème persiste, rétablissez le correctif. Si le correctif est géré par [!DNL Patching Automation] et que l’opération est disponible, sélectionnez [!UICONTROL Revert]. Si le correctif est un correctif personnalisé du répertoire `m2-hotfixes`, supprimez le fichier de correctif du référentiel du projet. Validez et envoyez la modification, puis redéployez l’environnement.
* Si le problème persiste, contactez l’assistance Adobe. Incluez les informations suivantes dans votre demande d’assistance : ID du projet d’assistance, ID de l’environnement et ce message exact : la dernière opération ne s’est pas correctement terminée. L’assistance devra donc peut-être confirmer l’état de l’environnement.

### Erreurs d’authentification et d’accès

#### « Accès refusé »

**Le cas échéant :** lorsque votre compte ne dispose pas des autorisations requises lors de la création ou de l’accès à l’environnement

**Cause :** votre compte utilisateur ne dispose pas des autorisations nécessaires

**Solutions:**

* Vérifier le rôle et les autorisations de votre utilisateur
* Contactez votre administrateur système
* Vérification des autorisations de gestion de l’environnement
* Vérifiez que vous disposez des autorisations de déploiement

### Erreurs d’intégration GitHub

#### « Aucune information d’identification Git disponible pour le fournisseur « github ». Installez l’application GitHub d’automatisation des correctifs pour ce référentiel. »

**Le cas échéant :** lors des opérations de correctif pour les projets connectés à GitHub.

**Cause :** l’application [!DNL Patching Automation] GitHub n’est pas installée sur votre référentiel

**Solution :** suivez les étapes de la section [Configurer l’intégration GitHub pour [!DNL Patching Automation]](github-integration.md)

#### « Échec de la requête d’API GitHub »

**Lorsque cela se produit :** lors des opérations de correctif pour les projets connectés à GitHub

**Cause :** un problème temporaire a empêché le service de se connecter à GitHub

**Solution :** patientez quelques minutes et recommencez l’opération. Si l’erreur persiste, contactez l’[assistance d’Adobe Commerce Cloud](https://experienceleague.adobe.com/home?lang=fr#support)

#### « Environnement non créé pendant la temporisation » (projet connecté à GitHub)

**Lorsque cela se produit :** lors de la création de l’environnement d’intégration

**Cause :** l’option `fetch-branches` est désactivée pour l’intégration GitHub du projet. Par conséquent, les branches temporaires transmises par le service ne sont pas synchronisées et l’environnement d’intégration n’est jamais créé.

**Solution :** activez l’option [`fetch-branches` de l’intégration](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration) puis relancez l’opération. Voir [&#x200B; Configuration de l’intégration GitHub pour  [!DNL Patching Automation]](github-integration.md).

### Erreurs d’activation de l’environnement

#### « Impossible d’activer l’environnement d’intégration. »

**Le cas échéant :** lorsque [!DNL Patching Automation] ne pouvez pas activer l’environnement d’intégration temporaire requis pour tester le correctif en toute sécurité.

**Cause :** dépend des détails supplémentaires affichés à côté de l’erreur :

**Si les détails mentionnent le compositeur ou les packages Adobe Commerce :**

* Connectez-vous à [&#128279;](https://account.magento.com/) (ou demandez au propriétaire de votre compte de le faire) et vérifiez que votre compte a accès à la base de code Commerce Enterprise.
* Vérifiez que la paire de clés publique/privée du compositeur de votre projet est correcte — voir [Clés d’authentification](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/authentication-keys).
* Connectez-vous à [&#128279;](https://account.magento.com/) (ou demandez au propriétaire de votre compte de le faire) et vérifiez que votre compte a accès à la base de code Commerce Enterprise.
* Vérifiez que les clés d’authentification publique et privée du compositeur de votre projet sont correctes. Voir [Clés d’authentification](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/authentication-keys).
* Vérifiez que le package nommé dans le message d’erreur est disponible pour votre version de Commerce. Voir [Packages &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-operations/release/packages/adobe-commerce).

**Si les détails mentionnent des emplacements ou des ressources d’environnement :**

* Dans la console cloud, ouvrez la présentation du projet et passez en revue les environnements et leurs statuts. Désactivez ou supprimez les environnements d’intégration inutilisés : sélectionnez l’environnement. Accédez à **[!UICONTROL Settings]>[!UICONTROL General]**. Définissez le statut de l’environnement sur inactif.

  Vous pouvez également utiliser l’interface en ligne de commande : `magento-cloud environment:list` / `magento-cloud environment:deactivate <environment-name>`
* Vérifiez que votre projet dispose de suffisamment de ressources, par exemple d’espace disque.
* Assurez-vous que l’environnement parent est stable (aucun déploiement actif) au moment de l’opération.
* Contactez l’assistance Adobe si vous devez augmenter la limite de votre environnement.

**Pour toute autre cause :** consultez les journaux d&#39;erreurs détaillés dans l&#39;interface utilisateur d&#39;automatisation des correctifs ou contactez l&#39;assistance avec le texte exact de l&#39;erreur.

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
* **Identifiant de l’opération** - Identifiant de l’opération [!DNL Patching Automation]
* **Détails de l’erreur** - Messages d’erreur complets et journaux
* **Procédure à suivre** - Que faisiez-vous lorsque l’erreur s’est produite ?
* **Tentatives précédentes** - Ce que vous avez déjà essayé de résoudre le problème

### Ressources supplémentaires

Pour obtenir des informations techniques plus détaillées :

* Consultez les journaux d’erreurs complets fournis avec les opérations ayant échoué
* Consultez la documentation Adobe Commerce pour obtenir des conseils spécifiques aux correctifs
* Contactez l’assistance Adobe Commerce Cloud pour les problèmes spécifiques à un environnement

### Rubriques connexes

* [Documentation Adobe Commerce Cloud](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/overview)
* [Guide d’installation d’Adobe Commerce](/help/installation/overview.md)
* [Présentation de l&#39;automatisation des correctifs](intro.md)
* [Accès](access.md)
* [Présentation des workflows](workflow.md)
* [Intégration de GitHub](github-integration.md)
* [Bonnes pratiques](best-practices.md)
