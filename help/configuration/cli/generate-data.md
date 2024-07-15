---
title: Génération de données pour les tests de performance
description: Découvrez comment générer une grande quantité de données à utiliser pour les tests de performance.
feature: Configuration, Orders
exl-id: 2f54701d-88c4-464a-b4dc-56db14d54160
source-git-commit: d4a6d5cd181c7c4426914bbe481f4d5d1e828b5e
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 9%

---

# Données de test de performance

## Profils

Vous pouvez ajuster la quantité de données que vous créez à l’aide des _profils_ (petits, moyens, grands et très grands). Les profils se trouvent dans le répertoire `<magento_root>/setup/performance-toolkit/profiles/<ce|ee>`.

Par exemple, `/var/www/html/magento2/setup/performance-toolkit/profiles/ce`

La figure suivante montre l’affichage d’un produit sur le storefront à l’aide du profil _small_ :

![Exemple de vitrine avec données générées](../../assets/configuration/generate-data.png)

Le tableau suivant fournit des détails sur les profils du générateur de données : petit, moyen, grand et très grand.

| Paramètre | Petit profil | Profil Medium | Profil multi-site Medium | Profil volumineux | Profil volumineux supplémentaire |
| --- | --- | --- | --- | --- | --- |
| `websites` | 1 | 3 | 25 | 5 | 5 |
| `store_groups` | 1 | 3 | 25 | 5 | 5 |
| `store_views` | 1 | 3 | 50 | 5 | 5 |
| `simple_products` | 800 | 24 000 | 4 000 | 300 000 | 600 000 |
| `configurable_products` | 16 avec 24 options | 640 avec 24 options | 800 avec 24 options et 79 avec 200 options | 8 000 avec 24 options | 16 000 avec 24 options |
| `product_images` | 100 images / 3 images par produit | 1 000 images / 3 images par produit | 1 000 images / 3 images par produit | 2 000 images / 3 images par produit | 2 000 images / 3 images par produit |
| `categories` | 30 | 300 | 100 | 3 000 | 6 000 |
| `categories_nesting_level` | 3 | 3 | 3 | 5 | 5 |
| `catalog_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `catalog_target_rules` | 5 | 5 | 5 | 5 | 5 |
| `cart_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `cart_price_rules_floor` | 2 | 2 | 2 | 2 | 2 |
| `customers` | 200 | 2 000 | 2 000 | 5 000 | 10 000 |
| `tax rates` | 130 | 40 000 | 40 000 | 40 000 | 40 000 |
| `orders` | 80 | 50 000 | 50 000 | 100 000 | 150 000 |

### Exécution du générateur de données

{{file-system-owner}}

