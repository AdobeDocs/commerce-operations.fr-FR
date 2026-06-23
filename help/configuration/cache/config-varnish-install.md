---
title: Installer le vernis
description: Découvrez les exigences d’installation de Varnish pour la mise en cache d’Adobe Commerce. Découvrez les ressources d’installation et les conseils de configuration.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
badgePaas: label="Sur Site" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets sur site Adobe Commerce."
autotag-review: '2026-06-22T21:26:58.525Z'
TQID: 'https://experienceleague.adobe.com/Cvy4Qsi-5Fom1t5wqNlq1SiSs4Bb8-DPsWrGfapWfSc'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 189
ht-degree: 0%

---

# Installer le vernis

{{varnish-config-cloud}}

L&#39;installation du vernis n&#39;entre pas dans le cadre de ce guide. Cette rubrique suppose qu’une version de vernis prise en charge et un serveur d’origine Adobe Commerce s’exécutant derrière Varnish. Les exemples de ce guide utilisent nginx comme serveur web d’origine.

- [guide d’installation](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Guides d&#39;installation de vernis](https://www.varnish-cache.org/docs)
- [Comment installer Varnish (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Si vous envisagez d’installer des modules Varnish (vmods), tels que le mode saint, vous devez installer Varnish en compilant le code, plutôt qu’en effectuant l’installation à partir d’un package. Voir [Mode Saint](config-varnish-advanced.md#saint-mode) pour plus d’informations.

## Confirmer votre version du vernis

Ouvrez un terminal et saisissez la commande suivante pour afficher la version de Vernis :

```shell
varnishd -V
```

Assurez-vous que [Adobe Commerce prend en charge](../../installation/system-requirements.md) la version installée de Varnish avant de continuer. Si vous exécutez une version non prise en charge, vous devez effectuer la mise à niveau vers une version prise en charge. Pour plus d&#39;informations, consultez la documentation relative à l&#39;installation de Varnish .
