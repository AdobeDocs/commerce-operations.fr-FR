---
title: Bonnes pratiques pour modifier le code PHP principal et tiers
description: Découvrez comment et à quel moment modifier le code Adobe Commerce principal et le code PHP tiers.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2023-12-8
exl-id: 32b3137d-fc00-4be8-ba02-5d8d48a51fe1
source-git-commit: d47567a8d69ccdae3db01e964f1db12e8ae26717
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 0%

---

# Bonnes pratiques pour modifier ou remplacer le code PHP principal et tiers

Ce document décrit les bonnes pratiques à suivre lorsque vous devez modifier la fonctionnalité, le résultat ou l’entrée d’un code que vous n’avez pas créé ou que vous ne contrôlez pas directement. En d’autres termes, le code principal et le code tiers. Ce document se concentre principalement sur le code PHP principal.

## Méthodes de modification de code

Lors de la modification du code, il est important de tenir compte de la portée de vos modifications. La « portée » des modifications fait référence à la portée des effets des modifications du code. Il est recommandé de baser la décision relative à la manière dont l’implémentation finale sera effectuée sur l’option ayant la plus faible empreinte et la plus faible utilisation des ressources. Plus la portée des remplacements de code est étendue, plus une équipe de développement s’écarte des fonctionnalités de base d’Adobe Commerce, ce qui augmente la probabilité de bogues et les efforts de maintenance de la base de code.

### Patch

Un correctif est un fichier qui contient des instructions pour modifier directement le code dans un fichier qui n’est pas sous le contrôle direct de l’équipe de développement. Il s’agit d’une option qui doit généralement être envisagée en dernier recours lorsqu’il n’existe aucune autre option. Les correctifs sont destinés à être une solution temporaire. Si vous devez créer un dispositif transdermique, la bonne pratique générale consiste à retirer le dispositif transdermique au profit d’une solution plus permanente dans les 2 à 4 semaines suivantes. 

Les patchs se cassent facilement. Si les fichiers ciblés par le correctif sont mis à jour, le correctif cesse souvent de fonctionner. En effet, un fichier de correctif contient des numéros de ligne et de colonne qui indiquent précisément ce que le correctif doit modifier. Si quelque chose ne correspond pas à ce que le correctif attendait, il cesse de s’appliquer et rompt le code.

```bash
diff --git a/vendor/magento/module-quote/Model/QuoteManagement.php b/vendor/magento/module-quote/Model/QuoteManagement.php
index 51b68411d40..ac4a3468322 100644
--- a/vendor/magento/module-quote/Model/QuoteManagement.php
+++ b/vendor/magento/module-quote/Model/QuoteManagement.php
@@ -424,8 +424,9 @@ class QuoteManagement implements CartManagementInterface
                 }
             }
             $quote->setCustomerIsGuest(true);
-            $groupId = $customer ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID;
-            $quote->setCustomerGroupId($groupId);
+            $quote->setCustomerGroupId(
+                $quote->getCustomerId() ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID
+            );
         }
  
         $remoteAddress = $this->remoteAddress->getRemoteAddress();
```

#### Éléments pouvant être modifiés par un correctif

N&#39;importe quoi. Littéralement, n’importe quel caractère d’un fichier ciblé peut être modifié. Les correctifs ne sont pas limités à un type de fichier ou un langage de code particulier. En règle générale, vous devez utiliser un correctif pour cibler les fichiers dans le répertoire `vendor`. 

#### Quand utiliser un correctif

Si vous réalisez qu&#39;il n&#39;y a pas d&#39;autre option. Par exemple, lorsque le fournisseur n’a pas encore publié de correctif pour le code, vous pouvez utiliser un correctif pour résoudre temporairement le problème en attendant une solution permanente.

#### Inconvénients

Les patchs se cassent facilement. Dès que le code ciblé change, le correctif cesse de fonctionner. Elles ne sont censées être qu&#39;une solution à court terme.

### Préférence

Une préférence est un concept intégré à la plateforme Adobe Commerce. Il s&#39;agit essentiellement d&#39;un « remplacement de classe PHP ».

