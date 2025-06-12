---
title: 'ACSD-50858 : amélioration des performances pour le chargement du contenu des bannières'
description: Appliquez le correctif ACSD-50858 pour résoudre le problème d’Adobe Commerce en raison duquel les performances des bannières sont affectées dans le panier ou la page de passage en caisse en raison de requêtes de base de données excessives et d’un temps de chargement de page accru.
feature: Page Content
role: Admin
exl-id: 1b46e51f-70ad-4450-b3a8-173c2e4b7925
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# ACSD-50858 : amélioration des performances pour le chargement du contenu des bannières

Le correctif ACSD-50858 corrige un problème de performances des bannières dans la page de panier/passage en caisse : *requêtes de base de données excessives et temps de chargement de page accru*. Ce correctif est disponible lorsque la version 1.1.31 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-50858. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les performances des bannières sont affectées dans la page de panier/passage en caisse en raison de *requêtes de base de données excessives et d’un temps de chargement de page accru*.

Ce problème a été corrigé en refactorisant la façon dont le contenu des bannières est chargé, ce qui a réduit le nombre de requêtes de base de données de 99,99 % et le temps de chargement des pages de ~99 %.

<u>Procédure à suivre </u> :

1. Connectez-vous à Admin et créez un produit simple.
1. Créez un client ou une cliente à partir de l’administration ou du serveur frontal et ajoutez une adresse de livraison pour ce client ou cette cliente.
1. Déplacez banners.php vers le dossier `magento_root/pub/`.
1. Générez des bannières à l’aide de la commande `php pub/banners.php` . Il génère 10 000 bannières simples et 1 000 bannières avec des règles de vente.
1. Connectez-vous au client créé précédemment sur le serveur frontal.
1. Ajoutez le produit créé précédemment au panier.
1. Accédez à la page de passage en caisse (passage en caisse/panier).
1. Surveillez le temps de chargement de la requête `banner/ajax/load` :

   * Sans `bin/magento dev:query-log:enable`
   * Avec `bin/magento dev:query-log:enable`

     ```
     grep 'magento_banner_content' var/debug/db.log  | wc -l
     ```

<u>Résultats attendus</u> :

Diminution du nombre de requêtes de base de données pour le temps de chargement des pages de `magento_banner_content` et de panier/passage en caisse.

<u>Résultats réels</u> :

Augmentation du nombre de requêtes de base de données pour le `magento_banner_content` et le temps de chargement de la page de panier/passage en caisse.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Informations supplémentaires

<u>contenu banners.php</u> :

```php
\Banner::class);
    $banner->setIsEnabled(
        \Magento\Banner\Model\Banner::STATUS_ENABLED
    )->setName(
        'Test Dynamic Block '.$i
    )->setTypes(
        ''
    )->setStoreContents(
        [0 => 'Dynamic Block Content '.$i]
    )->save();
}

$objectManager = \Magento\Framework\App\ObjectManager::getInstance();

/** @var \Magento\SalesRule\Model\Rule $salesRule */
$salesRule = $objectManager->create(\Magento\SalesRule\Model\Rule::class);
$salesRule->setData(
    [
        'name' => '50% Off ',
        'is_active' => 1,
        'customer_group_ids' => [\Magento\Customer\Model\GroupManagement::NOT_LOGGED_IN_ID],
        'coupon_type' => \Magento\SalesRule\Model\Rule::COUPON_TYPE_NO_COUPON,
        'conditions' => [
            [
                'type' => \Magento\SalesRule\Model\Rule\Condition\Address::class,
                'attribute' => 'base_subtotal',
                'operator' => '>',
                'value' => 0
            ]
        ],
        'simple_action' => 'by_percent',
        'discount_amount' => 50,
        'discount_step' => 0,
        'stop_rules_processing' => 1,
        'website_ids' => [
           1
        ]
    ]
);
$salesRule->save();

for ($i = 0; $i < 1000; $i++) {

    $banner = $objectManager->create(\Magento\Banner\Model\Banner::class);
    $banner->setData(
        [
            'name' => 'Get 50% Off ',
            'is_enabled' => \Magento\Banner\Model\Banner::STATUS_ENABLED,
            'types' => [], /*Any Banner Type*/
            'store_contents' => ['<img src="http://example.com/banner_40_percent_off.png" />'],
            'banner_sales_rules' => [$salesRule->getId()],
        ]
    );
    $banner->save();
}
```

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
