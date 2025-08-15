---
title: 'ACSD-53643 : le total de la commande est incorrect lors de la passation d''une commande fournisseur'
description: Appliquez le correctif ACSD-53643 pour résoudre le problème d’Adobe Commerce où le total de la commande est incorrect lors de la passation d’une commande fournisseur avec des produits désactivés ou en rupture de stock.
feature: B2B
role: Admin, Developer
exl-id: 72b52695-ef3c-4143-9e77-901463d4a9ed
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-53643 : le total de la commande est incorrect lors de la passation d&#39;une commande fournisseur

Le correctif ACSD-53643 corrige le problème en raison duquel le total de la commande est incorrect lors de la passation d&#39;une commande fournisseur avec des produits désactivés ou en rupture de stock. Ce correctif est disponible lorsque la version 1.1.41 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-53643. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le total de la commande est incorrect lors de la passation d&#39;une commande fournisseur avec des produits désactivés ou en rupture de stock.

<u>Procédure à suivre </u> :

1. Installez *[!UICONTROL B2B]* et *[!UICONTROL Inventory]*.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** et définissez **[!UICONTROL Company]** = *Oui* et **[!UICONTROL Purchase Order]** = *Oui*.
1. Effacez le cache de configuration.
1. Créez une nouvelle entreprise, activez-la et activez-la *[!UICONTROL Purchase order]* pour l’entreprise.
1. Créez un nouvel utilisateur pour la société.
1. Créez une *Règle d&#39;approbation* pour approuver toutes les commandes supérieures à 1 *USD* par l&#39;administrateur de la société.
1. Créez une source supplémentaire.
1. Connectez-vous en tant que nouvel utilisateur d’entreprise.
1. Ajoutez deux produits au panier et passez un bon de commande.
1. Désactivez le deuxième produit.
1. Connectez-vous en tant qu’administrateur d’entreprise.
1. Ouvrez la commande fournisseur et vérifiez qu&#39;elle contient les deux produits et que le total est pour les deux produits.
1. Validez la commande fournisseur.
1. Passez la commande.
1. Ouvrez les détails de la commande.

<u>Résultats attendus</u> :

* Impossible de passer la commande même si un produit de la commande est *désactivé* ou *en rupture de stock*.
* *[!UICONTROL Place Order]* bouton est masqué.

<u>Résultats réels</u> :

La commande passée contient uniquement le premier produit actif, mais le total de la commande est calculé pour les deux produits.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
