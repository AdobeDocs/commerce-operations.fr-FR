---
title: "ACSD-48058 : la réindexation des prix du produit ne fonctionne pas si le produit groupé n’est pas affecté à un site web"
description: Appliquez le correctif ACSD-48058 pour résoudre le problème Adobe Commerce en raison duquel la réindexation des prix du produit ne fonctionne pas si le produit fourni n’est affecté à aucun site web.
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-48058 : la réindexation des prix du produit ne fonctionne pas si le produit groupé n’est pas affecté à un site web

Le correctif ACSD-48058 corrige le problème en raison duquel la réindexation des prix du produit ne fonctionne pas si le produit fourni n’est affecté à aucun site web. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 est installé. L’ID de correctif est ACSD-48058. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La réindexation des prix du produit ne fonctionne pas si le produit fourni n’est affecté à aucun site web.

<u>Étapes à reproduire</u> :

1. Accédez à l’Admin Adobe Commerce > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et créez un produit regroupé ou modifiez un produit déjà regroupé.
   * Cliquez sur l’onglet **[!UICONTROL Product in Websites]** et décochez toutes les cases (sites web).
   * Enregistrer le produit
1. Effectuez la réindexation.

<u>Résultats attendus</u> :

La réindexation est effectuée avec succès.

<u>Résultats réels</u> :

L’erreur suivante est générée lors de l’exécution de l’indice des prix du produit :

```bash
Undefined array key <bundel product id > in vendor/magento/module-bundle/Model/ResourceModel/Indexer/Price/DisabledProductOptionPriceModifier.php on line 117
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
