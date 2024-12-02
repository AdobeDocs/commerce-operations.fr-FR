---
title: 'MDVA-42520 : Taux d''imposition appliqué deux fois lorsque "Activer le commerce transfrontalier" est utilisé'
description: Le correctif MDVA-42520 corrige le problème où le taux d'imposition est appliqué deux fois lorsque l'option **Activer le commerce transfrontalier** est utilisée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 est installé. L’ID de correctif est MDVA-42520. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Catalog Management, Orders, Taxes
role: Admin
exl-id: 34c101fd-3a47-4877-8a41-ccaeaa010969
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# MDVA-42520 : Taux d&#39;imposition appliqué deux fois lorsque &quot;Activer le commerce transfrontalier&quot; est utilisé

Le correctif MDVA-42520 corrige le problème où le taux d&#39;imposition est appliqué deux fois lorsque le **Activer le commerce transfrontalier** est utilisé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 est installé. L’ID de correctif est MDVA-42520. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le taux de taxe est appliqué deux fois lorsque l’option **Activer le commerce transfrontalier** est utilisée.

<u>Étapes à reproduire</u> :

1. Activez **Société**, **Catalogue partagé** et **Devis**
1. Paramétrez les taxes en fonction de la capture d&#39;écran. Assurez-vous d’activer l’option **Commerce transfrontalier**.

   ![Paramètres de taxe](/help/assets/tools/tax_settings_1.png){width="700"}

1. Créer un taux d&#39;imposition pour l&#39;Allemagne (10%).
1. Créez une règle fiscale pour appliquer le taux de taxe.
1. Créez une société et un catalogue partagé personnalisé.
1. Créez un produit au prix de 100 et incluez-le dans le catalogue partagé personnalisé avec une remise de 20 %.
1. Créer un client avec une adresse allemande et l’affecter à la société
1. Ajoutez 10 produits à la carte en tant que client.
1. Accédez au panier et demandez un devis.
1. Ouvrez ce guillemet sur le serveur principal et essayez d’ajouter une remise supplémentaire de 10 %.

<u>Résultats attendus</u> :

Sous-total des citations (y compris les taxes) et Total général des citations (y compris les taxes) = 720 $

<u>Résultats réels</u> :

Sous-total des citations (y compris les taxes) et Total général des citations (y compris les taxes) = 649,50 $.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
