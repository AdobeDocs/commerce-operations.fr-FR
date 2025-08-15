---
title: Bibliothèque JavaScript de confidentialité
description: Découvrez comment utiliser des outils personnalisés pour accéder aux informations personnelles des clients collectées par Adobe Commerce et les supprimer.
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Bibliothèque JavaScript de confidentialité

La bibliothèque JavaScript d’Adobe Privacy est un ensemble d’outils permettant de créer un processus d’accès et de suppression des données privées collectées par Adobe Commerce.

Les services de suivi des données de Commerce peuvent stocker des informations privées applicables aux réglementations de confidentialité telles que le [ Règlement général sur la protection des données (RGPD)](gdpr.md) et le [California Consumer Privacy Act (CCPA)](ccpa.md).

Cette bibliothèque fournit un ensemble de fonctions pour créer des demandes de données de confidentialité et collecter leurs réponses. Utilisez cette bibliothèque pour récupérer et supprimer les données stockées dans le navigateur par les services de suivi de données Adobe Commerce.

>[!NOTE]
>
>Si le [Mode de restriction des cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html?lang=fr) est activé, Commerce ne collecte pas de données comportementales tant que l’acheteur n’a pas donné son consentement. Si le [!UICONTROL **Mode de restriction des cookies**] est désactivé, Commerce collecte des données comportementales par défaut.

## Installation

La bibliothèque JavaScript de confidentialité est disponible à l’emplacement du réseau CDN suivant : `commerce.adobe.net/magentoprivacy.js`

Une fois que vous disposez du fichier, vous devez l’ajouter à un module ou à un thème personnalisé installé dans votre instance Adobe Commerce. Suivez les instructions décrites dans la rubrique [ Utilisation de JavaScript personnalisés ](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) pour accomplir cette tâche.

### Initialisation

Importez et instanciez un nouvel objet `MagentoPrivacy` ou utilisez l’objet `window` pour accéder aux fonctions JavaScript de confidentialité.

Exemple d’utilisation de `import` :

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

Exemple d’utilisation de `window` :

```js
const magePriv = new window.MagentoPrivacy()
```

## Utilisation

La bibliothèque JS d’Adobe Privacy fournit diverses fonctions de gestion des données d’identité stockées dans le navigateur.

`retrieveIdentity()`
: renvoie une promesse JavaScript pour un objet d’identité d’un service dans le navigateur.

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
: supprime les données d’identité d’un service dans le navigateur.
Cette fonction renvoie une promesse JavaScript pour un objet d’identité avec une propriété booléenne `isDeleted` pour indiquer si les données ont été supprimées.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
