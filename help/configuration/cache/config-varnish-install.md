---
title: Installer le vernis
description: Consultez les conseils sur l’installation de vernis.
source-git-commit: 688db9fcc9cd196d1560e49719b03ef32d13870d
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Installer le vernis

L&#39;installation du logiciel Varnish ne relève pas du présent guide. Pour plus d’informations sur l’installation de vernis, voir :

- [wiki d&#39;installation](http://wiki.mikejung.biz/Varnish)
- [Guides d’installation en pointillés](https://www.varnish-cache.org/docs)
- [Comment installer Varnish (Tecmint)](http://www.tecmint.com/install-varnish-cache-web-accelerator)

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