La plateforme Adobe Commerce utilise un « gestionnaire d&#39;objets » pour instancier les classes PHP, car elle n&#39;instancie pas les classes PHP avec le nouveau mot-clé comme c&#39;est le cas dans les applications PHP traditionnelles. Au lieu de cela, le gestionnaire d&#39;objets croise le nom de la classe PHP à instancier par rapport à une configuration compilée pour déterminer si un module a déclaré une préférence pour la classe d&#39;origine. Si une préférence est trouvée pour la classe PHP, le gestionnaire d&#39;objets instancie la classe spécifiée à la place.

Il est à noter que (habituellement) la nouvelle classe PHP qui remplace la classe PHP d&#39;origine étend/hérite de la classe PHP d&#39;origine. Cela est fait pour plusieurs raisons :

- Pour garantir que l&#39;injection dépendante/l&#39;indication de type est respectée. Dans le cas contraire, une erreur fatale se produit et l’application est interrompue.
- Pour permettre une écriture de code minimale. Si la classe PHP d&#39;origine contient dix méthodes mais que vous n&#39;avez besoin de remplacer qu&#39;une seule, vous pouvez généralement changer une méthode seule et laisser les neuf autres méthodes intactes. Cela est important pour vous assurer que vous ne bloquez pas les mises à jour des fonctionnalités principales lorsque la plateforme est mise à niveau vers de nouvelles versions.

#### Déclarer une préférence

Il est assez simple de déclarer une préférence. Une seule ligne de code doit être ajoutée à un fichier `di.xml` dans un module . Vous pouvez le faire globalement ou dans n’importe quelle « zone » d’Adobe Commerce, comme `frontend`, `adminhtml`, `graphql`, `webapi_rest` et `crontab`.

```xml
<preference for="Magento\Elasticsearch7\SearchAdapter\Adapter" type="Vendor\Namespace\Adapter\AlgoliaElasticSearch7Adapter"/>
```

```php
<?php

declare(strict_types=1);

namespace Vendor\Namespace\Adapter;

class AlgoliaElasticSearchAdapter extends \Magento\Elasticsearch7\SearchAdapter\Adapter
{
}
```

#### Ce qui peut être modifié avec une préférence

Seules les classes PHP peuvent être remplacées par une préférence. Dans la classe PHP, vous pouvez modifier les méthodes et propriétés publiques et protégées. Pour les méthodes publiques et protégées, vous pouvez remplacer entièrement la méthode ou vous pouvez modifier les arguments entrant dans la méthode parent d’origine (ou le résultat en sortant).

Techniquement, les méthodes privées ne peuvent pas être remplacées. Cependant, vous pouvez créer votre propre remplacement de la méthode privée d’origine. Vous pouvez même lui donner un nom arbitraire, vous pouvez également utiliser le nom d&#39;origine. Cela n’a pas d’importance, car une méthode privée n’existe que dans le fichier qui la contient. Pour remplacer une méthode privée, vous devez remplacer ou modifier la méthode publique ou protégée qui appelle la méthode privée d’origine et vous devez remplacer votre propre fonctionnalité.

#### Quand utiliser une préférence

Une fois de plus, vous devez utiliser les préférences lorsqu’il n’existe aucune autre option et lorsque vous ne pouvez pas atteindre votre objectif avec l’injection de dépendance, un plug-in ou un observateur. Il peut arriver que vous ayez besoin d’une préférence si vous devez modifier ou remplacer des méthodes ou propriétés privées ou protégées. Il convient de noter que les préférences doivent être utilisées avec parcimonie. Ils sont une méthode assez « gourmande » de changer l&#39;application et vous prenez effectivement possession de la classe PHP. Cela peut entraîner des conflits avec les modules tiers et bloquer les mises à jour de la classe principale, ce qui entraîne des bugs difficiles à diagnostiquer. La plateforme Adobe Commerce a été conçue pour inclure d’autres méthodes permettant d’apporter des modifications au code sous-jacent avec une empreinte plus réduite.

#### Inconvénients

Les préférences sont un moyen gourmand de modifier le code et ne doivent être utilisées que lorsque d’autres options n’existent pas. Les préférences peuvent souvent entraîner des conflits au sein de la base de code et, pire encore, elles peuvent bloquer les mises à jour de base qui se produisent avec les mises à niveau de la plateforme. 

### Observateur

Un observateur est le concept d’écouteur d’événement, qui se trouve dans de nombreuses applications, plateformes, bibliothèques et langages de codage. Le concept n’est pas propre à la plateforme Adobe Commerce. Les observateurs font partie intégrante de la plateforme depuis l’époque de Magento 1 et sont considérés comme un choix principal quant à la manière de modifier le code principal et le code tiers. 

