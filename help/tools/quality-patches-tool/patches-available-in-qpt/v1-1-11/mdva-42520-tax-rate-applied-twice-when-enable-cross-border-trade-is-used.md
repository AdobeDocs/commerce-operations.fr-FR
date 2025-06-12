---
title: 'MDVA-42520 : taux de taxe appliqué deux fois lorsque l''option « Activer le commerce transfrontalier » est utilisée'
description: Le correctif MDVA-42520 corrige le problème en raison duquel le taux de taxe est appliqué deux fois lorsque le **Activer le commerce transfrontalier** est utilisé. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 est installé. L’ID du correctif est MDVA-42520. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Catalog Management, Orders, Taxes
role: Admin
exl-id: 34c101fd-3a47-4877-8a41-ccaeaa010969
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# MDVA-42520 : taux de taxe appliqué deux fois lorsque l&#39;option « Activer le commerce transfrontalier » est utilisée

Le correctif MDVA-42520 corrige le problème en raison duquel le taux de taxe est appliqué deux fois lorsque le **Activer le commerce transfrontalier** est utilisé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 est installé. L’ID du correctif est MDVA-42520. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le taux de taxe est appliqué deux fois lorsque le **Activer le commerce transfrontalier** est utilisé.

<u>Procédure à suivre </u> :

1. Activez **Société**, **Catalogue partagé** et **Devis**
1. Configurez les taxes en fonction de la capture d’écran. Assurez-vous d’activer **Commerce transfrontalier**.

   ![paramètres fiscaux](/help/assets/tools/tax_settings_1.png){width="700"}

1. Créer un taux d&#39;imposition pour l&#39;Allemagne (10%).
1. Créez une règle de taxe pour appliquer le taux de taxe.
1. Créez une entreprise et un catalogue partagé personnalisé.
1. Créez un produit au prix de 100 et incluez-le dans le catalogue partagé personnalisé avec une remise de 20 %.
1. Créez un client avec une adresse en allemand et affectez-la à la société
1. Ajoutez 10 produits à la carte en tant que client ou cliente.
1. Accédez au panier et demandez un devis.
1. Ouvrez ce devis sur le serveur principal et essayez d’ajouter une remise supplémentaire de 10 %.

<u>Résultats attendus</u> :

Sous-total du devis (taxes comprises) et total général du devis (taxes comprises) = 720 $

<u>Résultats réels</u> :

Sous-total du devis (taxes comprises) et total général du devis (taxes comprises) = 649,50 $.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
