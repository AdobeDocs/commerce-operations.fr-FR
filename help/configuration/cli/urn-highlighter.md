---
title: Surligneur URN
description: Découvrez comment configurer la mise en surbrillance des URL dans votre IDE.
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Surligneur URN - Aperçu

{{file-system-owner}}

Le code de commerce référence tous les schémas XSD [Uniform Resource Names (URL)](https://www.ietf.org/rfc/rfc2141.txt). Si vous développez du code et devez référencer des schémas XSD, cette commande configure votre environnement de développement intégré (IDE) pour reconnaître et mettre en évidence les URL. Cela facilite le développement.

Par défaut, un IDE tel que PhpStorm n’est pas configuré pour reconnaître les URL. Par conséquent, elles s’affichent en texte rouge comme suit :

![PhpStorm non configuré pour reconnaître l’URL](../../assets/configuration/urn-before.png)

La variable `bin/magento dev:urn-catalog:generate` La commande permet à votre IDE (actuellement, uniquement PhpStorm et Visual Studio Code) de reconnaître et de mettre en surbrillance les URL comme suit :

![Activer IDE pour reconnaître l’URL](../../assets/configuration/urn-after.png)

Plus précisément, cette commande crée la configuration PhpStorm suivante :

![Exemple de configuration PhpStorm](../../assets/configuration/urn-settings.png)

## Configuration de votre IDE

Actuellement, seuls PhpStorm et Visual Studio Code sont pris en charge.

Syntaxe de la commande :

```bash
bin/magento dev:urn-catalog:generate <path>
```

Où `<path>` est le chemin d’accès à PhpStorm. `misc.xml` qui se trouve par rapport à la racine de votre projet. En règle générale, `<path>` is `.idea/misc.xml`.

>[!INFO]
>
>Pour que vos &quot;schémas et DTD&quot; restent à jour, exécutez le `dev:urn-catalog:generate` chaque fois que vous ajoutez, modifiez ou supprimez des modules Commerce 2 contenant `*.xsd` fichiers .
