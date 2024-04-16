---
title: Installer le vernis
description: Consultez les conseils sur l’installation de vernis.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Installer le vernis

L&#39;installation du logiciel Varnish ne relève pas du présent guide. Pour plus d’informations sur l’installation de vernis, voir :

- [guide d’installation](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Guides d’installation en pointillés](https://www.varnish-cache.org/docs)
- [Comment installer Varnish (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Cette rubrique est écrite pour le vernis sur CentOS et Apache 2.4. Si vous configurez le vernis dans un autre environnement, certaines commandes sont probablement différentes. Pour plus d’informations, consultez la documentation précédente .
>
>Si vous avez l’intention d’installer des modules Varnish (vmods), par exemple le mode saint, vous devez installer le vernis en compilant le code, plutôt qu’en l’installant à partir d’un package. Voir [Mode Saint](config-varnish-advanced.md#saint-mode) pour plus d’informations.

## Confirmez votre version de vernis.

Ouvrez un terminal et saisissez la commande suivante pour afficher la version de vernis :

```bash
varnishd -V
```

Assurez-vous que [Adobe Commerce prend en charge](../../installation/system-requirements.md) la version installée de Varnish avant de continuer. Si vous exécutez une version non prise en charge, vous devez effectuer une mise à niveau vers une version prise en charge. Pour plus d’informations, consultez la documentation sur l’installation du vernis .
