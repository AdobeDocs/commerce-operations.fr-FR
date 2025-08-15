---
title: 'ACSD-52277 : redirection incorrecte de l’utilisateur administrateur lors de la sélection de la vue de magasin lors de la création d’une commande'
description: Appliquez le correctif ACSD-52277 pour résoudre le problème d’Adobe Commerce en raison duquel un utilisateur administrateur n’est pas correctement redirigé après avoir sélectionné la vue du magasin lors de la création d’une nouvelle commande dans Admin.
exl-id: 61ef59a9-7a31-441f-a763-2d8016498fa7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52277 : redirection incorrecte de l’utilisateur administrateur lors de la sélection de la vue de magasin lors de la création d’une commande

Le correctif ACSD-52277 corrige le problème où un utilisateur administrateur n’est pas redirigé correctement après avoir sélectionné la vue de magasin lors de la création d’une nouvelle commande dans Admin. Ce correctif est disponible lorsque la version 1.1.34 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-52277. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4, 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un utilisateur administrateur n’est pas correctement redirigé après avoir sélectionné la vue de magasin lors de la création d’une commande.

<u>Procédure à suivre</u>

1. Installez une instance propre.
1. Créez un produit.
1. Créez un site web supplémentaire, un magasin et deux vues de magasin.
1. Créez une commande auprès de l’administrateur en sélectionnant *vue de magasin 1*.

<u>Résultats attendus</u> :

L’utilisateur est redirigé vers la page de commande.

<u>Résultats réels</u> :

L’utilisateur n’est pas redirigé vers la page de commande après avoir sélectionné la vue du magasin.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
