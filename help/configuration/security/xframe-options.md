---
title: En-tête X-Frame-Options
description: Utilisez X-Frame-Options pour contrôler les rendus de page.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# En-tête X-Frame-Options

Pour éviter [détournement de clic](https://owasp.org/www-community/attacks/Clickjacking) exploits, nous avons ajouté une option pour utiliser la variable [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) En-tête de requête HTTP dans les requêtes à votre storefront.

La variable `X-Frame-Options` L’en-tête vous permet de spécifier si un navigateur doit être autorisé à effectuer le rendu d’une page dans une `<frame>`, `<iframe>`, ou `<object>` comme suit :

- `DENY`: la page ne peut pas être affichée dans un cadre.
- `SAMEORIGIN`: (par défaut) la page ne peut être affichée que dans un cadre de la même origine que la page elle-même.

>[!WARNING]
>
>La variable `ALLOW-FROM <uri>` Cette option a été abandonnée, car les navigateurs pris en charge par Commerce ne la prennent plus en charge. Voir [Compatibilité du navigateur](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Pour des raisons de sécurité, Adobe recommande vivement de ne pas exécuter le storefront Commerce dans un cadre.

## Mise en oeuvre `X-Frame-Options`

Définir une valeur pour `X-Frame-Options` in `<project-root>/app/etc/env.php`. La valeur par défaut est définie comme suit :

```php
'x-frame-options' => 'SAMEORIGIN',
```

Redéployez pour toute modification apportée à la fonction `env.php` pour qu’il prenne effet.

>[!TIP]
>
>La modification de la variable `env.php` plutôt que de définir une valeur dans Admin.

## Vérifiez votre paramètre pour `X-Frame-Options`

Pour vérifier votre paramètre, affichez les en-têtes HTTP sur n’importe quelle page de storefront. Il existe plusieurs façons de procéder, notamment l’utilisation d’un inspecteur de navigateur Web.

L’exemple suivant utilise curl, que vous pouvez exécuter à partir de n’importe quel ordinateur pouvant se connecter à votre serveur Commerce via le protocole HTTP.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Recherchez le `X-Frame-Options` dans les en-têtes.
