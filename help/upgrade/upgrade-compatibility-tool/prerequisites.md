---
title: Conditions préalables pour l’outil de compatibilité de mise à niveau
description: 'Vérifiez que votre système respecte la configuration requise pour exécuter l’outil de compatibilité de mise à niveau pour votre projet Adobe Commerce. '
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Conditions préalables de l’outil de compatibilité de mise à niveau

L’exécution de l’outil de compatibilité de mise à niveau vous permet d’identifier les actions à effectuer. **before** mise à niveau de votre version Adobe Commerce.

Les conditions minimales requises pour exécuter l’outil de compatibilité de mise à niveau sont les suivantes :

| **Conditions** | **Contraintes** |
|----------------|-----------------|
| version PHP | >= 7.3 |
| Compositeur | none |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`ou `>=16.0.0`) |
| Limites de mémoire | Au moins 2 Go de RAM |
| Clés d’accès Adobe Commerce | none |
| Adobe Commerce (Open Source ou Enterprise) | none |

Vous pouvez exécuter l’outil de compatibilité de mise à niveau dans n’importe quel système d’exploitation. Il n’est pas nécessaire d’exécuter l’outil de compatibilité de mise à niveau où se trouve votre instance Adobe Commerce.

Il est nécessaire que l’outil de compatibilité de mise à niveau ait accès au code source de l’instance Adobe Commerce. Par exemple, vous pouvez l’installer sur un serveur et le pointer vers votre installation Adobe Commerce sur un autre serveur. Reportez-vous à la section [install](../upgrade-compatibility-tool/install.md) pour plus d’informations.
