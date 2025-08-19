---
title: 'ACP2E-3964 : produits enfants configurables avec vidéo non répertoriés via l’API REST'
description: Appliquez le correctif ACP2E-3964 pour résoudre le problème d’Adobe Commerce où les produits enfants de produits configurables avec une vidéo dans le [!UICONTROL Media Gallery] ne sont pas répertoriés via l’API REST.
feature: Products, Media, REST, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f48ced28035c65db561f4700113652574d302ec9
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# ACP2E-3964 : produits enfants configurables avec vidéo non répertoriés via l’API REST

Le correctif ACP2E-3964 corrige le problème où les produits enfants de produits configurables avec une vidéo dans le **[!UICONTROL Media Gallery]** ne sont pas répertoriés via l’API REST. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACP2E-3964. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits enfants de produits configurables avec une vidéo dans le **[!UICONTROL Media Gallery]** ne peuvent pas être répertoriés via l’API REST, ce qui entraîne une réponse d’erreur.

<u>Procédure à suivre </u> :

1. Créez un produit configurable et ajoutez un seul produit enfant.
1. Modifiez le produit enfant et ajoutez une vidéo sous **[!UICONTROL Images and Videos]** (par exemple, [https://vimeo.com/1084537](https://vimeo.com/1084537)).
1. Enregistrez le produit enfant.
1. Envoyez une requête GET au point d’entrée de l’API REST : `rest/v1/configurable-products/%sku%/children` à l’aide d’un jeton porteur administrateur.

<u>Résultats attendus</u> :

L’API REST doit renvoyer les données de produit enfant sans erreur, y compris les informations vidéo dans la **[!UICONTROL Media Gallery]**.

<u>Résultats réels</u> :

L’API REST renvoie une erreur :

```
Error: Call to a member function getVideoProvider() on null in vendor/magento/module-product-video/Model/Product/Attribute/Media/ExternalVideoEntryConverter.php:87
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
