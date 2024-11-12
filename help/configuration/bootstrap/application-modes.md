---
title: Modes d’application
description: L’application Commerce peut fonctionner dans différents modes selon vos besoins. Affichez la liste détaillée des modes d’application disponibles.
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
| [default](#default-mode) | Déployez et exécutez l’application Commerce sur un seul serveur sans modifier les paramètres. _Not_ optimisé pour la production. | non |
| [développeur](#developer-mode) | Idéal pour le développement lors de l’extension ou de la personnalisation de l’application Commerce. | non |
| [production](#production-mode) | Déployez et exécutez l’application Commerce sur un système de production. | Oui |
| [maintenance](#maintenance-mode) | Empêcher l’accès à un site lors de l’exécution des mises à jour et des configurations. | Oui |

Voir [Définition du mode d’opération](../cli/set-mode.md) pour savoir comment modifier manuellement les modes d’opération Adobe Commerce.

## Prise en charge du cloud

En raison du système de fichiers en lecture seule, il existe une restriction stricte contre la modification des modes dans les environnements cloud distants et il ne peut pas être remplacé par le support Adobe Commerce. Ne tentez pas de modifier les modes en modifiant le fichier `app/etc/env.php`, car le package `ece-tools` remplace le fichier en fonction de plusieurs sources de configuration.

Adobe Commerce sur l’infrastructure cloud exécute automatiquement l’application en mode _maintenance_ lors d’un déploiement, ce qui met votre site hors ligne jusqu’à la fin du déploiement. Sinon, l&#39;application reste en mode _production_. Voir [Processus de déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) dans le _guide Commerce on Cloud Infrastructure_.

Si vous utilisez Cloud Docker pour Commerce comme outil de développement, vous pouvez déployer votre projet d’infrastructure cloud dans un environnement Docker en mode _développeur_, mais les performances sont plus lentes en raison d’opérations de synchronisation de fichiers supplémentaires. Voir [Déploiement de l’environnement Docker](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) dans le _guide de Cloud Docker pour Commerce_.


## Mode par défaut

Le mode _default_ permet de déployer l’application Commerce sur un seul serveur sans modifier les paramètres. Cependant, le mode par défaut n’est pas optimisé pour la production en raison de l’impact négatif sur les performances des fichiers statiques. La création de fichiers statiques et leur mise en cache ont un impact sur les performances plus important que leur génération à l’aide de l’outil de création de fichiers statiques.

En mode par défaut :

- Les exceptions sont écrites dans des fichiers journaux au lieu d’être affichées.
- Les fichiers d’affichage statique sont mis en cache.
- Masque les en-têtes de requête et de réponse HTTP `X-Magento-*` personnalisés

Commerce fonctionne en mode par défaut si aucun autre mode n’est spécifié.

## Mode Développeur

Le mode _développeur_ est recommandé pour étendre et personnaliser l’application Commerce. Les fichiers d’affichage statique ne sont pas mis en cache, mais écrits dans le répertoire `pub/static` à la demande.

En mode Développeur :

- Active la [compilation automatique de code](../cli/code-compiler.md) et le débogage amélioré
- Les exceptions non interceptées s’affichent dans le navigateur.
- La connexion système à `var/report` est un verbose
- Une exception est générée dans le gestionnaire d’erreurs, plutôt que d’être consignée.
- Une exception est générée lorsqu’un abonné à un événement ne peut pas être appelé.
- Affiche les en-têtes de requête et de réponse HTTP `X-Magento-*` personnalisés

>[!NOTE]
>
>Ce mode n’est pas pris en charge dans l’environnement Adobe Commerce Cloud et la prise en charge d’Adobe Commerce ne peut pas faciliter le changement de mode d’application.

## Mode de production

Le mode _production_ est idéal pour déployer l’application Commerce sur un système de production. Après avoir optimisé l’environnement du serveur, tel que la base de données et le serveur web, vous devez exécuter l’ [ outil de déploiement de fichiers d’affichage statique](../cli/static-view-file-deployment.md) pour écrire des fichiers d’affichage statique dans le répertoire `pub/static`. Cela améliore les performances en fournissant tous les fichiers statiques nécessaires au déploiement au lieu de forcer l’application Commerce à localiser et à copier dynamiquement (matérialiser) les fichiers statiques à la demande pendant l’exécution.

Certains champs, tels que les sections Advanced et Developer system configuration dans Admin, ne sont pas disponibles en mode de production. Par exemple, vous _ne pouvez pas_ activer ou désactiver les types de cache à l’aide de l’administrateur. Vous pouvez activer et désactiver les types de cache _uniquement_ à l’aide de la [ligne de commande](../cli/manage-cache.md#config-cli-subcommands-cache-en).

En mode de production :

- Les fichiers d’affichage statique sont diffusés à partir du cache uniquement.
- Les erreurs et les exceptions sont consignées dans le système de fichiers et ne sont jamais affichées pour l’utilisateur.
- Certains champs de configuration de l’administrateur ne sont pas disponibles.

## Mode de maintenance

Le mode _maintenance_ limite ou empêche l’accès à un site pendant les améliorations, les mises à jour et les tâches de configuration. Par défaut, le site redirige les visiteurs vers une page `Service Temporarily Unavailable` par défaut.

Vous pouvez créer une [page de maintenance personnalisée](../../upgrade/troubleshooting/maintenance-mode-options.md), activer et désactiver manuellement le mode de maintenance et configurer le mode de maintenance pour permettre aux visiteurs d’adresses IP autorisées d’afficher normalement le magasin. Voir [Activation et désactivation du mode de maintenance](../../installation/tutorials/maintenance-mode.md) dans le _Guide d&#39;installation_.

Si vous utilisez Commerce sur l’infrastructure cloud, l’application Commerce s’exécute en mode de maintenance pendant la phase de déploiement. Une fois le déploiement terminé, l’application Commerce revient en mode de production. Voir [Hooks de déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) dans le _guide Commerce on Cloud Infrastructure_.

En mode de maintenance :

- Les visiteurs du site sont redirigés vers une page `Service Temporarily Unavailable` par défaut.
- Le répertoire `var/` contient le fichier `.maintenance.flag`
- Vous pouvez limiter l’accès des visiteurs en fonction des adresses IP.
