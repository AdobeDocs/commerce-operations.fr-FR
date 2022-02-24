---
title: '"[!DNL Upgrade Compatibility Tool] Prerequisites"'
description: 'Vérifiez que votre système respecte les exigences nécessaires à l’exécution de la variable [!DNL Upgrade Compatibility Tool] pour votre projet Adobe Commerce. '
source-git-commit: 97295df89fda393c8cf8675f8f4be92ac6f38a6a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] conditions préalables

Running the [!DNL Upgrade Compatibility Tool] helps you identify what you must do **before** upgrading your Adobe Commerce version.

Configuration minimale requise pour exécuter la variable [!DNL Upgrade Compatibility Tool] sont :

| **Conditions** | **Contraintes** |
|----------------|-----------------|
| version PHP | >= 7.3 |
| Compositeur | none |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`ou `>=16.0.0`) |
| Memory limitations | Au moins 2 Go de RAM |
| Clés d’accès Adobe Commerce | none |
| Adobe Commerce (Open Source ou Enterprise) | none |

Vous pouvez exécuter la variable [!DNL Upgrade Compatibility Tool] dans n’importe quel système d’exploitation. Il n’est pas nécessaire d’exécuter la variable [!DNL Upgrade Compatibility Tool] où se trouve votre instance Adobe Commerce.

Il est nécessaire que la fonction [!DNL Upgrade Compatibility Tool] pour accéder au code source de l’instance Adobe Commerce. For example, you can install it on one server and point it at your Adobe Commerce installation on another server. Reportez-vous à la section [install](../upgrade-compatibility-tool/install.md) pour plus d’informations.
