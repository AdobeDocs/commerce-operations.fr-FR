---
title: Surligneur URN
description: Découvrez comment configurer la mise en surbrillance des URL dans votre IDE pour le développement Adobe Commerce. Découvrez la configuration du schéma XSD et l’optimisation du développement.
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
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
source-wordcount: '191'
ht-degree: 0%
---
# Présentation du surligneur d’URL

{{file-system-owner}}

Le code Commerce fait référence à tous les schémas XSD [Uniform Resource Names [URN])](https://www.ietf.org/rfc/rfc2141.txt). Si vous développez du code et que vous devez référencer des fichiers XSD, cette commande configure votre environnement de développement intégré (IDE) pour reconnaître et mettre en évidence les URN. Cela facilite le développement.

Par défaut, un IDE tel que PhpStorm n’est pas configuré pour reconnaître les URN et, par conséquent, ils s’affichent en rouge comme suit :

![PhpStorm non configuré pour reconnaître URN](../../assets/configuration/urn-before.png)

La commande `bin/magento dev:urn-catalog:generate` permet à votre IDE (actuellement, uniquement PhpStorm et Visual Studio Code) de reconnaître et de mettre en évidence des URN comme ceux-ci :

![Activer l’IDE pour reconnaître l’URN](../../assets/configuration/urn-after.png)

Plus précisément, cette commande crée la configuration PhpStorm suivante :

![Exemple de configuration PhpStorm](../../assets/configuration/urn-settings.png)

## Configuration de votre IDE

Actuellement, seuls PhpStorm et Visual Studio Code sont pris en charge.

Syntaxe de la commande :

```shell
bin/magento dev:urn-catalog:generate <path>
```

Où `<path>` est le chemin d&#39;accès à votre fichier PhpStorm `misc.xml`, qui est situé par rapport à la racine de votre projet. En règle générale, `<path>` est `.idea/misc.xml`.

>[!INFO]
>
>Pour garder vos « schémas et DTD » à jour, exécutez la commande `dev:urn-catalog:generate` chaque fois que vous ajoutez, modifiez ou supprimez des modules Commerce 2 contenant des fichiers `*.xsd`.
