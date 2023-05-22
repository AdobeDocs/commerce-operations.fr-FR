---
title: Installer le vernis
description: Consultez les conseils sur l’installation de vernis.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '165'
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

Voici un exemple :

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

Assurez-vous que la version est 6.x avant de continuer. Si vous exécutez une version antérieure à 6.x, vous devez effectuer une mise à niveau vers une version prise en charge. Pour plus d’informations, consultez la documentation sur l’installation du vernis .
