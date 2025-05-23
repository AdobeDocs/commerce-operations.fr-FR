---
title: Bibliothèque JavaScript Adobe Privacy
description: Découvrez comment utiliser des outils personnalisés pour accéder aux informations personnelles des clients et les supprimer collectées par Adobe Commerce.
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Bibliothèque JavaScript Adobe Privacy

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

La [bibliothèque JavaScript Adobe Privacy](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=fr) est un ensemble d’outils permettant de créer un processus d’accès et de suppression de données privées.

Les services de suivi de données Adobe Commerce peuvent stocker des informations privées applicables aux réglementations de confidentialité telles que le [Règlement général sur la protection des données (RGPD)](gdpr.md) et le [California Consumer Privacy Act (CCPA)](ccpa.md).

Cette bibliothèque fournit un ensemble unifié de fonctions permettant de créer des demandes de données d’accès à des informations personnelles, de les envoyer aux mises en oeuvre de chaque produit et de collecter les réponses. Utilisez cette bibliothèque pour récupérer et supprimer les données stockées dans le navigateur par ces services de suivi de données.

## Installation

Utilisez l’une des méthodes suivantes pour télécharger le fichier de bibliothèque :

- npm : `npm install @adobe/adobe-privacy`
- GitHub : [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

Une fois le fichier installé, vous devez l’ajouter à un module ou à un thème personnalisé installé dans votre instance Adobe Commerce. Suivez les instructions décrites dans la rubrique [Utilisation d’un JavaScript personnalisé](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) pour accomplir cette tâche.

## Utilisation

La bibliothèque JS d’AdobePrivacy fournit différentes fonctions pour gérer les données d’identité stockées dans le navigateur.

`retrieveIdentities()`
: renvoie un tableau d’identités d’un service avec un tableau d’identités introuvables dans le service.

`removeIdentities()`
: supprime les identités du navigateur et renvoie un tableau d’objets d’identité avec une propriété booléenne `isDeleteClientSide` pour indiquer si les données ont été supprimées.

`retrieveThenRemoveIdentities()`
: cette fonction est similaire à `removeIdentities()` en ce qu’elle récupère un tableau d’identités et les supprime du navigateur.

Pour plus d’informations et d’exemples d’utilisation de ces fonctions, consultez la [documentation officielle de la bibliothèque](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=fr).

### Initialisation

Instanciez un nouvel objet `AdobePrivacy` pour utiliser la bibliothèque JS AdobePrivacy dans votre code de mise en oeuvre.

```js
var adobePrivacy = new AdobePrivacy({});
```

Le constructeur accepte un objet de configuration avec des paramètres lors de l’instanciation.
Reportez-vous à la [documentation officielle de la bibliothèque](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=fr) pour obtenir la liste de ces paramètres de configuration.
