---
title: Bonnes pratiques relatives à la modification du code PHP principal et tiers
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

# Bonnes pratiques relatives à la modification ou au remplacement de code PHP principal et tiers

Ce document décrit les bonnes pratiques lorsque la nécessité se présente de modifier la fonctionnalité, le résultat ou la saisie de tout code que vous n’avez pas créé ou que vous n’avez pas directement contrôlé. En d’autres termes, le code principal et le code tiers. Ce document se concentre principalement sur le code PHP principal.

## Méthodes de modification du code

Lors de la modification du code, il est important de tenir compte de la portée de vos modifications. La &quot;portée&quot; des modifications fait référence à l’ampleur des effets des modifications du code. Il est recommandé de baser la décision sur la manière dont la mise en oeuvre finale est effectuée en fonction de l’option ayant le plus faible impact et la moins grande utilisation des ressources. Plus les remplacements de code sont étendus, plus une équipe de développement s’éloigne des fonctionnalités de base d’Adobe Commerce, augmentant la probabilité de bogues et intensifiant les efforts de maintenance du code base à l’avenir.

### Correctif

Un correctif est un fichier qui contient des instructions pour modifier directement le code dans un fichier qui n’est pas sous le contrôle direct de l’équipe de développement. Il s’agit d’une option qui doit généralement être considérée en dernier recours lorsqu’il n’existe aucune autre option. Les correctifs sont destinés à être une solution temporaire. Si vous devez créer un correctif, en règle générale, supprimez le correctif au profit d’une solution plus permanente dans les 2 à 4 semaines suivantes. 

Les correctifs se cassent facilement. Si les fichiers que le correctif cible sont mis à jour, cela entraîne souvent l’arrêt du fonctionnement du correctif. En effet, un fichier de correctif contient des numéros de ligne et de colonne qui indiquent spécifiquement ce qui doit être modifié par le correctif. Si un élément ne correspond pas à ce que le correctif attendait, il cesse d’appliquer et interrompt le code.

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

#### Modifications possibles avec un correctif

N&#39;importe quoi. Littéralement, tout caractère d’un fichier ciblé peut être modifié. Les correctifs ne sont pas limités à un type de fichier ou à un langage de code particulier. En règle générale, vous utilisez un correctif pour cibler des fichiers dans le répertoire `vendor`. 

#### Quand utiliser un correctif

Si vous vous rendez compte qu&#39;il n&#39;existe aucune autre option. Par exemple, lorsque le fournisseur doit encore publier un correctif pour le code, vous pouvez utiliser un correctif pour résoudre temporairement le problème en attendant une solution permanente.

#### Inconvénients

Les correctifs se cassent facilement. Dès que le code ciblé change, le correctif cesse de fonctionner. Elles ne sont censées être qu&#39;une solution à court terme.

### Préférence

Une préférence est un concept conçu dans la plateforme Adobe Commerce. C&#39;est essentiellement un &quot;remplacement de classe PHP&quot;.

La plateforme Adobe Commerce utilise un &quot;gestionnaire d’objets&quot; pour instancier des classes PHP, car elle n’instancie pas les classes PHP avec le nouveau mot-clé, comme c’est le cas dans les applications PHP traditionnelles. Au lieu de cela, le gestionnaire d’objets fait référence de manière croisée au nom de la classe PHP à instancier par rapport à une configuration compilée afin de déterminer si un module a déclaré une préférence pour la classe d’origine. Si une préférence pour la classe PHP est trouvée, le gestionnaire d’objets instancie la classe spécifiée à la place.

Notez que (généralement) la nouvelle classe PHP remplaçant la classe PHP d’origine étend/hérite de la classe PHP d’origine. Cela est fait pour plusieurs raisons :

- Pour garantir le respect de l’injection/du conseil de type de dépendance. Dans le cas contraire, une erreur fatale se produit et l’application est interrompue.
- Pour permettre une écriture de code minimale. Si la classe PHP d’origine contient dix méthodes, mais qu’il suffit de remplacer une seule, vous pouvez généralement changer une méthode seule et conserver les neuf autres. Il est important de s’assurer que vous ne bloquez pas les mises à jour des fonctionnalités de base, car la plateforme est mise à niveau vers de nouvelles versions.

