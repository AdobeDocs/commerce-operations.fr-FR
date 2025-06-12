---
title: 'ACSD-58141 : PHPSESSID se régénère sur les requêtes POST pour les clients connectés avec le cache L2 Redis activé'
description: Appliquez le correctif ACSD-58141 pour résoudre le problème Adobe Commerce où « PHPSESSID » se régénère sur les requêtes POST sur la zone Storefront pour un client connecté avec le cache L2 Redis activé, et le client est mis à jour à partir de Admin.
feature: Customers, Cache
role: Admin, Developer
exl-id: c188c215-204c-489f-8703-4c81ca8703b7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-58141 : PHPSESSID se régénère sur les demandes [!DNL POST] pour les clients connectés si le cache L2 Redis est activé

Le correctif ACSD-58141 corrige le problème où `PHPSESSID` se régénère sur [!DNL POST] requêtes pour un client connecté si le cache L2 Redis est activé et que le client est mis à jour depuis Admin. Ce correctif est disponible lorsque la version 1.1.50 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-58141. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions Adobe Commerce et Magento Open Source :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`PHPSESSID` se régénère sur les demandes [!DNL POST] pour un client connecté avec le cache Redis L2 activé.

<u>Conditions préalables</u>

L’environnement doit être configuré avec Redis ayant au moins 3 nœuds.

<u>Procédure à suivre </u> :

1. Créez un produit simple.
1. Créez un client et connectez-vous à la vitrine.
1. Vérifiez la valeur de `PHPSESSID`.
1. Envoyez quelques requêtes [!DNL POST] (par exemple, ajout d’un produit au panier) et vérifiez que `PHPSESSID` reste le même).
1. Connectez-vous au panneau **[!UICONTROL Admin]** et modifiez le deuxième prénom du client.
1. Lorsque le deuxième prénom est enregistré, modifiez-le et enregistrez-le à nouveau plusieurs fois.
1. Sur le storefront, envoyez une requête [!DNL POST]. `PHPSESSID` aurait dû être mis à jour.
1. Sur le storefront, envoyez une autre demande de [!DNL POST] et `PHPSESSID`.
1. Répétez l’étape précédente plusieurs fois.

<u>Résultats attendus</u>

`PHPSESSID` n’est régénéré qu’une seule fois après la modification des données client.

<u>Résultats réels</u> :

La `PHPSESSID` est régénérée chaque fois que les requêtes [!DNL POST] sont envoyées.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
