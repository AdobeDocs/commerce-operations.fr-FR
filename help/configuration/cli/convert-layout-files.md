---
title: Convertir les fichiers de disposition
description: Découvrez comment convertir des fichiers de disposition XML à l’aide d’outils de ligne de commande Adobe Commerce. Découvrez les mises à jour des feuilles de style XSLT et les processus de conversion de fichiers.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Convertir des fichiers de disposition XML

{{file-system-owner}}

Utilisez cette commande pour mettre à jour vos fichiers XML de disposition si vous mettez à jour la feuille de style XSLT (Extensible Stylesheet Language Transformations) correspondante.

- [Instructions de disposition](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [Types de fichiers de disposition](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

Options de commande :

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Où :

- `{xml file}` : est le chemin d&#39;accès complet et le nom d&#39;un fichier XML de mise en page à convertir (obligatoire)
- `{xslt stylesheet}` : chemin d&#39;accès complet et nom d&#39;un fichier de feuille de style XSLT à utiliser pour la conversion (obligatoire)
- `-o|--overwrite` : incluez cette option pour remplacer le fichier XML existant
