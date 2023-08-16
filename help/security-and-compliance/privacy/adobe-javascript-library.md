---
title: Bibliothèque JavaScript Adobe Privacy
description: Découvrez comment utiliser des outils personnalisés pour accéder aux informations personnelles des clients et les supprimer collectées par Adobe Commerce et Magento Open Source.
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Bibliothèque JavaScript Adobe Privacy

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

La variable [Bibliothèque JavaScript Adobe Privacy](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) est un ensemble d’outils permettant de créer un processus d’accès et de suppression de données privées.

Adobe Commerce et les services de suivi des données Magento Open Source peuvent stocker des informations privées applicables aux réglementations de confidentialité, telles que la variable [Règlement général sur la protection des données (RGPD)](gdpr.md) et [California Consumer Privacy Act (CCPA)](ccpa.md).

Cette bibliothèque fournit un ensemble unifié de fonctions permettant de créer des demandes de données d’accès à des informations personnelles, de les envoyer aux mises en oeuvre de chaque produit et de collecter les réponses. Utilisez cette bibliothèque pour récupérer et supprimer les données stockées dans le navigateur par ces services de suivi de données.

## Installation

Utilisez l’une des méthodes suivantes pour télécharger le fichier de bibliothèque :

- npm : `npm install @adobe/adobe-privacy`
- GitHub : [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

Une fois que vous disposez du fichier, vous devez l’ajouter à un module ou à un thème personnalisé installé dans votre instance Adobe Commerce et Magento Open Source. Suivez les instructions décrites dans la section [Utilisation de JavaScript personnalisé](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) pour accomplir cette tâche.

## Utilisation

La bibliothèque JS d’AdobePrivacy fournit différentes fonctions pour gérer les données d’identité stockées dans le navigateur.

`retrieveIdentities()`
: renvoie un tableau d’identités d’un service avec un tableau d’identités introuvables dans le service.

`removeIdentities()`
: supprime les identités du navigateur et renvoie un tableau d’objets d’identité avec une `isDeleteClientSide` propriété boolean pour indiquer si les données ont été supprimées.

`retrieveThenRemoveIdentities()`
: cette fonction est similaire à la fonction `removeIdentities()` en ce sens qu’il récupère un tableau d’identités et les supprime du navigateur.

Pour plus d’informations et d’exemples sur l’utilisation de ces fonctions, voir la section [documentation officielle de la bibliothèque](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html).

### Initialisation

Instanciation d’une nouvelle `AdobePrivacy` pour utiliser la bibliothèque JS d’AdobePrivacy dans votre code de mise en oeuvre.

```js
var adobePrivacy = new AdobePrivacy({});
```

Le constructeur accepte un objet de configuration avec des paramètres lors de l’instanciation.
Voir [documentation officielle de la bibliothèque](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) pour une liste de ces paramètres de configuration.
