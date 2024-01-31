---
title: Modes d’application
description: L’application Commerce peut fonctionner dans différents modes selon vos besoins. Affichez la liste détaillée des modes d’application disponibles.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: 5003e8dcbb3736201ea19ebe30d5e56775096157
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 0%

---

# Modes d’application

Vous pouvez exécuter l’application Commerce dans l’une des méthodes suivantes : _modes_:

| Nom du mode | Description | Prise en charge du cloud |
| ------------------------ | ------------------- | ------------- |
| [default](#default-mode) | Déployez et exécutez l’application Commerce sur un seul serveur sans modifier les paramètres. _Not_ optimisé pour la production. | non |
| [développeur](#developer-mode) | Idéal pour le développement lors de l’extension ou de la personnalisation de l’application Commerce. | non |
| [production](#production-mode) | Déployez et exécutez l’application Commerce sur un système de production. | Oui |
| [maintenance](#maintenance-mode) | Empêcher l’accès à un site lors de l’exécution des mises à jour et des configurations. | Oui |

Voir [Définir le mode de fonctionnement](../cli/set-mode.md) pour savoir comment modifier manuellement les modes d’opération Adobe Commerce.

## Prise en charge du cloud

En raison du système de fichiers en lecture seule, vous ne pouvez pas modifier les modes dans les environnements cloud distants. Ne tentez pas de modifier les modes en modifiant les `app/etc/env.php` car la variable `ece-tools` Le package remplace le fichier en fonction de plusieurs sources de configuration.

Adobe Commerce sur l’infrastructure cloud exécute automatiquement l’application dans _maintenance_ pendant un déploiement, ce qui permet à votre site d’être déconnecté jusqu’à ce que le déploiement soit terminé. Sinon, l’application reste dans _production_ mode . Voir [Processus de déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) dans le _Guide de Commerce sur l’infrastructure cloud_.

Si vous utilisez Cloud Docker pour Commerce en tant qu’outil de développement, vous pouvez déployer votre projet d’infrastructure cloud dans un environnement Docker dans _développeur_ , mais les performances sont plus lentes en raison d’opérations de synchronisation de fichiers supplémentaires. Voir [Déploiement de l’environnement Docker](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) dans le _Guide de Cloud Docker pour Commerce_.

## Mode par défaut

La variable _default_ Le mode permet de déployer l’application Commerce sur un seul serveur sans modifier les paramètres. Cependant, le mode par défaut n’est pas optimisé pour la production en raison de l’impact négatif sur les performances des fichiers statiques. La création de fichiers statiques et leur mise en cache ont un impact sur les performances plus important que leur génération à l’aide de l’outil de création de fichiers statiques.

En mode par défaut :

- Les exceptions sont écrites dans des fichiers journaux au lieu d’être affichées.
- Les fichiers d’affichage statique sont mis en cache.
- Masque les `X-Magento-*` En-têtes de requête et de réponse HTTP

Commerce fonctionne en mode par défaut si aucun autre mode n’est spécifié.

## Mode Développeur

La variable _développeur_ est recommandé pour étendre et personnaliser l’application Commerce. Les fichiers d’affichage statiques ne sont pas mis en cache, mais écrits dans le `pub/static` répertoire à la demande.

En mode Développeur :

- Active [compilation automatique de code](../cli/code-compiler.md) et débogage amélioré
- Les exceptions non interceptées s’affichent dans le navigateur.
- Connexion système `var/report` is verbose
- Une exception est générée dans le gestionnaire d’erreurs, plutôt que d’être consignée.
- Une exception est générée lorsqu’un abonné à un événement ne peut pas être appelé.
- Affiche les `X-Magento-*` En-têtes de requête et de réponse HTTP

## Mode de production

La variable _production_ est idéal pour déployer l’application Commerce sur un système de production. Après avoir optimisé l’environnement du serveur, tel que la base de données et le serveur web, vous devez exécuter la variable [outil de déploiement des fichiers d’affichage statique](../cli/static-view-file-deployment.md) pour écrire des fichiers d’affichage statiques dans le `pub/static` répertoire . Cela améliore les performances en fournissant tous les fichiers statiques nécessaires au déploiement au lieu de forcer l’application Commerce à localiser et à copier dynamiquement (matérialiser) les fichiers statiques à la demande au cours de l’exécution.

Certains champs, tels que les sections Advanced et Developer system configuration dans Admin, ne sont pas disponibles en mode de production. Par exemple, vous _cannot_ activez ou désactivez les types de cache à l’aide de l’administrateur. Vous pouvez activer et désactiver les types de cache. _only_ en utilisant la variable [ligne de commande](../cli/manage-cache.md#config-cli-subcommands-cache-en).

En mode de production :

- Les fichiers d’affichage statique sont diffusés à partir du cache uniquement.
- Les erreurs et les exceptions sont consignées dans le système de fichiers et ne sont jamais affichées pour l’utilisateur.
- Certains champs de configuration de l’administrateur ne sont pas disponibles.

## Mode de maintenance

La variable _maintenance_ limite ou empêche l’accès à un site pendant les améliorations, les mises à jour et les tâches de configuration. Par défaut, le site redirige les visiteurs vers une `Service Temporarily Unavailable` page.

Vous pouvez créer un [page de maintenance personnalisée](../../upgrade/troubleshooting/maintenance-mode-options.md), activez et désactivez manuellement le mode de maintenance et configurez le mode de maintenance pour permettre aux visiteurs provenant d’adresses IP autorisées de visualiser normalement le magasin. Voir [activation et désactivation du mode de maintenance](../../installation/tutorials/maintenance-mode.md) dans le _Guide d’installation_.

Si vous utilisez Commerce sur l’infrastructure cloud, l’application Commerce s’exécute en mode de maintenance pendant la phase de déploiement. Une fois le déploiement terminé, l’application Commerce revient en mode de production. Voir [Hooks de déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) dans le _Guide de Commerce sur l’infrastructure cloud_.

En mode de maintenance :

- Les visiteurs du site sont redirigés vers une `Service Temporarily Unavailable` page
- La variable `var/` contient le répertoire `.maintenance.flag` fichier
- Vous pouvez limiter l’accès des visiteurs en fonction des adresses IP.
