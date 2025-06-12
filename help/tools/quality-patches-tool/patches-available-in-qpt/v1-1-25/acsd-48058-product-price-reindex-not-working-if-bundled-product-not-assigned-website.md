---
title: 'ACSD-48058 : la réindexation du prix du produit ne fonctionne pas si le produit groupé n’est pas affecté à un site Web'
description: Appliquez le correctif ACSD-48058 pour résoudre le problème d’Adobe Commerce en raison duquel la réindexation du prix du produit ne fonctionne pas si le produit groupé n’est attribué à aucun site web.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 270e1b5d-75e0-4374-973a-2bb37161ceec
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-48058 : la réindexation du prix du produit ne fonctionne pas si le produit groupé n’est pas affecté à un site Web

Le correctif ACSD-48058 corrige le problème en raison duquel la réindexation du prix du produit ne fonctionne pas si le produit groupé n’est affecté à aucun site web. Ce correctif est disponible lorsque la version 1.1.25 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48058. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La réindexation du prix des produits ne fonctionne pas si le produit groupé n’est affecté à aucun site web.

<u>Procédure à suivre </u> :

1. Accédez à Admin Adobe Commerce > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et créez un nouveau produit groupé, ou modifiez un produit groupé existant.
   * Cliquez sur l&#39;onglet **[!UICONTROL Product in Websites]** et décochez toutes les cases (sites web)
   * Enregistrer le produit
1. Effectuez la réindexation.

<u>Résultats attendus</u> :

La réindexation a été effectuée.

<u>Résultats réels</u> :

L’erreur suivante est générée lors de l’exécution de l’indice des prix des produits :

```bash
Undefined array key <bundel product id > in vendor/magento/module-bundle/Model/ResourceModel/Indexer/Price/DisabledProductOptionPriceModifier.php on line 117
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
