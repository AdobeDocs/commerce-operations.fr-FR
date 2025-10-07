---
title: Installer le vernis
description: Découvrez les exigences d’installation de Varnish pour la mise en cache d’Adobe Commerce. Découvrez les ressources d’installation et les conseils de configuration.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# Installer le vernis

L&#39;installation du logiciel Varnish n&#39;entre pas dans le cadre de ce guide. Pour plus d&#39;informations sur l&#39;installation de Varnish, voir :

- [guide d’installation](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Guides d&#39;installation de vernis](https://www.varnish-cache.org/docs)
- [Comment installer Varnish (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Cette rubrique a été écrite pour Varnish sur CentOS et Apache 2.4. Si vous configurez le vernis dans un environnement différent, certaines commandes sont probablement différentes. Pour plus d’informations, consultez la documentation précédente .
>
>Si vous envisagez d’installer des modules Varnish (vmods), tels que le mode saint, vous devez installer Varnish en compilant le code, plutôt qu’en effectuant l’installation à partir d’un package. Voir [Mode Saint](config-varnish-advanced.md#saint-mode) pour plus d’informations.

## Confirmer votre version du vernis

Ouvrez un terminal et saisissez la commande suivante pour afficher la version de Vernis :

```bash
varnishd -V
```

Assurez-vous que [Adobe Commerce prend en charge](../../installation/system-requirements.md) la version installée de Varnish avant de continuer. Si vous exécutez une version non prise en charge, vous devez effectuer la mise à niveau vers une version prise en charge. Pour plus d&#39;informations, consultez la documentation relative à l&#39;installation de Varnish .
