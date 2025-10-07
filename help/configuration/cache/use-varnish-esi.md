---
title: Bloc d'ESI vernis
description: Découvrez les inclusions côté Edge (ESI) de Varnish et comment incorporer des pages web pour Adobe Commerce. Découvrez l’implémentation et l’optimisation des blocs ESI.
badge: label="Contribution Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---

# Bloc d&#39;ESI vernis

Les inclusions côté Edge (ESI) sont des directives spéciales que vous pouvez utiliser pour inclure des pages web dans d’autres pages web.

Par exemple :

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

Le vernis récupère le contenu de `http://domain.com/index.php/page_cache/block/esi/blocks` et remplace la balise `<esi>` par celui-ci.

## ESI Commerce et vernis

Le framework Commerce crée une balise ESI lorsque les conditions suivantes sont remplies :

- L’application de mise en cache est définie sur `Varnish Cache`
- Un élément de `block` de mise en page XML est ajouté avec un attribut `ttl`

### Exemple

`cms_index_index.xml` :

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

Dans l’exemple ci-dessus, l’élément `block` ajoute le contenu du modèle `esi.phtml` à une page d’accueil et Varnish le met automatiquement à jour toutes les 30 secondes.

## Restrictions

Actuellement, Varnish ne prend pas en charge l’ESI via HTTPS et passe donc automatiquement au HTTP.

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
