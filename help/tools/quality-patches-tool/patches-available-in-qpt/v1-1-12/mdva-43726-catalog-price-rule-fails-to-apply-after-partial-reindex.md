---
title: 'MDVA-43726 : la règle de prix de catalogue ne s’applique pas après une réindexation partielle'
description: Le correctif MDVA-43726 corrige le problème en raison duquel la règle de prix de catalogue basée sur la correspondance d’attributs au niveau du magasin ne s’applique pas après une réindexation partielle. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-43726. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
exl-id: db536749-eb89-4bb5-9c69-f448f74497b8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# MDVA-43726 : la règle de prix de catalogue ne s’applique pas après une réindexation partielle

Le correctif MDVA-43726 corrige le problème en raison duquel la règle de prix de catalogue basée sur la correspondance d’attributs au niveau du magasin ne s’applique pas après une réindexation partielle. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-43726. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La règle de prix catalogue basée sur la correspondance d’attributs au niveau du magasin ne s’applique pas après une réindexation partielle.

<u>Procédure à suivre </u> :

1. Définissez le mode de l’indexeur pour qu’il s’exécute selon le calendrier.
1. Créez deux attributs de produit configurables. Par exemple : Couleur (Échantillon visuel) et Taille (Échantillon de texte).
1. Créez un produit configurable à l’aide des deux attributs créés à l’étape 2.
1. Après avoir créé les produits, créez un attribut de type **Oui/Non** et rendez-le visible dans les conditions de la règle.
1. Ajoutez cet attribut au jeu d’attributs par défaut.
1. Créez une règle de prix de catalogue à appliquer lorsque cet attribut est défini sur **Oui**.
1. Ouvrez l’un des produits simples liés au produit configurable.
1. Modifiez la portée pour stocker l’affichage et mettez à jour la valeur de l’attribut sur **Oui**.
1. Exécutez le `CRON` et vérifiez le prix sur le serveur frontal.
1. Exécutez une réindexation complète. Là encore, vérifiez le prix sur le front-end.
1. Mettez à jour la catégorie de produits configurable.
1. Exécutez le `CRON` et vérifiez à nouveau le prix sur le serveur frontal.

<u>Résultats attendus</u> :

La règle de catalogue s’applique correctement sans réindexation complète à l’aide d’indexeurs incrémentiels.

<u>Résultats réels</u> :

La règle de catalogue ne s’applique pas sans exécuter une réindexation complète.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
