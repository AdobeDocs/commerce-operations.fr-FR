---
title: '"[!DNL Upgrade Compatibility Tool] Conditions préalables"'
description: 'Vérifiez que votre système respecte les exigences nécessaires à l’exécution de la variable [!DNL Upgrade Compatibility Tool] pour votre projet Adobe Commerce. '
source-git-commit: c4769b555df49ed2f0b2fffbeaf458c5a64816ba
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] conditions préalables

{{commerce-only}}

L’exécution de la variable [!DNL Upgrade Compatibility Tool] vous aide à identifier ce que vous devez faire **before** mise à niveau de votre version Adobe Commerce.

Configuration minimale requise pour exécuter la variable [!DNL Upgrade Compatibility Tool] sont :

| **Conditions** | **Contraintes** |
|----------------|-----------------|
| version PHP | >= 7.3 |
| Compositeur | none |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`ou `>=16.0.0`) |
| Limites de mémoire | Au moins 2 Go de RAM |
| Clés d’accès Adobe Commerce | none |
| Adobe Commerce | none |

Vous pouvez exécuter la variable [!DNL Upgrade Compatibility Tool] dans n’importe quel système d’exploitation. Il n’est pas nécessaire d’exécuter la variable [!DNL Upgrade Compatibility Tool] où se trouve votre instance Adobe Commerce.

Il est nécessaire que la fonction [!DNL Upgrade Compatibility Tool] pour accéder au code source de l’instance Adobe Commerce. Par exemple, vous pouvez l’installer sur un serveur et le pointer vers votre installation Adobe Commerce sur un autre serveur. Reportez-vous à la section [install](../upgrade-compatibility-tool/install.md) pour plus d’informations.

Si vous exécutez le [!DNL Upgrade Compatibility Tool] pour une instance Adobe Commerce avec des modules et des fichiers volumineux, l’outil peut nécessiter une grande quantité de RAM, au moins 2 Go de mémoire vive.
