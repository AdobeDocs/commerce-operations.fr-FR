---
title: Convertir les fichiers de disposition
description: Découvrez comment convertir des fichiers de disposition XML à l’aide d’outils de ligne de commande Adobe Commerce. Découvrez les mises à jour des feuilles de style XSLT et les processus de conversion de fichiers.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%
---
# Convertir des fichiers de disposition XML

{{file-system-owner}}

Utilisez cette commande pour mettre à jour vos fichiers XML de disposition si vous mettez à jour la feuille de style XSLT (Extensible Stylesheet Language Transformations) correspondante.

- [Instructions de mise en page](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions)
- [Types de fichiers de disposition](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-files-types-and-conventions)

Options de commande :

```shell
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Où :

- `{xml file}` : est le chemin d&#39;accès complet et le nom d&#39;un fichier XML de mise en page à convertir (obligatoire)
- `{xslt stylesheet}` : chemin d&#39;accès complet et nom d&#39;un fichier de feuille de style XSLT à utiliser pour la conversion (obligatoire)
- `-o|--overwrite` : incluez cette option pour remplacer le fichier XML existant
