---
title: Conversion de fichiers de mise en page
description: Convertir les fichiers de mise en page XML.
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# Conversion de fichiers de disposition XML

{{file-system-owner}}

Utilisez cette commande pour mettre à jour vos fichiers XML de mise en page si vous mettez à jour la feuille de style XSLT (Extensible Stylesheet Language Transformations) correspondante.

- [Instructions de mise en page](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/xml-instructions.html)
- [Types de fichiers de mise en page](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/layout-types.html)

Options de commande :

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Où :

- `{xml file}`: chemin d’accès complet et nom de fichier d’un fichier XML de mise en page à convertir (obligatoire).
- `{xslt stylesheet}`: chemin d’accès complet et nom de fichier d’un fichier de feuille de style XSLT à utiliser pour la conversion (obligatoire).
- `-o|--overwrite`: incluez cette option pour remplacer le fichier XML existant.
