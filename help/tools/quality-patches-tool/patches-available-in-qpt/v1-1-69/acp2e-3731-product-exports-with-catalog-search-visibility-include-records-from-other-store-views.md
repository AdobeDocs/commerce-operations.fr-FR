---
title: 'ACP2E-3731 : les exportations de produits avec une visibilité [!UICONTROL Catalog, Search] incluent des enregistrements d’autres vues de magasin.'
description: Appliquez le correctif ACP2E-3731 pour corriger l’Adobe Commerce où les exportations de produits avec le filtre de visibilité défini sur [!UICONTROL Catalog, Search] inclure des lignes incorrectes dans les configurations multi-magasin en raison de variations d’attributs de la portée du magasin.
feature: Data Import/Export
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7a2e98b836fcc1759910777d1e9fe50e03dabb07
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# ACP2E-3731 : les exportations de produits avec une visibilité [!UICONTROL Catalog, Search] incluent des enregistrements d’autres vues de magasin.

Le correctif ACP2E-3731 corrige le problème en raison duquel les exportations de produits avec une visibilité *[!UICONTROL Catalog, Search]* incluent incorrectement des enregistrements provenant d’autres vues de magasin dans des environnements multi-magasin. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACP2E-3731. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p9

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les exportations de produits incluent des lignes incorrectes lorsque le filtre de visibilité est défini sur *[!UICONTROL Catalog, Search]* dans des configurations multi-magasin en raison de variations d’attributs de la portée du magasin.

<u>Procédure à suivre </u> :

1. Dans le panneau d’administration, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** pour créer une vue de site web, de magasin et de magasin supplémentaire.
1. Accédez à **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* **[!UICONTROL Attribute Set]**. Cliquez sur **[!UICONTROL Add Attribute Set]** pour créer un attribut. Définissez **[!UICONTROL Based On]** sur *Par défaut*.
1. Créez un produit et affectez-le à la fois au site web principal et au site web secondaire.
1. Définissez une valeur de texte pour l’attribut nouvellement créé avec **[!UICONTROL Scope]** défini sur *Toutes les vues de la boutique*.
1. Modifiez la portée en vue de magasin secondaire et mettez à jour l’attribut avec une valeur différente.
1. Modifiez la portée en affichant la boutique par défaut et la boutique secondaire, puis définissez la visibilité du produit sur *Non visible individuellement*.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Export]**, puis sélectionnez *Produits* dans le menu déroulant.
1. Définissez un filtre où **[!UICONTROL Visibility]** = *[!UICONTROL Catalog, Search]*, puis cliquez sur **[!UICONTROL Continue]**.
1. Exécutez la commande suivante pour traiter l’exportation :

   ```
   php bin/magento queue:consumers:start exportProcessor
   ```

1. Vérifiez le fichier exporté.

<u>Résultats attendus</u> :

Seuls les enregistrements filtrés sont exportés.

<u>Résultats réels</u> :

Le fichier exporté inclut une ligne pour la vue de magasin secondaire, qui ne correspond pas aux critères de filtre définis lors de l’exportation.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
