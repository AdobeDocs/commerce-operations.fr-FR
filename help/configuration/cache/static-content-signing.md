---
title: Cache de contenu statique
description: Apprenez à signer du contenu statique et à activer ou désactiver cette fonctionnalité.
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Cache de contenu statique

Pour améliorer les performances, Commerce définit les en-têtes `Expires` pour les ressources statiques, telles que les images, JavaScript et les fichiers CSS.
La définition de l’en-tête `Expires` sur une ressource statique indique au navigateur de mettre en cache la ressource à cette URL et de diffuser la version mise en cache jusqu’à son expiration.
Il s’agit d’une [bonne pratique](https://developer.yahoo.com/performance/rules.html#expires=) courante pour la mise en cache de ressources statiques.

Lorsque le navigateur met en cache une ressource statique et que cette ressource change sur le serveur, vous devez effacer le cache du navigateur afin qu’il puisse télécharger la nouvelle version.
L’effacement manuel du cache du navigateur fonctionne si vous êtes administrateur d’un site web, mais il ne s’agit pas d’une requête appropriée à l’attention de vos utilisateurs lorsque vous souhaitez qu’ils téléchargent de nouvelles versions d’une ressource statique.

## Signature de contenu statique

La signature de contenu statique est une fonction de Commerce qui vous permet d’invalider le cache du navigateur pour les ressources statiques.
Pour ce faire, Commerce ajoute une version de déploiement à l’URL des fichiers statiques.

Voici un exemple d’URL signée avec une version :

```
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Lorsque vous exécutez la commande [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) pour déployer du contenu statique, Commerce modifie automatiquement la version de déploiement.
Cela modifie l’URL des fichiers statiques et force le navigateur à charger la nouvelle version des fichiers.

Commerce active cette fonctionnalité par défaut et Adobe recommande de l’activer afin d’éviter les problèmes liés aux navigateurs qui diffusent d’anciennes ressources statiques.

La configuration pour la signature de contenu statique est dans [**[!UICONTROL Stores]**> Paramètres > Configuration >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/tools/developer-tools#static-file-signatures).

- **On-Premise uniquement** : cette configuration est disponible si votre site est **et non** en [mode de production](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html?lang=fr#production-mode).
- **Cloud** : cette configuration est masquée car le mode de production est strictement appliqué. Par conséquent, vous devez utiliser la ligne de commande comme illustré ci-dessous.

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

Après la mise à niveau ou la modification de ressources statiques, vous devez exécuter la commande `setup:static-content:deploy` pour déployer la version et mettre à jour le contenu statique, ce qui force le navigateur à charger les ressources mises à jour.

Si vous déployez du code sur un serveur distinct et le déplacez en production à l’aide d’un référentiel de code afin de réduire le temps d’arrêt, vous devez également ajouter le fichier `pub/static/deployed_version.txt` au référentiel.
Ce fichier contient la nouvelle version du contenu statique déployé.
