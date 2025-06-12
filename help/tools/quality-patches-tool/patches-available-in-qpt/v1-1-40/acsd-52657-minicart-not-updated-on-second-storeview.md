---
title: 'ACSD-52657 : Minicart non mis à jour sur le deuxième magasin qui utilise le sous-domaine'
description: Appliquez le correctif ACSD-52657 pour résoudre le problème Adobe Commerce où le mini-art n'est pas mis à jour sur le deuxième magasin qui utilise un sous-domaine.
feature: Shopping Cart
role: Admin, Developer
exl-id: feec9dde-5532-481b-9410-7f6be9df4be7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-52657 : Minicart non mis à jour sur le deuxième magasin qui utilise le sous-domaine

Le correctif ACSD-52657 corrige le problème où le minicart n&#39;est pas mis à jour sur le deuxième magasin qui utilise un sous-domaine. Ce correctif est disponible lorsque la version 1.1.40 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-52657. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Minicart n&#39;est pas mis à jour sur la boutique secondaire qui utilise un sous-domaine.

<u>Procédure à suivre </u> :

1. Créez un deuxième magasin et configurez un sous-domaine pour l’URL de base.
1. Mettez à jour le domaine du cookie pour avoir le domaine commun.
1. Dans le magasin principal, ajoutez un produit au panier.
1. Actualisez le deuxième magasin, puis accédez à la page du panier.

<u>Résultats attendus</u> :

Le panier et le mini-panier sont mis à jour sur le sous-domaine.

<u>Résultats réels</u> :

Le minicart n’est pas mis à jour lorsque le magasin secondaire est actualisé, mais la page du panier affiche le produit ajouté et vous pouvez passer une commande dans cette session (`PHPSESSID` cookie est partagé).

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
