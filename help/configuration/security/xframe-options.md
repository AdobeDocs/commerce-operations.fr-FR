---
title: Empêcher les exploits de détournement de clic
description: Empêchez les exploits de détournement de clic en utilisant l’en-tête « X-Frame-Options » pour contrôler les rendus de page.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Empêcher les exploits de détournement de clic

Empêchez les exploits [détournement de clic](https://owasp.org/www-community/attacks/Clickjacking) en incluant l’en-tête de requête HTTP [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) dans les requêtes envoyées à votre storefront.

L’en-tête `X-Frame-Options` vous permet de spécifier si un navigateur est autorisé à effectuer le rendu d’une page dans une `<frame>`, un `<iframe>` ou un `<object>` comme suit :

- `DENY` : la page ne peut pas être affichée dans un cadre.
- `SAMEORIGIN` : (par défaut) la page ne peut être affichée que dans un cadre, sur la même origine que la page elle-même.

>[!WARNING]
>
>L’option `ALLOW-FROM <uri>` est obsolète, car les navigateurs pris en charge par Commerce ne la prennent plus en charge. Voir [Compatibilité navigateur](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Pour des raisons de sécurité, Adobe recommande vivement de ne pas exécuter le storefront Commerce dans un frame.

## Implémentation de `X-Frame-Options`

Définissez une valeur pour `X-Frame-Options` dans `<project-root>/app/etc/env.php`. La valeur par défaut est définie comme suit :

```php
'x-frame-options' => 'SAMEORIGIN',
```

Effectuez un redéploiement pour que les modifications apportées au fichier `env.php` soient prises en compte.

>[!TIP]
>
>La modification du fichier `env.php` est plus sûre que la définition d’une valeur dans l’Administration.

## Vérifier votre paramètre pour `X-Frame-Options`

Pour vérifier votre paramètre, affichez les en-têtes HTTP sur n’importe quelle page de storefront. Il existe plusieurs façons de le faire, notamment en utilisant un inspecteur de navigateur web.

L’exemple suivant utilise curl, que vous pouvez exécuter à partir de tout ordinateur pouvant se connecter à votre serveur Commerce via le protocole HTTP.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Recherchez la valeur `X-Frame-Options` dans les en-têtes.
