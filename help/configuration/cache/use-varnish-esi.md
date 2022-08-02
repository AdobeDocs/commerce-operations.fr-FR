---
title: Bloc ESI de marque
description: Découvrez Edge Side Includes et comment les utiliser pour incorporer des pages web.
contributor_name: Goivvy LLC
contributor_link: https://www.goivvy.com/magento-optimization-service
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Bloc ESI de marque

Edge Side Includes (ESI) sont des directives spéciales que vous pouvez utiliser pour inclure des pages web dans d’autres pages web.

Exemple :

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

Le vernis récupère le contenu à partir de `http://domain.com/index.php/page_cache/block/esi/blocks` et remplacez la fonction `<esi>` avec.

## Commerce et vernissage de l’ESI

La structure Commerce crée une balise ESI lorsque les conditions suivantes sont remplies :

- L’application de mise en cache est définie sur `Varnish Cache`
- Une disposition XML `block` est ajouté avec un élément `ttl` attribute

### Exemple

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

Dans l’exemple ci-dessus, la variable `block` ajoute du contenu à partir de la fonction `esi.phtml` sur une page d’accueil et Varnish la met automatiquement à jour toutes les 30 secondes.

## Limites

Actuellement, Varnish ne prend pas en charge l’ESI par HTTPS et passe donc automatiquement au HTTP.

`Magento\PageCache\Observer\ProcessLayoutRenderElement`:

```php
    private function _wrapEsi(
        \Magento\Framework\View\Element\AbstractBlock $block,
        \Magento\Framework\View\Layout $layout
    ) {
    ....
        // Varnish does not support ESI over HTTPS must change to HTTP
        $url = substr($url, 0, 5) === 'https' ? 'http' . substr($url, 5) : $url;
        return sprintf('<esi:include src="%s" />', $url);
    }
```