#### Déclarer une préférence

Il est assez simple de déclarer une préférence. Une seule ligne de code doit être ajoutée à un fichier `di.xml` dans un module. Cela peut être effectué globalement ou dans n’importe quelle &quot;zone&quot; Adobe Commerce, par exemple `frontend`, `adminhtml`, `graphql`, `webapi_rest` et `crontab`.

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

#### Modifications possibles avec une préférence

Seules les classes PHP peuvent être remplacées par une préférence. Dans la classe PHP, vous pouvez modifier les méthodes et propriétés publiques et protégées. Pour les méthodes publiques et protégées, vous pouvez remplacer entièrement la méthode ou modifier les arguments entrant (ou le résultat sortant) dans la méthode parent d’origine.

Techniquement, les méthodes privées ne peuvent pas être remplacées. Cependant, vous pouvez créer votre propre remplacement pour la méthode privée d’origine. Vous pouvez même lui donner un nom arbitraire, vous pouvez aussi utiliser le nom d&#39;origine. Cela n’a pas d’importance car une méthode privée existe uniquement dans le fichier qui le contient. Pour remplacer une méthode privée, vous devez remplacer ou modifier la méthode publique ou protégée qui appelle la méthode privée d’origine et vous devez remplacer vos propres fonctionnalités à la place.

#### Quand utiliser une préférence

Une fois de plus, vous devez utiliser les préférences lorsqu’il n’existe aucune autre option et que vous ne pouvez pas atteindre votre objectif avec l’injection de dépendance, un module externe ou un observateur. Il peut arriver que vous ayez besoin d’une préférence si vous devez modifier ou remplacer des méthodes ou des propriétés privées ou protégées. Il est à noter que les préférences doivent être utilisées avec modération. C&#39;est une méthode assez &quot;gourmande&quot; pour changer l&#39;application et vous prenez en charge la classe PHP. Cela peut entraîner des conflits avec les modules tiers et bloquer les mises à jour de la classe principale et conduire à des bogues difficiles à diagnostiquer. La plateforme Adobe Commerce a été conçue pour inclure d’autres moyens permettant de modifier le code sous-jacent avec un encombrement moindre.

#### Inconvénients

Les préférences sont un moyen gourmand de modifier le code et ne doivent être utilisées que lorsque d’autres options n’existent pas. Les préférences peuvent souvent entraîner des conflits au sein du code base, mais pire encore, elles peuvent bloquer les mises à jour de base qui se produisent avec les mises à niveau de la plateforme. 

### Observateur

Un observateur est le concept d’un écouteur d’événement, comme on le trouve dans de nombreuses applications, plateformes, bibliothèques et langages de codage. Le concept n’est pas propre à la plateforme Adobe Commerce. Les observateurs sont intégrés à la plateforme depuis l’époque de Magento 1 et sont considérés comme un choix principal de la modification du code principal et du code tiers. 

Le code base principal et tout module tiers peuvent distribuer un événement à un emplacement donné dans le code. L’observateur, qui est déclaré dans un fichier `events.xml` et qui écoute l’événement distribué par nom, peut travailler à un niveau global ou être limité à n’importe quelle &quot;zone&quot; Adobe Commerce, telle que `frontend`, `adminhtml`, `graphql`, `webapi_rest` et `crontab`.

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

#### Modifications possibles avec un observateur

Les observateurs s’appliquent uniquement au code PHP dans la plateforme Adobe Commerce. Vous pouvez uniquement modifier les données et les objets spécifiques transmis avec la distribution de l’événement.

#### Quand utiliser un observateur

Dès que possible ! Si les observateurs étaient plus disponibles et plus flexibles, les observateurs occuperaient la deuxième place dans cette liste. Les observateurs ont moins de surcharge de traitement que les modules externes, ils sont moins disponibles et moins flexibles.

#### Inconvénients

