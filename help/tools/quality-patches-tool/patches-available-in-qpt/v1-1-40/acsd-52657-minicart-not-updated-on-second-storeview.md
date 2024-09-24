---
title: "ACSD-52657 : Minicart non mis à jour sur le deuxième storeview utilisant le sous-domaine"
description: Appliquez le correctif ACSD-52657 pour résoudre le problème Adobe Commerce en raison duquel le minicart n’est pas mis à jour dans la seconde vue de magasin qui utilise un sous-domaine.
feature: Shopping Cart
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-52657 : Minicart n’est pas mis à jour sur le deuxième storeview qui utilise le sous-domaine

Le correctif ACSD-52657 corrige le problème en raison duquel le minicart n’est pas mis à jour sur la deuxième vue de magasin qui utilise un sous-domaine. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 est installé. L’ID de correctif est ACSD-52657. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Minicart n’est pas mis à jour dans l’aperçu de magasin secondaire qui utilise un sous-domaine.

<u>Étapes à reproduire</u> :

1. Créez un deuxième storeview et configurez un sous-domaine pour l’URL de base.
1. Mettez à jour le domaine du cookie pour qu’il ait le domaine commun.
1. Sur la boutique principale, ajoutez un produit au panier.
1. Actualisez la deuxième vue de magasin, puis accédez à la page Panier.

<u>Résultats attendus</u> :

Le panier et le minicart sont mis à jour sur le sous-domaine .

<u>Résultats réels</u> :

Minicart n’est pas mis à jour lorsque le magasin secondaire est actualisé, mais la page du panier affiche le produit ajouté et vous pouvez passer une commande dans cette session (`PHPSESSID` cookie est partagé).

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
