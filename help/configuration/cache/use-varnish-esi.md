---
title: Bloc ESI en pointillé
description: Découvrez les inclusions côté Edge et comment les utiliser pour incorporer des pages web.
badge: label="Contribution de Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Constantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Bloc ESI en pointillé

Edge Side Includes (ESI) sont des directives spéciales que vous pouvez utiliser pour inclure des pages web dans d’autres pages web.

Exemple :

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

Le vernis récupère le contenu de `http://domain.com/index.php/page_cache/block/esi/blocks` et remplace la balise `<esi>` par celle-ci.

## Commerce et ESI vernal

La structure Commerce crée une balise ESI lorsque les conditions suivantes sont remplies :

- L’application de mise en cache est définie sur `Varnish Cache`
- Un élément `block` de disposition XML est ajouté avec un attribut `ttl`

### Exemple

`cms_index_index.xml` :

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

Dans l’exemple ci-dessus, l’élément `block` ajoute du contenu du modèle `esi.phtml` à une page d’accueil et le vernis le met automatiquement à jour toutes les 30 secondes.

## Limites

Actuellement, Varnish ne prend pas en charge l’ESI par HTTPS et passe donc automatiquement au HTTP.

`Magento\PageCache\Observer\ProcessLayoutRenderElement` :

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