Bien que les observateurs constituent un excellent moyen d’intercepter et de modifier le code, l’envoi des événements doit être ajouté au code principal ou tiers pour que votre code puisse l’écouter. Cela rend le concept d&#39;utiliser des observateurs un peu limité. Vous êtes limité aux événements qu’un développeur a la prévoyance d’inclure dans le code.

En outre, un autre facteur limitatif pour les observateurs est que l’événement distribué ne donne accès qu’aux données et aux objets spécifiques que le développeur a décidé de transmettre avec l’événement.

### Module externe

Un module externe est un concept flexible introduit dans la plateforme Adobe Commerce. Il vous permet d’intercepter, de remplacer et de modifier toutes les méthodes PHP publiques. Les plug-ins vous permettent de modifier les arguments d’une méthode avant l’exécution de la méthode ciblée, de modifier le résultat après l’exécution de la méthode ciblée ou de remplacer entièrement la méthode ciblée. Vous pouvez modifier de nombreuses méthodes d’une classe PHP ciblée dans un seul fichier de module externe. Vous pouvez également utiliser l’argument `$subject` pour exécuter toutes les méthodes publiques existant dans la classe PHP ciblée.

#### Comment déclarer un module externe

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

#### Éléments pouvant être modifiés avec un module externe

Cette fonctionnalité est uniquement disponible pour les classes PHP. Vous pouvez modifier l’entrée ou la sortie d’une méthode publique et vous pouvez utiliser un module externe pour déclencher d’autres fonctionnalités. Si plusieurs modules externes ciblent la même classe PHP, un ordre de tri peut être défini pour l’exécution des modules externes afin que le module externe puisse s’exécuter avant ou après d’autres modules externes.

#### Quand utiliser un module externe

Chaque fois que le remplacement de dépendance n’est pas disponible. Les modules externes sont généralement utilisés dans l’ensemble du code base, du code tiers et peuvent généralement l’être dans votre propre code personnalisé. En règle générale, lorsque vous devez modifier des fonctionnalités qui ne sont pas détenues ou contrôlées par votre code personnalisé, un module externe est la solution.

#### Inconvénients

Impossible de modifier les méthodes ou propriétés protégées. La surcharge de traitement est supérieure à celle d’un observateur. Ce n&#39;est pas vraiment un argument de ne pas utiliser de plugins, la différence est triviale. Cependant, il est bon de garder cela à l’esprit.

### Remplacement de dépendance

L’injection de dépendance est un concept de codage standard orienté objet dans lequel vous transmettez vos dépendances requises dans une classe avec le constructeur. Cependant, la plateforme Adobe Commerce va plus loin en offrant plusieurs moyens de substituer des dépendances à XML. Essentiellement, le remplacement des dépendances. Le remplacement des dépendances n’est pas adapté à toutes les situations, mais il permet une écriture de code minimale, une surcharge faible et vous pouvez cibler des éléments de code exacts uniquement. Vous pouvez modifier des méthodes privées et protégées avec le remplacement de dépendances.

#### Utilisation du remplacement de dépendance

Le remplacement des dépendances peut être effectué sur une base globale ou spécifique à une zone.

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

Après avoir suivi ces étapes, vous avez modifié le comportement d’une méthode privée.

#### Modifications possibles avec le remplacement de dépendances

Les méthodes publiques, protégées et privées peuvent être modifiées par le remplacement de dépendances. Comme avec un module externe, vous pouvez modifier les arguments entrants, complètement remplacer la fonction ou modifier la sortie de la fonction.

#### Quand utiliser le remplacement de dépendance

Il s’agit là d’une première option judicieuse lorsqu’elle atteindrait effectivement l’objectif souhaité, en supposant qu’il n’ait rien à faire de trop complexe à mettre en oeuvre.

#### Inconvénients

Pas beaucoup. Il n&#39;est pas utilisable dans toutes les situations. L’inconvénient principal est que vous devez étendre la classe d’origine qui contient la fonctionnalité que vous souhaitez modifier. Cela va à l&#39;encontre du principe de &quot;Composition par rapport à Héritage&quot;.
