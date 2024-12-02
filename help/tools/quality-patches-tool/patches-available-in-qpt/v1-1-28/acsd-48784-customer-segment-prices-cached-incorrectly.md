---
title: 'ACSD-48784 : les prix des segments clients sont incorrectement mis en cache entre les groupes de clients.'
description: Appliquez le correctif ACSD-48784 pour résoudre le problème Adobe Commerce en raison duquel les prix des segments de clients sont incorrectement mis en cache entre les groupes de clients.
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
exl-id: a691c61c-fdba-4d6a-8314-095dfb0ba4a1
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-48784 : les prix des segments clients sont incorrectement mis en cache entre les groupes de clients.

Le correctif ACSD-48784 corrige le problème en raison duquel les prix des segments de clients sont incorrectement mis en cache entre les groupes de clients. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 est installé. L’ID de correctif est ACSD-48784. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les prix des segments clients sont incorrectement mis en cache entre les groupes de clients.

<u>Conditions préalables</u> :

Configurez [!DNL Varnish] ou [!DNL Fastly].

<u>Étapes à reproduire</u> :

1. Activez la mise en cache complète des pages dans votre boutique.
1. Connectez-vous au site en tant qu’utilisateur disposant de tarifs spéciaux pour les groupes de clients.
1. Accédez à la page produit d’un produit avec des tarifs spéciaux pour le groupe de clients. Observez le *prix spécial*.
1. Dans un navigateur distinct, ouvrez la même page de produit qu’un utilisateur invité sans vous connecter. Observez le prix régulier.
1. Accédez à l’interface d’administration Adobe Commerce et effacez le cache Adobe Commerce et [!DNL Fastly] de ce magasin.
1. Dans le navigateur connecté, supprimez le cookie `X-Magento-Vary`.
1. Dans le navigateur connecté, rechargez plusieurs fois la même page de produit jusqu’à ce que la mise en cache soit complètement vidée.
1. Dans le navigateur non connecté, rechargez la page du produit pour maintenant afficher le prix du groupe de clients.

<u>Résultats attendus</u> :

La page Produit affiche le prix correct pour des groupes de clients spécifiques.

<u>Résultats réels</u> :

* Les utilisateurs invités voient le prix spécial de l’utilisateur connecté.
* Le mini panier affiche le prix correct une fois le produit ajouté.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
