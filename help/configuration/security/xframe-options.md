---
title: Prévention des explosions de détournement de clic
description: Empêchez les exploits de détournement de clic à l’aide de l’en-tête "X-Frame-Options" pour contrôler les rendus de page.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Prévention des explosions de détournement de clic

Empêchez l’utilisation de [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) en incluant l’en-tête de requête HTTP [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) dans les requêtes envoyées à votre vitrine.

L’en-tête `X-Frame-Options` vous permet de spécifier si un navigateur est autorisé à effectuer le rendu d’une page dans un `<frame>`, `<iframe>` ou `<object>` comme suit :

- `DENY` : la page ne peut pas être affichée dans un cadre.
- `SAMEORIGIN` : (par défaut) la page ne peut être affichée que dans un cadre de la même origine que la page elle-même.

>[!WARNING]
>
>L’option `ALLOW-FROM <uri>` a été abandonnée car les navigateurs pris en charge par Commerce ne la prennent plus en charge. Voir [Compatibilité du navigateur](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Pour des raisons de sécurité, Adobe recommande vivement de ne pas exécuter le storefront Commerce dans un cadre.

## Mise en oeuvre de `X-Frame-Options`

Définissez une valeur pour `X-Frame-Options` dans `<project-root>/app/etc/env.php`. La valeur par défaut est définie comme suit :

```php
'x-frame-options' => 'SAMEORIGIN',
```

Redéployez pour que les modifications apportées au fichier `env.php` prennent effet.

>[!TIP]
>
>Il est plus sûr de modifier le fichier `env.php` que de définir une valeur dans l’administrateur.

## Vérifiez votre paramètre pour `X-Frame-Options`

Pour vérifier votre paramètre, affichez les en-têtes HTTP sur n’importe quelle page de storefront. Il existe plusieurs façons de procéder, notamment l’utilisation d’un inspecteur de navigateur Web.

L’exemple suivant utilise curl, que vous pouvez exécuter à partir de n’importe quel ordinateur pouvant se connecter à votre serveur Commerce via le protocole HTTP.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Recherchez la valeur `X-Frame-Options` dans les en-têtes.
