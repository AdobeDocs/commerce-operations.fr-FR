---
title: Configurer le bloc ESI Varnish
description: Découvrez les inclusions côté Edge (ESI) de Varnish et comment incorporer des pages web pour Adobe Commerce. Découvrez l’implémentation et l’optimisation des blocs ESI.
badge: label="Contribution Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
badgePaas: label="Sur Site" type="Informative" url="https://experienceleague.adobe.com/fr/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets sur site Adobe Commerce."
autotag-review: '2026-06-22T22:02:08.706Z'
TQID: 'https://experienceleague.adobe.com/hzsfaZyHuUhzfb86anO43PfP-62WRPOoMbYOh-H1vqo'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 159
ht-degree: 0%

---

# Configurer le bloc ESI Varnish {#varnish-esi-block}

{{varnish-config-cloud}}

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

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

Dans l’exemple ci-dessus, l’élément `block` ajoute le contenu du modèle `esi.phtml` à une page d’accueil et Varnish le met automatiquement à jour toutes les 30 secondes.

## Restrictions

Actuellement, Varnish ne prend pas en charge l’ESI via HTTPS et passe donc automatiquement au HTTP.

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
