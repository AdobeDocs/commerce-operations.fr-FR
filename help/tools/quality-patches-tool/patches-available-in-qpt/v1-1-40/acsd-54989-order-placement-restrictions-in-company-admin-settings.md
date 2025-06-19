---
title: 'ACSD-54989 : l’administrateur de la société ne peut pas commander lorsque [!UICONTROL Enable Purchase Orders] avez la valeur Oui et [!UICONTROL Purchase Order] la valeur Non'
description: Appliquez le correctif ACSD-54989 pour résoudre le problème d’Adobe Commerce en raison duquel l’administrateur de la société ne peut pas passer de commandes si [!UICONTROL Enable Purchase Orders] est défini sur Oui et [!UICONTROL Purchase Order] sur Non.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: 13830361-dd0c-486f-b07f-34280a17ab76
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-54989 : l’administrateur de la société ne peut pas commander lorsque *[!UICONTROL Enable Purchase Orders]* avez la valeur *Oui* et *[!UICONTROL Purchase Order]* la valeur *Non*

Le correctif ACSD-54989 corrige le problème où les commandes ne peuvent pas être passées si **[!UICONTROL Enable Purchase Orders]** avez la valeur *Oui* et **[!UICONTROL Purchase Order]** la valeur *Non*. Ce correctif est disponible lorsque la version 1.1.40 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54989. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les administrateurs de la société ne peuvent pas passer de commandes lorsque **[!UICONTROL Enable Purchase Orders]** est défini sur *Oui* et **Bon de commande** sur *Non*.

<u>Conditions préalables</u> :

Installez les modules [!DNL B2B].

<u>Procédure à suivre </u> :

1. Activez la société et laissez [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *Non*.
1. Créez un produit simple au prix de 100.
1. Créez une nouvelle entreprise via l’Administration.
1. Définissez [!UICONTROL **Activer les commandes fournisseur**] sur *Oui*.
1. Connectez-vous en tant qu’administrateur d’entreprise sur le storefront.
1. Ajoutez le produit simple créé au panier.
1. Accédez à la page de passage en caisse et cliquez sur **[!UICONTROL Place Order]** pour terminer l’achat.

<u>Résultats attendus</u> :

Vous pouvez passer une commande avec succès.

<u>Résultats réels</u> :

La page **[!UICONTROL My Account]** s’ouvre et la commande n’est pas passée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
