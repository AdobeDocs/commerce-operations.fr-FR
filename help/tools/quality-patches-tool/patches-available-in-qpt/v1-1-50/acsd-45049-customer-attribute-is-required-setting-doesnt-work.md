---
title: 'ACSD-45049 : le paramètre d’attribut « Est requis » du client ne fonctionne pas selon la portée du site web dans Admin'
description: Appliquez le correctif ACSD-45049 pour résoudre le problème d’Adobe Commerce en raison duquel l’attribut « [!UICONTROL Is required] » du client n’est pas correctement remplacé conformément à la portée du site web dans Admin.
feature: Attributes, Customers
role: Admin, Developer
exl-id: 368af877-a3ec-431f-8f41-5d51354be571
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-45049 : le paramètre d’attribut de *[!UICONTROL Is required]* du client ne fonctionne pas selon la portée du site web dans Admin

Le correctif ACSD-45049 corrige le problème en raison duquel le paramètre d’attribut de *[!UICONTROL Is required]* du client ne fonctionne pas correctement selon la portée du site web dans Admin. Ce correctif est disponible lorsque la version 1.1.50 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/usage.md) est installée. L’ID du correctif est ACSD-45049. Notez que le problème a été résolu dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p7 et 2.4.5 - 2.4.5-p9

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le paramètre d’attribut de *[!UICONTROL Is required]* du client ne fonctionne pas correctement selon la portée du site web dans Admin.

<u>Procédure à suivre </u> :

1. Créez deux sites web.
1. Ouvrez **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer attribute]**.
1. Créez un attribut, définissez **[!UICONTROL Is value required]** = *Non*.
1. Passez au site web par défaut et modifiez **[!UICONTROL Is value required]** = *Oui*. La valeur par défaut est affectée à l&#39;autre site Web.
1. Créez un nouveau client à partir de l’administrateur pour le site web autre que celui par défaut.

<u>Résultats attendus</u> :

L’attribut n’est pas requis pour le site web autre que celui par défaut.

<u>Résultats réels</u> :

* L’attribut est requis pour le site web autre que celui par défaut lors de la création d’un client dans Admin.
* L’attribut n’est pas requis pour le site web autre que celui par défaut lors de l’enregistrement d’un client sur Storefront.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
