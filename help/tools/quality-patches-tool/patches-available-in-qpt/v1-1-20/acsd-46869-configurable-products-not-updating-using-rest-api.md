---
title: 'ACSD-46869 : produits configurables qui ne sont pas mis à jour à l’aide de l’API REST lors du passage en caisse'
description: Le correctif ACSD-46869 corrige le problème en raison duquel les produits configurables ne sont pas mis à jour à l’aide de l’API REST lors du passage en caisse. Ce correctif est disponible lorsque l’[Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20 est installé. L’ID du correctif est ACSD-46869. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
exl-id: f03d4b24-ac95-406e-8e9d-908149b9207c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-46869 : produits configurables qui ne sont pas mis à jour à l’aide de l’API REST lors du passage en caisse

Le correctif ACSD-46869 corrige le problème en raison duquel les produits configurables ne sont pas mis à jour à l’aide de l’API REST lors du passage en caisse. Ce correctif est disponible lorsque la version 1.1.20 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-46869. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL QPT] page de destination](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits configurables ne sont pas mis à jour à l’aide de l’API REST lors du passage en caisse.

<u>Procédure à suivre </u> :

1. Créez un produit configurable avec des attributs de couleur et de taille.
1. Sélectionnez **[!UICONTROL Options]** et ajoutez le produit au panier.
1. Accédez à **[!UICONTROL Checkout]**, mettez à jour la taille plusieurs fois à l’exception de qty, puis vérifiez la requête et la réponse.
1. La réponse suivante s’affiche lorsque vous mettez à jour la taille.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Résultats attendus</u> :

La valeur est mise à jour en fonction des modifications.

<u>Résultats réels</u> :

`option_value` n’est pas mis à jour. Par conséquent, lorsque la commande est passée, elle a l’ancienne valeur de taille.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tools] > Utilisation ](/help/tools/quality-patches-tool/usage.md) dans le guide de l’outil de correctifs de qualité.
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
