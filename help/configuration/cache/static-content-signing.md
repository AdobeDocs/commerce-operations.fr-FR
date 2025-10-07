---
title: Cache de contenu statique
description: Découvrez la signature du cache de contenu statique et l’optimisation des performances dans Adobe Commerce. Découvrez comment activer, désactiver et configurer les fonctionnalités de mise en cache.
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# Cache de contenu statique

Pour améliorer les performances, Commerce définit les en-têtes `Expires` pour les ressources statiques, telles que les images, les fichiers JavaScript et CSS.
La définition de l’en-tête `Expires` sur une ressource statique indique au navigateur de mettre la ressource en cache à cette URL et de diffuser la version mise en cache jusqu’à son expiration.
Il s’agit d’une [bonne pratique](https://developer.yahoo.com/performance/rules.html#expires=) courante pour mettre en cache des ressources statiques.

Lorsque le navigateur met en cache une ressource statique et que cette ressource change sur le serveur, vous devez vider la mémoire cache du navigateur afin qu’il puisse télécharger la nouvelle version.
L’effacement manuel du cache du navigateur fonctionne si vous êtes administrateur d’un site web, mais il ne s’agit pas d’une requête appropriée à effectuer sur vos utilisateurs lorsque vous souhaitez qu’ils téléchargent de nouvelles versions d’une ressource statique.

## Signature de contenu statique

La signature de contenu statique est une fonctionnalité de Commerce qui vous permet d’invalider le cache du navigateur pour les ressources statiques.
Pour ce faire, Commerce ajoute une version de déploiement à l’URL des fichiers statiques.

Voici un exemple d’URL signée avec une version :

```
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Lorsque vous exécutez la [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) de commande pour déployer du contenu statique, Commerce modifie automatiquement la version de déploiement.
Cela modifie l’URL des fichiers statiques et force le navigateur à charger la nouvelle version des fichiers.

Commerce active cette fonctionnalité par défaut et Adobe recommande de la conserver pour éviter les problèmes liés aux navigateurs qui diffusent d’anciennes ressources statiques.

La configuration de la signature de contenu statique se trouve dans [**[!UICONTROL Stores]**> Paramètres > Configuration >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#static-file-signatures).

- **On-Premise uniquement** : cette configuration est disponible si votre site n’est **pas** en [mode de production](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#production-mode).
- **Cloud** : cette configuration est masquée, car le mode de production est strictement appliqué. Vous devez donc utiliser la ligne de commande, comme illustré ci-dessous.

![Paramètres des fichiers statiques](../../assets/configuration/static-files-settings.png)

Déterminez le statut :

```bash
bin/magento config:show dev/static/sign
```

Activez ou désactivez la signature de contenu statique :

```bash
bin/magento config:set dev/static/sign <value>
```

Où `<value>` est 1 (activé) ou 0 (désactivé).

## Signatures de version

Commerce ajoute la signature de version en tant que composant de chemin d’accès directement après l’URL de base des fichiers de vue statiques afin de préserver l’intégrité des URL relatives dans les ressources statiques.
Cela force également le navigateur à résoudre une URL relative sur la source signée correcte tout en conservant son contenu indépendant de la présence/l’absence de la valeur de signature.

Lorsqu’un navigateur demande une source signée au serveur, le serveur utilise des réécritures d’URL pour supprimer le composant de signature de l’URL.

## Utilisation lors des déploiements

Après avoir mis à niveau ou modifié des ressources statiques, vous devez exécuter la commande `setup:static-content:deploy` pour déployer la version et mettre à jour le contenu statique, ce qui force le navigateur à charger les ressources mises à jour.

Si vous déployez du code sur un serveur distinct et le déplacez en production à l’aide d’un référentiel de code pour réduire les temps d’arrêt, vous devez également ajouter le fichier `pub/static/deployed_version.txt` au référentiel.
Ce fichier contient la nouvelle version du contenu statique déployé.
