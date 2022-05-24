---
title: '"[!DNL Upgrade Compatibility Tool] Conditions préalables"'
description: 'Vérifiez que votre système respecte les exigences nécessaires à l’exécution de la variable [!DNL Upgrade Compatibility Tool] pour votre projet Adobe Commerce. '
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] conditions préalables

{{commerce-only}}

Configuration minimale requise pour exécuter la variable [!DNL Upgrade Compatibility Tool] sont :

| **Conditions** | **Contraintes** |
|----------------|-----------------|
| version PHP | >= 7.3 |
| Compositeur | none |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`ou `>=16.0.0`) |
| Limites de mémoire | Au moins 2 Go de RAM |
| Clés d’accès Adobe Commerce | none |
| Adobe Commerce | none |

Vous pouvez exécuter la variable [!DNL Upgrade Compatibility Tool] dans plusieurs systèmes d’exploitation (Windows n’est pas pris en charge). Vous n’avez pas à exécuter la variable [!DNL Upgrade Compatibility Tool] où se trouve votre instance Adobe Commerce.

Il est nécessaire que la fonction [!DNL Upgrade Compatibility Tool] pour accéder au code source de l’instance Adobe Commerce. Par exemple, vous pouvez l’installer sur un serveur et le pointer vers votre installation Adobe Commerce sur un autre serveur. Reportez-vous à la section [install](../upgrade-compatibility-tool/install.md) pour plus d’informations.

Si vous exécutez le [!DNL Upgrade Compatibility Tool] pour une instance Adobe Commerce avec des modules et des fichiers volumineux, l’outil peut nécessiter une quantité élevée de mémoire vive (au moins 2 Go). Vous pouvez utiliser la variable `[=MODULE-PATH]` dans votre commande pour spécifier le répertoire de chemin d’accès au module afin d’éviter des problèmes en raison d’une faible limitation de mémoire :

```bash
bin/uct upgrade:check <dir> -m[=MODULE-PATH]
```

Où les arguments sont les suivants :

- `<dir>`: Répertoire d’installation d’Adobe Commerce.
- `[=MODULE-PATH]`: Répertoire de chemin d’accès au module spécifique.
