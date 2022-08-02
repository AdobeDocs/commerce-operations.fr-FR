---
title: Modes d’application
description: L’application Commerce peut fonctionner dans différents modes selon vos besoins. Affichez la liste détaillée des modes d’application disponibles.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# Modes d’application

Vous pouvez exécuter l’application Commerce dans l’une des méthodes suivantes : _modes_:

| Nom du module | Description |
| ----------- | ----------- |
| default | Permet de déployer l’application Commerce sur un seul serveur sans modifier les paramètres. Cependant, le mode par défaut n’est pas optimisé pour la production.<br>Pour déployer l’application Commerce sur plusieurs serveurs ou l’optimiser pour la production, définissez l’un des autres modes.<ul><li>La mise en cache des fichiers d’affichage statique est activée.</li><li>Les exceptions ne s’affichent pas pour l’utilisateur. à la place, les exceptions sont écrites dans des fichiers journaux.</li><li>Masque les `X-Magento-*` En-têtes de requête et de réponse HTTP</li></ul> |
| développeur | Destiné uniquement au développement, ce mode :<ul><li>Désactive la mise en cache des fichiers de vue statique</li><li>Permet la journalisation en mode verbeux</li><li>Active [compilation automatique de code](../cli/code-compiler.md)</li><li>Active le débogage amélioré</li><li>Affiche les `X-Magento-*` En-têtes de requête et de réponse HTTP</li><li>Les performances sont alors les plus lentes.</li><li>Affiche les erreurs sur le front-end</li></ul> |
| production | Destiné au déploiement sur un système de production, ce mode est le suivant :<ul><li>N’affiche pas d’exceptions pour l’utilisateur (les exceptions sont écrites dans les journaux uniquement).</li><li>Sert les fichiers d’affichage statique à partir du cache uniquement.</li><li>Empêche la compilation automatique des fichiers de code. Les fichiers nouveaux ou mis à jour ne sont pas écrits dans le système de fichiers.</li><li>**Ne vous permet pas d’activer ou de désactiver les types de cache dans l’administrateur.** Voir [activation et désactivation du cache](../cli/manage-cache.md#enable-or-disable-cache-types).</li><li>Certains champs, tels que les sections Advanced et Developer system configuration dans Admin, ne sont pas disponibles en mode de production.</li></ul> |
| maintenance | Ce mode est destiné à empêcher l&#39;accès à un site lorsqu&#39;il est mis à jour ou reconfiguré :<ul><li>Redirige les visiteurs du site vers une valeur par défaut `Service Temporarily Unavailable` page.</li><li>Lorsque le site est en mode de maintenance, la variable `var/` contient le répertoire `.maintenance.flag` fichier .</li><li>Vous pouvez configurer le mode de maintenance pour autoriser l’accès des visiteurs à partir d’une liste d’adresses IP spécifiée.</li></ul> |

>[!INFO]
>
>[Adobe Commerce sur l’infrastructure cloud](https://devdocs.magento.com/cloud/bk-cloud.html) ne prend en charge que les modes de production et de maintenance.

## Mode par défaut

Comme son nom l’indique, le mode par défaut est le mode de fonctionnement de Commerce si aucun autre mode n’est spécifié. Le mode par défaut permet de déployer l’application Commerce sur un seul serveur sans modifier les paramètres. Cependant, le mode par défaut n’est pas aussi optimisé pour la production que le mode de production.

Pour déployer l’application Commerce sur plusieurs serveurs ou l’optimiser pour la production, définissez l’un des autres modes.

En mode par défaut :

- Les erreurs sont consignées dans les rapports de fichiers sur le serveur et ne sont jamais affichées pour un utilisateur.
- Les fichiers d’affichage statique sont mis en cache.
- Le mode par défaut n’est pas optimisé pour un environnement de production, principalement en raison de l’impact négatif sur les performances de [fichiers statiques](https://glossary.magento.com/static-files) générés dynamiquement plutôt que matérialisés. En d’autres termes, la création de fichiers statiques et leur mise en cache ont un impact sur les performances plus important que leur génération à l’aide de l’outil de création de fichiers statiques.

Voir [Définir le mode de fonctionnement](../cli/set-mode.md).

## Mode Développeur

Exécutez l’application Commerce en mode Développeur lorsque vous l’étendez ou la personnalisez.

En mode Développeur :

- Les fichiers d’affichage statique ne sont pas mis en cache ; ils sont écrits dans la variable `pub/static` à chaque appel
- Les exceptions non interceptées s’affichent dans le navigateur.
- Connexion système `var/report` is verbose
- Un [exception](https://glossary.magento.com/exception) est généré dans le gestionnaire d’erreurs, plutôt que d’être consigné.
- Une exception est générée lorsqu’une [event](https://glossary.magento.com/event) abonné ne peut pas être appelé

Voir [Définir le mode de fonctionnement](../cli/set-mode.md).

## Mode de production

Exécutez Commerce en mode de production lorsqu’il est déployé sur un serveur de production. Après avoir optimisé l’environnement du serveur, tel que la base de données et le serveur web, vous devez exécuter la variable [outil de déploiement des fichiers d’affichage statique](../cli/static-view-file-deployment.md) pour écrire des fichiers d’affichage statiques dans le `pub/static` répertoire .

Cela améliore les performances en fournissant tous les fichiers statiques nécessaires au déploiement au lieu de forcer Commerce à localiser et à copier dynamiquement (matérialiser) les fichiers statiques à la demande au moment de l’exécution.

En mode de production :

- Les fichiers d’affichage statique ne sont pas matérialisés et les URL pour eux sont composées à la volée. Les fichiers d’affichage statique sont diffusés à partir de la fonction [cache](https://glossary.magento.com/cache) uniquement.
- Les erreurs sont consignées dans le système de fichiers et ne s’affichent jamais pour l’utilisateur.
- Vous pouvez activer et désactiver les types de cache. _only_ en utilisant la variable [ligne de commande](../cli/manage-cache.md#config-cli-subcommands-cache-en).
- You _cannot_ activez ou désactivez les types de cache à l’aide de l’administrateur.

## Mode de maintenance

Exécutez l’application Commerce en mode de maintenance pour mettre votre site hors ligne pendant que vous effectuez des tâches de maintenance, de mise à niveau ou de configuration. En mode de maintenance, le site redirige les visiteurs vers un `Service Temporarily Unavailable` page.

Vous pouvez créer un [page de maintenance personnalisée](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html), activez et désactivez manuellement le mode de maintenance et configurez le mode de maintenance pour permettre aux visiteurs provenant d’adresses IP autorisées de visualiser normalement le magasin. Voir [activation et désactivation du mode de maintenance](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

Si vous utilisez Commerce sur l’infrastructure cloud, l’application Commerce s’exécute en mode de maintenance pendant la phase de déploiement. Une fois le déploiement terminé, l’application Commerce revient en mode de production. Voir [Hooks de déploiement](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-hook) dans le _Guide Commerce Cloud_.
