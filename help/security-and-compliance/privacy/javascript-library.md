---
title: Bibliothèque JavaScript Privacy
description: Découvrez comment utiliser des outils personnalisés pour accéder aux informations personnelles des clients et les supprimer collectées par Adobe Commerce et Magento Open Source.
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Bibliothèque JavaScript Privacy

La bibliothèque JavaScript de confidentialité est un ensemble d’outils permettant de créer un processus d’accès et de suppression des données privées collectées par Adobe Commerce et Magento Open Source.

Les services de suivi des données de commerce peuvent stocker des informations privées applicables aux réglementations de confidentialité, telles que [Règlement général sur la protection des données (RGPD)](gdpr.md) et [California Consumer Privacy Act (CCPA)](ccpa.md).

Cette bibliothèque fournit un ensemble de fonctions permettant de créer des demandes de données d’accès à des informations personnelles et de collecter leurs réponses. Utilisez cette bibliothèque pour récupérer et supprimer les données stockées dans le navigateur par Adobe Commerce et les services de suivi des données du Magento Open Source.

>[!NOTE]
>
>If [Mode de restriction des cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) est activée, Commerce ne collecte les données comportementales que si l’acheteur a donné son consentement. If [!UICONTROL **Mode de restriction des cookies**] est désactivée, Commerce collecte les données comportementales par défaut.

## Installation

La bibliothèque JavaScript Privacy est disponible à l’emplacement suivant du réseau CDN : `commerce.adobe.net/magentoprivacy.js`

Une fois que vous disposez du fichier, vous devez l’ajouter à un module ou à un thème personnalisé installé dans votre instance Adobe Commerce ou Magento Open Source. Suivez les instructions décrites dans la section [Utilisation de JavaScript personnalisé](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) pour accomplir cette tâche.

### Initialisation

Importer et instancier une nouvelle `MagentoPrivacy` ou utilisez l’objet `window` pour accéder aux fonctions JavaScript Privacy.

Exemple d’utilisation `import`:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

Exemple d’utilisation `window`:

```js
const magePriv = new window.MagentoPrivacy()
```

## Utilisation

La bibliothèque JS d’Adobe Privacy fournit diverses fonctions pour gérer les données d’identité stockées dans le navigateur.

`retrieveIdentity()`
: renvoie une promesse JavaScript pour un objet d’identité à partir d’un service dans le navigateur.

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
: supprime les données d’identité d’un service dans le navigateur.
Cette fonction renvoie une promesse JavaScript pour un objet d’identité avec une `isDeleted` propriété boolean pour indiquer si les données ont été supprimées.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
