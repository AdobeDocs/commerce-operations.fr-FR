---
title: Cache de contenu statique
description: Apprenez à signer du contenu statique et à activer ou désactiver cette fonctionnalité.
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Cache de contenu statique

Pour améliorer les performances, Commerce définit la variable `Expires` en-têtes pour les ressources statiques, telles que les images, JavaScript et les fichiers CSS.
La définition de la variable `Expires` sur une ressource statique, l’en-tête indique au navigateur de mettre la ressource en cache à cette URL et de diffuser la version mise en cache jusqu’à son expiration.
Ceci est courant [bonne pratique](https://developer.yahoo.com/performance/rules.html#expires=) pour la mise en cache de ressources statiques.

Lorsque le navigateur met en cache une ressource statique et que cette ressource change sur le serveur, vous devez effacer le cache du navigateur afin qu’il puisse télécharger la nouvelle version.
L’effacement manuel du cache du navigateur fonctionne si vous êtes administrateur d’un site web, mais il ne s’agit pas d’une requête appropriée à l’attention de vos utilisateurs lorsque vous souhaitez qu’ils téléchargent de nouvelles versions d’une ressource statique.

## Signature de contenu statique

La signature de contenu statique est une fonction Commerce qui vous permet d’invalider le cache du navigateur pour les ressources statiques.
Pour ce faire, Commerce ajoute une version de déploiement à l’URL des fichiers statiques.

Voici un exemple d’URL signée avec une version :

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Lorsque vous exécutez la commande [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) pour déployer du contenu statique, Commerce modifie automatiquement la version de déploiement.
Cela modifie l’URL des fichiers statiques et force le navigateur à charger la nouvelle version des fichiers.

Commerce active cette fonctionnalité par défaut et Adobe recommande de la conserver afin d’éviter les problèmes liés aux navigateurs qui diffusent d’anciennes ressources statiques.

Vous trouverez la configuration de cette fonction dans [**[!UICONTROL Stores]**> Paramètres > Configuration >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

![Paramètres des fichiers statiques](../../assets/configuration/static-files-settings.png)

Déterminez l’état :

```bash
bin/magento config:show dev/static/sign
```

Activer ou désactiver la signature de contenu statique :

```bash
bin/magento config:set dev/static/sign <value>
```

Où `<value>` est 1 (activé) ou 0 (désactivé).

## Signatures de version

Commerce ajoute la signature de version en tant que composant de chemin juste après l’URL de base des fichiers d’affichage statique afin de préserver l’intégrité des URL relatives sur les ressources statiques.
Cela oblige également le navigateur à résoudre une URL relative à la source signée correcte, tout en conservant son contenu indépendamment de la présence/absence de la valeur de signature.

Lorsqu’un navigateur demande une source signée au serveur, le serveur utilise les réécritures d’URL pour supprimer le composant de signature de l’URL.

## Utilisation pendant les déploiements

Après la mise à niveau ou la modification de ressources statiques, vous devez exécuter la variable `setup:static-content:deploy` pour déployer la version et mettre à jour le contenu statique, ce qui force le navigateur à charger les ressources mises à jour.

Si vous déployez du code sur un serveur distinct et le déplacez en production à l’aide d’un référentiel de code afin de réduire les temps d’arrêt, vous devez également ajouter le fichier . `pub/static/deployed_version.txt` au référentiel.
Ce fichier contient la nouvelle version du contenu statique déployé.
