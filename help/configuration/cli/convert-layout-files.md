---
title: Conversion de fichiers de mise en page
description: Convertir les fichiers de mise en page XML.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# Conversion de fichiers de disposition XML

{{file-system-owner}}

Utilisez cette commande pour mettre à jour vos fichiers XML de mise en page si vous mettez à jour la feuille de style XSLT (Extensible Stylesheet Language Transformations) correspondante.

- [Instructions de mise en page](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [Types de fichiers de mise en page](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

Options de commande :

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Où :

- `{xml file}` : chemin d’accès complet et nom de fichier d’un fichier XML de mise en page à convertir (obligatoire)
- `{xslt stylesheet}` : chemin d’accès complet et nom de fichier d’un fichier de feuille de style XSLT à utiliser pour la conversion (obligatoire).
- `-o|--overwrite` : incluez cette option pour remplacer le fichier XML existant.
