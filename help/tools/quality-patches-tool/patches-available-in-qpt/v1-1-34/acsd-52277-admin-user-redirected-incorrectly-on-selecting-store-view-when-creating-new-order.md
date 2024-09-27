---
title: "ACSD-52277 : l’utilisateur administrateur a redirigé incorrectement la sélection de la vue de magasin lors de la création d’une commande"
description: Appliquez le correctif ACSD-52277 pour résoudre le problème Adobe Commerce en raison duquel un utilisateur administrateur n’est pas redirigé correctement après avoir sélectionné la vue de magasin lors de la création d’une commande dans Admin.
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52277 : L’utilisateur administrateur a redirigé incorrectement la sélection de la vue de magasin lors de la création d’une nouvelle commande.

Le correctif ACSD-52277 corrige le problème lorsqu’un utilisateur administrateur n’est pas redirigé correctement après avoir sélectionné la vue de magasin lors de la création d’une commande dans Admin. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34 est installé. L’ID de correctif est ACSD-52277. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4, 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un utilisateur administrateur n’est pas redirigé correctement après avoir sélectionné la vue de magasin lors de la création d’une nouvelle commande.

<u>Étapes à reproduire</u>

1. Installez une instance propre.
1. Créez un produit.
1. Créez un site web supplémentaire, un magasin et deux vues de magasin.
1. Créez une commande à partir de l’administrateur en sélectionnant *vue de magasin 1*.

<u>Résultats attendus</u> :

L’utilisateur est redirigé vers la page de commande.

<u>Résultats réels</u> :

L’utilisateur n’est pas redirigé vers la page de commande après avoir sélectionné la vue de magasin.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
