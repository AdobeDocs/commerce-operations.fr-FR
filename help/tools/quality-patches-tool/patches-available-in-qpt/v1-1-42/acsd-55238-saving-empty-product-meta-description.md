---
title: 'ACSD-55238 : enregistrement de la méta-description du produit vide'
description: Appliquez le correctif ACSD-55238 pour résoudre le problème Adobe Commerce en raison duquel une description de produit contenant le code d’HTML généré par [!DNL Page Builder] ou un autre éditeur d’HTML s’affiche toujours dans la métamdescription, et il n’est pas possible de la définir sur vide.
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 39ccf1bb-a71a-47a0-b252-e6331e2df9b0
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-55238 : enregistrement de la méta-description du produit vide

Le correctif ACSD-55238 corrige le problème en raison duquel une description de produit contenant le code d’HTML généré par un éditeur d’HTML s’affiche toujours dans la méta-description. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 est installé. L’ID de correctif est ACSD-55238. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une description de produit qui contient le code d’HTML généré par [!DNL Page Builder] ou un autre éditeur d’HTML s’affiche toujours dans la méta-description et il n’est pas possible de la définir sur vide.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** et créez un nouveau bloc avec tout contenu.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** et créez un produit. Définissez la méta-description sur vide.
1. Ajoutez le bloc créé ci-dessus à l’aide de *[!DNL Page Builder]* dans l’onglet *[!UICONTROL Content]* et enregistrez le produit.
1. Ouvrez le produit sur le storefront et vérifiez son élément de document `meta name = "description"`.

<u>Résultats attendus</u> :

La méta-description est vide.

<u>Résultats réels</u> :

Lorsqu’une description d’un produit contient un bloc, il est utilisé pour la méta-description du produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
