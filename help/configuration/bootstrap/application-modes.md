---
title: Modes d’application
description: L’application Commerce peut fonctionner dans différents modes en fonction de vos besoins. Consultez une liste détaillée des modes d’application disponibles.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: c415c3427f513255b9d4ebe1d24ba4024df21928
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Modes d’application

Vous pouvez exécuter l’application Commerce dans l’un des _modes_ suivants :

| Nom du mode | Description | Prise en charge du cloud |
| ------------------------ | ------------------- | ------------- |
| [par défaut](#default-mode) | Déployez et exécutez l’application Commerce sur un seul serveur sans modifier les paramètres. _non_ optimisé pour la production. | non |
| [développeur](#developer-mode) | Idéal pour le développement lors de l’extension ou de la personnalisation de l’application Commerce. | non |
| [production](#production-mode) | Déployez et exécutez l’application Commerce sur un système d’exploitation. | Oui |
| [maintenance](#maintenance-mode) | Empêcher l’accès à un site lors des mises à jour et des configurations. | Oui |

Voir [ Définir le mode de fonctionnement ](../cli/set-mode.md) pour savoir comment modifier manuellement les modes de fonctionnement d’Adobe Commerce.

## Prise en charge du cloud

En raison du système de fichiers en lecture seule, il existe une restriction stricte empêchant de modifier les modes dans les environnements cloud distants et elle ne peut pas être remplacée par l’assistance Adobe Commerce. N’essayez pas de changer de mode en modifiant le fichier `app/etc/env.php`, car le package `ece-tools` remplace le fichier basé sur plusieurs sources de configuration.

Adobe Commerce sur l’infrastructure cloud exécute automatiquement l’application en mode _maintenance_ au cours d’un déploiement, ce qui met votre site hors ligne jusqu’à ce que le déploiement soit terminé. Dans le cas contraire, l’application reste en mode _production_. Voir [ Processus de déploiement ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=fr#deploy-phase) dans le guide _Commerce sur les infrastructures cloud_.

Si vous utilisez Cloud Docker pour Commerce en tant qu’outil de développement, vous pouvez déployer votre projet d’infrastructure cloud dans un environnement Docker en mode _développeur_, mais les performances sont plus lentes en raison d’opérations de synchronisation de fichiers supplémentaires. Voir [Déploiement de l’environnement Docker](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) dans le guide _Cloud Docker pour Commerce_.


## Mode par défaut

Le mode _par défaut_ permet de déployer l’application Commerce sur un seul serveur sans modifier les paramètres. Cependant, le mode par défaut n’est pas optimisé pour la production en raison de l’impact négatif des fichiers statiques sur les performances. La création et la mise en cache de fichiers statiques ont un impact plus important sur les performances que leur génération à l’aide de l’outil de création de fichiers statiques.

En mode par défaut :

- Les exceptions sont écrites dans des fichiers journaux au lieu d’être affichées
- Les fichiers de vue statiques sont mis en cache
- Masque les en-têtes de requête et de réponse HTTP `X-Magento-*` personnalisés

Commerce fonctionne en mode par défaut si aucun autre mode n’est spécifié.

## Mode Développeur

Le mode _développeur_ est recommandé pour étendre et personnaliser l’application Commerce. Les fichiers de vue statiques ne sont pas mis en cache, mais écrits dans le répertoire `pub/static` à la demande.

En mode Développeur :

- Active la [compilation de code automatique](../cli/code-compiler.md) et le débogage amélioré
- Les exceptions non interceptées s’affichent dans le navigateur
- La connexion système `var/report` est détaillée
- Une exception est générée dans le gestionnaire d’erreurs plutôt que consignée
- Une exception est générée lorsqu’un abonné à un événement ne peut pas être appelé
- Affiche les en-têtes de requête et de réponse HTTP `X-Magento-*` personnalisés

>[!NOTE]
>
>Ce mode n’est pas pris en charge dans l’environnement Adobe Commerce Cloud et la prise en charge d’Adobe Commerce ne peut pas faciliter le changement de mode d’application.

## Mode de production

Le mode _production_ est idéal pour déployer l’application Commerce sur un système d’exploitation. Après avoir optimisé l’environnement du serveur, tel que la base de données et le serveur web, vous devez exécuter l’outil [déploiement de fichiers d’affichage statique](../cli/static-view-file-deployment.md) pour écrire des fichiers d’affichage statique dans le répertoire `pub/static`. Cela améliore les performances en fournissant tous les fichiers statiques nécessaires au déploiement au lieu de forcer l’application Commerce à localiser et copier (matérialiser) dynamiquement les fichiers statiques à la demande pendant l’exécution.

Certains champs, tels que les sections Configuration du système avancé et Développeur dans l’Administration, ne sont pas disponibles en mode production. Par exemple, vous _ne pouvez pas_ activer ou désactiver les types de cache à l’aide de l’Administration. Vous pouvez activer et désactiver les types de cache _uniquement_ à l’aide de la [ligne de commande](../cli/manage-cache.md#config-cli-subcommands-cache-en).

En mode production :

- Les fichiers de vue statiques sont diffusés à partir du cache uniquement
- Les erreurs et exceptions sont consignées dans le système de fichiers et ne sont jamais affichées pour l’utilisateur
- Certains champs de configuration de l’administration ne sont pas disponibles

## Mode de maintenance

Le mode _maintenance_ limite ou empêche l’accès à un site lors des tâches d’amélioration, de mise à jour et de configuration. Par défaut, le site redirige les visiteurs vers une page de `Service Temporarily Unavailable` par défaut.

Vous pouvez créer une [page de maintenance personnalisée](../../upgrade/troubleshooting/maintenance-mode-options.md), activer et désactiver manuellement le mode de maintenance et configurer le mode de maintenance pour permettre aux visiteurs utilisant des adresses IP autorisées de consulter normalement le magasin. Voir [activation et désactivation du mode de maintenance](../../installation/tutorials/maintenance-mode.md) dans le _Guide d’installation_.

Si vous utilisez Commerce sur une infrastructure cloud, l’application Commerce s’exécute en mode de maintenance pendant la phase de déploiement. Une fois le déploiement terminé, l’application Commerce revient en mode d’exécution. Voir [Hooks de déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html?lang=fr#phase-5%3A-deployment-hooks) dans le guide _Commerce sur les infrastructures cloud_.

En mode de maintenance :

- Les visiteurs du site sont redirigés vers une page de `Service Temporarily Unavailable` par défaut
- Le répertoire `var/` contient le fichier `.maintenance.flag`
- Vous pouvez limiter l’accès des visiteurs et visiteuses en fonction des adresses IP
