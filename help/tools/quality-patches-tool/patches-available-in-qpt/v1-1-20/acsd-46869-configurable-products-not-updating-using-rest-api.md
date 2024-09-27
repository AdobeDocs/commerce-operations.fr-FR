---
title: "ACSD-46869 : produits configurables ne se mettant pas à jour à l’aide de l’API REST au passage en caisse"
description: Le correctif ACSD-46869 corrige le problème en raison duquel les produits configurables ne sont pas mis à jour à l’aide de l’API REST lors du passage en caisse. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 est installé. L’ID de correctif est ACSD-46869. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-46869 : produits configurables ne se mettant pas à jour à l’aide de l’API REST au passage en caisse

Le correctif ACSD-46869 corrige le problème en raison duquel les produits configurables ne sont pas mis à jour à l’aide de l’API REST lors du passage en caisse. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 est installé. L’ID de correctif est ACSD-46869. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 à 2.4.5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL QPT] landing page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits configurables ne sont pas mis à jour à l’aide de l’API REST lors du passage en caisse.

<u>Étapes à reproduire</u> :

1. Créez un produit configurable avec des attributs de couleur et de taille.
1. Sélectionnez **[!UICONTROL Options]** et ajoutez le produit au panier.
1. Accédez à **[!UICONTROL Checkout]**, mettez à jour la taille plusieurs fois, à l’exception de la quantité, et vérifiez la requête et la réponse.
1. Vous obtenez la réponse suivante lorsque vous mettez à jour la taille.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Résultats attendus</u> :

La valeur est mise à jour en fonction des modifications.

<u>Résultats réels</u> :

`option_value` n’est pas mis à jour. Par conséquent, lorsque la commande est placée, elle a l’ancienne valeur de taille.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tools] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de l’outil de correctifs de qualité.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans [!DNL QPT], reportez-vous à la section [Correctifs disponibles dans [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) du guide de l’outil Correctifs de qualité.