>[!WARNING]
>
>Avant d’exécuter le générateur de données, désactivez toutes les tâches cron exécutées sur le serveur. La désactivation des tâches cron empêche le générateur de données d’effectuer des actions qui entrent en conflit avec les tâches cron actives et évite les erreurs inutiles.
>
>Si vous avez l’intention d’implémenter des événements avec [!DNL Adobe I/O Events for Adobe Commerce] lors du test des performances, exécutez cette commande avant d’abonner [events](https://developer.adobe.com/commerce/extensibility/events/). L’inscription préalable d’événements peut entraîner des erreurs.

Exécutez la commande comme décrit dans cette section. Une fois la commande exécutée, vous devez [réindexer tous les indexeurs](../cli/manage-indexers.md).

Options de commande :

```bash
bin/magento setup:perf:generate-fixtures <path-to-profile>
```

Où `<path-to-profile>` spécifie le chemin d’accès absolu au système de fichiers et le nom d’un profil.

Par exemple,

```bash
bin/magento setup:perf:generate-fixtures /var/www/html/magento2/setup/performance-toolkit/profiles/ce/small.xml
```

Exemple de sortie pour le petit profil :

```terminal
Generating profile with following params:
    |- Websites: 1
    |- Store Groups Count: 1
    |- Store Views Count: 1
    |- Categories: 30
    |- Attribute Sets (Default): 3
    |- Attribute Sets (Extra): 10
    |- Simple products: 800
    |- Configurable products: 0
    |--- 5 products for attribute set "Attribute Set 1"
    |--- 5 products for attribute set "Attribute Set 2"
    |--- 5 products for attribute set "Attribute Set 3"
    |--- 40 products for attribute set "Dynamic Attribute Set 1-24"
    |- Product images: 100, 3 per product
    |- Customers: 200
    |- Cart Price Rules: 20
    |- Catalog Price Rules: 20
    |- Catalog Target Rules: 5
    |- Orders: 80
Generating websites, stores and store views...  done in <time>
Generating categories...  done in <time>
Generating attribute sets...  done in <time>
Generating simple products...  done in <time>
... more ...
```

## Correctifs de performances

### Utilisateurs administrateurs

Génère les utilisateurs administrateurs. Noeud de profil XML :

```xml
<!-- Number of admin users -->
<admin_users>{int}</admin_users>
```

### Jeux d’attributs

Génère des jeux d’attributs avec la configuration spécifiée. Noeud de profil XML :

```xml
<!-- Number of product attribute sets -->
<product_attribute_sets>{int}</product_attribute_sets>

<!-- Number of attributes per set -->
<product_attribute_sets_attributes>{int}</product_attribute_sets_attributes>

<!-- Number of values per attribute -->
<product_attribute_sets_attributes_values>{int}</product_attribute_sets_attributes_values>
```

### Lot de produits

Génère des produits en bundle. Les sélections de lots générées ne s’affichent pas individuellement dans le catalogue. Les produits sont répartis uniformément par catégories et par sites web. Si `assign_entities_to_all_websites` du profil est défini sur `1`. Les produits sont attribués à tous les sites web.

Noeud de profil XML :

```xml
<!-- Number of products -->
<bundle_products>{int}</bundle_products>

<!-- Number of options per each product -->
<bundle_products_options>{int}</bundle_products_options>

<!-- Number of simple products per each option -->
<bundle_products_variation>{int}</bundle_products_variation>
```

### Règles de prix du panier

Génère des règles de prix de panier. Noeud de profil XML :

```xml
<!-- Number of cart price rules -->
<cart_price_rules>{int}</cart_price_rules>

<!-- Number of conditions per rule -->
<cart_price_rules_floor>{int}</cart_price_rules_floor>
```

### Règles de prix du catalogue

Génère des règles de prix de catalogue. Noeud de profil XML :

```xml
<!-- Number of catalog price rules -->
<catalog_price_rules>{int}</catalog_price_rules>
```

### Catégories

Génère des catégories. Si `assign_entities_to_all_websites` est défini sur `0`, toutes les catégories sont réparties uniformément par catégories racine ; dans le cas contraire, toutes les catégories sont affectées à une seule catégorie racine.

Noeud de profil XML :

```xml
<!-- Number of categories to generate -->
<categories>{int}</categories>

<!-- Nesting level of categories -->
<categories_nesting_level>{int}</categories_nesting_level>
```

### Configurations

Définit des valeurs pour les champs de configuration. Noeud de profil XML :

```xml
<!-- Config variables and values for change -->
<configs>
    <config>
        <path>{string}</path> <!-- e.g. admin/security/use_form_key -->
        <scope>{string}</scope> <!-- e.g. default -->
        <scopeId>{int}</scopeId>
        <value>{int|string}</value>
    </config>

    <!-- ... more entries ... -->
</configs>
```

### Produits configurables

Génère des produits configurables. Les options configurables générées ne s’affichent pas individuellement dans le catalogue. Les produits sont répartis uniformément par catégories et par sites web. Si `assign_entities_to_all_websites` est défini sur `1`, les produits sont attribués à tous les sites Web.

Les formats de noeud XML suivants sont pris en charge :

- Distribution par jeu d’attributs par défaut et prédéfini :

  ```xml
  <!-- Number of configurable products -->
  <configurable_products>{int}</configurable_products>
  ```

- Générer des produits en fonction d’un jeu d’attributs existant :

  ```xml
  <configurable_products>
  
      <config>
              <!-- Existing attribute set name -->
              <attributeSet>{string}</attributeSet>
  
              <!-- Configurable sku pattern with %s -->
              <sku>{string}</sku>
  
              <!-- Number of configurable products -->
              <products>{int}</products>
  
              <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
              <category>[{string}]</category>
  
              <!-- Type of Swatch attribute e.g. color|image -->
              <swatches>{string}</swatches>
      </config>
  
  <!-- ... more entries ... -->
  </configurable_products>
  ```

- Générer des produits à partir d’un jeu d’attributs créé dynamiquement avec un nombre spécifié d’attributs et d’options :

  ```xml
  <configurable_products>
  
      <config>
          <!-- Number of attributes in configurable product -->
          <attributes>{int}</attributes>
  
          <!-- Number of options per attribute -->
          <options>{int}</options>
  
          <!-- Configurable sku pattern with %s -->
          <sku>{string}</sku>
  
          <!-- Number of configurable products -->
          <products>{int}</products>
  
          <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
          <category>[{string}]</category>
  
          <!-- Type of Swatch attribute e.g. color|image -->
          <swatches>{string}</swatches>
      </config>
  
      <!-- ... more entries ... -->
  </configurable_products>
  ```

- Générer des produits à partir d’un jeu d’attributs créé dynamiquement avec une configuration spécifiée pour chaque attribut :

  ```xml
  <configurable_products>
  
      <config>
          <attributes>
              <!-- Configuration for a first attribute -->
              <attribute>
                  <!-- Amount of options per attribute -->
                  <options>{int}</options>
  
                  <!-- Type of Swatch attribute -->
                  <swatches>{string}</swatches>
              </attribute>
  
              <!-- Configuration for a second attribute -->
              <attribute>
                  <!-- Amount of options per attribute -->
                  <options>{int}</options>
              </attribute>
          </attributes>
  
          <!-- Configurable sku pattern with %s -->
          <sku>{string}</sku>
  
          <!-- Number of configurable products -->
          <products>{int}</products>
  
          <!-- Category Name. Optional. By default, the category name from Categories fixture will be used -->
          <category>[{string}]</category>
      </config>
  
      <!-- ... more entries ... -->
  </configurable_products>
  ```

### Clients

Génère des clients. Les clients disposent d’une distribution normale sur tous les sites web disponibles. Chaque client possède les mêmes données, à l’exception de l’adresse électronique du client, du groupe de clients et des adresses du client.

Noeud de profil XML :

```xml
<!-- Number of customers to generate -->
<customers>{int}</customers>
```

Vous pouvez utiliser le code XML suivant pour modifier la configuration du client :

```xml
<customer-config>
    <!-- Number of addresses per each customer -->
    <addresses-count>{int}</addresses-count>
</customer-config>
```

### Images de produit

Génère des images de produit. La génération n’inclut pas le redimensionnement.

Noeud de profil XML :

```xml
<product-images>
    <!-- Number of images to generate -->
    <images-count>{int}</images-count>

    <!-- Number of images to be assigned per each product -->
    <images-per-product>{int}</images-per-product>
</product-images>
```

### État des indexeurs

Met à jour l’état des indexeurs. Noeud de profil XML :

```xml
<indexer>
    <!-- Name of indexer (e.g. catalogrule_product) -->
    <id>{string}</id>
    <set_scheduled>{bool}</set_scheduled>
</indexer>
```

### Commandes

Génère des commandes avec un nombre configurable de différents types d’articles de commande. Vous pouvez également générer des guillemets inactifs pour les commandes générées.

Noeud de profil XML :

```xml
<!-- It is necessary to enable quotes for orders -->
<order_quotes_enable>{bool}</order_quotes_enable>

<!-- Min number of simple products per each order -->
<order_simple_product_count_from>{int}</order_simple_product_count_from>

<!-- Max number of simple products per each order -->
<order_simple_product_count_to>{int}</order_simple_product_count_to>

<!-- Min number of configurable products per each order -->
<order_configurable_product_count_from>{int}</order_configurable_product_count_from>

<!-- Max number of configurable products per each order -->
<order_configurable_product_count_to>{int}</order_configurable_product_count_to>

<!-- Min number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_from>{int}</order_big_configurable_product_count_from>

<!-- Max number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_to>{int}</order_big_configurable_product_count_to>

<!-- Number of orders to generate -->
<orders>{int}</orders>
```

### Produits simples

Génère des produits simples. Les produits sont distribués par défaut et par jeux d’attributs prédéfinis. Si des jeux d’attributs supplémentaires sont spécifiés dans le profil comme suit : `<product_attribute_sets>{int}</product_attribute_sets>`, les produits sont également distribués par jeux d’attributs supplémentaires.

Les produits sont répartis uniformément par catégories et par sites web. Si `assign_entities_to_all_websites` est défini sur `1`, les produits sont attribués à tous les sites Web.

Noeud de profil XML :

```xml
<!-- Number of simple products to generate -->
<simple_products>{int}</simple_products>
```

### Sites web

Génère des sites web. Noeud de profil XML :

```xml
<!-- Number of websites to be generated -->
<websites>{int}</websites>
```

### Groupes de magasin

Génère des groupes de magasins (appelés dans l’administrateur _stores_). Les groupes de magasins sont distribués normalement entre les sites web.

Noeud de profil XML :

```xml
<!-- Number of store groups to be generated -->
<store_groups>{int}</store_groups>
```

### Vues du magasin

Génère des vues de magasin. Les vues des magasins sont distribuées normalement entre les groupes de magasins. Noeud de profil XML :

```xml
<!-- Number of store views to be generated -->
<store_views>{int}</store_views>

<!-- 1 means that all stores will have the same root category, 0 means that all stores will have unique root category -->
<assign_entities_to_all_websites>{0|1}<assign_entities_to_all_websites/>
```

### Taux d&#39;imposition

Génère des taux d&#39;imposition. Noeud de profil XML :

```xml
<!-- Accepts name of CSV file with tax rates (<path to Commerce folder>/setup/src/Magento/Setup/Fixtures/_files) -->
<tax_rates_file>{CSV file name}</tax_rates_file>
```

## Informations de configuration supplémentaires :

- `<Commerce root dir>/setup/performance-toolkit/config/attributeSets.xml` : ensembles d’attributs par défaut

- `<Commerce root dir>/setup/performance-toolkit/config/customerConfig.xml` - Configuration client

- `<Commerce root dir>/setup/performance-toolkit/config/description.xml` : configuration de description complète du produit

- `<Commerce root dir>/setup/performance-toolkit/config/shortDescription.xml` : configuration de description courte du produit

- `<Commerce root dir>/setup/performance-toolkit/config/searchConfig.xml` : configuration pour une description courte et complète du produit. Cette ancienne mise en oeuvre est fournie à des fins de rétrocompatibilité.

- `<Commerce root dir>/setup/performance-toolkit/config/searchTerms.xml` : petit nombre de termes de recherche à en termes courts et complets

- `<Commerce root dir>/setup/performance-toolkit/config/searchTermsLarge.xml` : nombre plus important de termes de recherche à utiliser dans une description courte et complète.
