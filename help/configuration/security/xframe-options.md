---
title: En-tête X-Frame-Options
description: Utilisez X-Frame-Options pour contrôler les rendus de page.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# En-tête X-Frame-Options

Pour éviter [détournement de clic](https://owasp.org/www-community/attacks/Clickjacking) exploits, nous avons ajouté une option pour utiliser la variable [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) En-tête de requête HTTP dans les requêtes à votre storefront.

Le `X-Frame-Options` L’en-tête vous permet de spécifier si un navigateur doit être autorisé à effectuer le rendu d’une page dans une `<frame>`, `<iframe>`ou `<object>` comme suit :

- `DENY`: La page ne peut pas être affichée dans un cadre.
- `SAMEORIGIN`: (par défaut) La page ne peut être affichée que dans un cadre de la même origine que la page elle-même.

>[!WARNING]
>
>Le `ALLOW-FROM <uri>` Cette option a été abandonnée, car les navigateurs pris en charge par Commerce ne la prennent plus en charge. Voir [Compatibilité du navigateur](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Pour des raisons de sécurité, Adobe recommande vivement de ne pas exécuter le storefront Commerce dans un cadre.

## Mise en oeuvre `X-Frame-Options`

Définir une valeur pour `X-Frame-Options` in `<magento_root>/app/etc/env.php`. Voici la valeur par défaut :

```php
'x-frame-options' => 'SAMEORIGIN',
```

>[!TIP]
>
>Il est plus sécurisé de modifier la variable `env.php` plutôt que de définir une valeur dans Admin.

## Vérifiez votre paramètre pour `X-Frame-Options`

Pour vérifier votre paramètre, affichez les en-têtes HTTP sur n’importe quelle page de storefront. Il existe plusieurs façons de procéder, notamment l’utilisation d’un inspecteur de navigateur Web.

L’exemple suivant utilise curl, que vous pouvez exécuter à partir de n’importe quel ordinateur pouvant se connecter à votre serveur Commerce via le protocole HTTP.

Utilisez la commande suivante :

```bash
curl -I -v --location-trusted '<your storefront URL>'
```

Recherchez le `X-Frame-Options` dans les en-têtes.