La base de code principale et les modules tiers peuvent distribuer un événement à un emplacement choisi dans le code. L’observateur, qui est déclaré dans un fichier `events.xml` et écoute l’événement distribué par son nom, peut travailler à un niveau global ou être limité à une « zone » Adobe Commerce, telle que `frontend`, `adminhtml`, `graphql`, `webapi_rest` et `crontab`.

#### Comment déclarer un observateur

Les observateurs peuvent être configurés dans un fichier `events.xml` global ou spécifique à une zone.

```xml
    <event name="sales_model_service_quote_submit_before">
        <observer name="set_reward_flag_order" instance="Adobe\RewardAdjustments\Observer\SetOrderRewardFlag" />
    </event>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\RewardAdjustments\Observer;

use Magento\Framework\Event\ObserverInterface;
use Magento\Framework\Event\Observer;
use Magento\Quote\Model\Quote;
use Magento\Sales\Api\Data\OrderInterface;

class SetOrderRewardFlag implements ObserverInterface
{
    /**
     * @param Observer $observer
     * @return void
     */
    public function execute(Observer $observer)
    {
        $event = $observer->getEvent();
        /* @var $order OrderInterface */
        $order = $event->getOrder();
        /** @var $quote Quote $quote */
        $quote = $event->getQuote();

        // do something to the order and/or quote object here
    }
}
```

#### Ce qui peut être changé avec un observateur

Les observateurs ne s’appliquent qu’au code PHP de la plateforme Adobe Commerce. Vous pouvez uniquement modifier les données et objets spécifiques qui sont transmis avec le Dispatcher d’événement.

#### Quand utiliser un observateur

Dès que possible ! Si les observateurs étaient plus largement disponibles et plus souples, ils occuperaient la deuxième place sur cette liste. Les observateurs ont moins de frais de traitement que les plug-ins. Ils sont moins disponibles et moins flexibles.

#### Inconvénients

Bien que les observateurs soient un excellent moyen d’intercepter et de modifier le code, l’envoi des événements doit être ajouté au code principal ou tiers pour que votre code puisse les écouter. Cela limite un peu le concept d&#39;utilisation d&#39;observateurs. Vous êtes limité aux événements qu’un développeur a eu la prévoyance d’inclure dans le code.

En outre, un autre facteur de limitation pour les observateurs est que l’événement distribué permet uniquement d’accéder aux données et objets spécifiques que le développeur a décidé de transmettre avec l’événement.

### Plug-in

Le plug-in est un concept flexible introduit dans la plateforme Adobe Commerce. Il vous permet d&#39;intercepter, remplacer et modifier toutes les méthodes PHP publiques. Les modules externes vous permettent de modifier les arguments entrant dans une méthode avant l&#39;exécution de la méthode ciblée, de modifier le résultat après l&#39;exécution de la méthode ciblée ou de remplacer complètement la méthode ciblée. Vous pouvez modifier de nombreuses méthodes d’une classe PHP ciblée dans un seul fichier de plug-in. En outre, vous pouvez utiliser l&#39;argument `$subject` pour exécuter toutes les méthodes publiques qui existent dans la classe PHP ciblée.

#### Comment déclarer un plug-in

Les modules externes peuvent être configurés dans un fichier `di.xml` global ou spécifique à une zone.

```xml
    <type name="Magento\Catalog\Api\CategoryRepositoryInterface">
        <plugin name="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin" type="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin"/>
    </type>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\CatalogAdjustments\Plugin;

class CategoryRepositoryPlugin
{
    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param int $categoryId
     * @param int $storeId
     *
     * @return array
     */
    public function beforeGet($subject, $categoryId, $storeId = null): array
    {
        // modify the $categoryId or $storeId arguments or perform some other functionality prior to execution of the `get` method
        return [$categoryId, $storeId];
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Closure $origMethod
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function aroundGet($subject, $origMethod, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you can do something before calling the original method
        $result = $origMethod($categoryId, $storeId);
        // here you can do something after calling the original method
        // you can also NOT call the original method at all and instead, substitute our own functionality

        return $result;
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Magento\Catalog\Api\Data\CategoryInterface $result
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function afterGet($subject, $result, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you modify the result produced by the original `get` function or you can execute some other functionality
        // note that you also have access to the original function arguments. it's too late to modify them, but if needed, they are available for reading

        return $result;
    }
}
```

#### Changements possibles avec un plug-in

Cette fonctionnalité n&#39;est disponible que pour les classes PHP cibles. Vous pouvez modifier l’entrée ou la sortie d’une méthode publique et utiliser un module externe pour déclencher d’autres fonctionnalités. Si plusieurs plug-ins ciblent la même classe PHP, un ordre de tri pour l&#39;exécution des plug-ins peut être défini pour permettre à votre plug-in de s&#39;exécuter avant ou après d&#39;autres plug-ins.

#### Quand utiliser un module externe

Lorsque le remplacement de dépendance n’est pas disponible. Les plug-ins sont couramment utilisés dans la base de code principale, dans le code tiers, et peuvent être couramment utilisés dans votre propre code personnalisé. En règle générale, lorsque vous devez modifier des fonctionnalités qui ne sont pas détenues ni contrôlées par votre code personnalisé, un plug-in est la solution.

#### Inconvénients

Impossible de modifier les méthodes ou propriétés protégées. La surcharge de traitement est supérieure à celle d’un observateur. Ce n&#39;est pas vraiment un argument pour ne pas utiliser de plugins, la différence est triviale. Cependant, c&#39;est une bonne chose à garder à l&#39;esprit.

### Remplacement de dépendance

L’injection de dépendance est un concept de codage orienté objet standard dans lequel vous transmettez vos dépendances requises dans une classe avec le constructeur . Cependant, la plateforme Adobe Commerce va encore plus loin en offrant plusieurs possibilités de substituer des dépendances au XML. Essentiellement, le remplacement des personnes à charge. Le remplacement des dépendances ne convient pas à toutes les situations, mais il permet une écriture de code minimale, une faible surcharge, et vous pouvez cibler de manière étroite des éléments de code exacts uniquement. Vous pouvez modifier les méthodes privées et protégées avec le remplacement des dépendances.

#### Utilisation du remplacement des dépendances

Le remplacement de la dépendance peut être effectué à l&#39;échelle mondiale ou à l&#39;échelle d&#39;une région.

```php
<?php

class SomeClass
{
    public function __construct(
        private readonly AllowedCountries $allowedCountriesReader
    ) {}

    /**
     * Check is address allowed for store
     *
     * @param AddressInterface $address
     * @param int|null $storeId
     * @return bool
     */
    private function isAddressAllowedForWebsite(AddressInterface $address, $storeId): bool
    {
        $allowedCountries = $this->allowedCountriesReader->getAllowedCountries(ScopeInterface::SCOPE_STORE, $storeId);

        return in_array($address->getCountryId(), $allowedCountries);
    }
}
```

```php
<?php

use Magento\Store\Model\ScopeInterface;

class OverrideAllowedCountries extends AllowedCountries
{
    /**
     * Retrieve all allowed countries for scope or scopes
     *
     * @param string $scope
     * @param string|null $scopeCode
     * @return array
     * @since 100.1.2
     */
    public function getAllowedCountries(
        $scope = ScopeInterface::SCOPE_WEBSITE,
        $scopeCode = null
    ) {
        // do some stuff here
        // you can call the original method or override it completely
        
        return $something;
    }
}
```

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Vendor\Namespace\SomeClass">
        <arguments>
            <argument name="allowedCountriesReader" xsi:type="object">OverrideAllowedCountries</argument>
        </arguments>
    </type>
</config>
```

Après avoir suivi ces étapes, vous aurez correctement modifié le comportement d’une méthode privée.

#### Ce qui peut être modifié par le remplacement des dépendances

Les méthodes publiques, protégées et privées peuvent être modifiées par le remplacement des dépendances. Comme avec un module externe, vous pouvez modifier les arguments qui y sont intégrés, remplacer complètement la fonction ou modifier la sortie de la fonction.

#### Quand utiliser le remplacement des dépendances

Il s’agit d’une bonne première option lorsqu’elle permettrait d’atteindre l’objectif souhaité, en supposant qu’il n’y ait rien de trop complexe à mettre en œuvre.

#### Inconvénients

Pas beaucoup. Ce n&#39;est pas utilisable dans toutes les situations. L’inconvénient principal est que vous devez étendre la classe d’origine qui contient la fonctionnalité que vous souhaitez modifier. Cela va à l&#39;encontre du principe de la « composition sur l&#39;héritage ».
