---
title: "ACSD-48771 : l’éditeur WYSIWYG effectue un rendu du contenu différent"
description: Appliquez le correctif ACSD-48771 pour résoudre le problème Adobe Commerce où l’éditeur WYSIWYG effectue un rendu du contenu différent.
feature: Cache, Page Content
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# ACSD-48771 : l’éditeur WYSIWYG effectue un rendu du contenu différent

Le correctif ACSD-48771 corrige le problème en raison duquel l’éditeur WYSIWYG effectue un rendu du contenu différent. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 est installé. L’ID de correctif est ACSD-48771. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’éditeur WYSIWYG effectue un rendu différent du contenu.

<u>Étapes à reproduire</u> :

1. Accédez à l’administrateur Adobe Commerce, créez une page avec une ligne de trois colonnes, puis enregistrez la page.
1. Mettez Adobe Commerce à jour vers l’une des dernières versions.
1. Définissez le navigateur [!DNL Chrome] pour désactiver le cache et accélérer sur *Fast 3G*.
1. Accédez à nouveau à la page d’édition et actualisez-la jusqu’à ce que les colonnes deviennent des lignes.
1. Enregistrez la page lorsque les colonnes se trouvent dans des lignes.

<u>Résultats attendus</u> :

Le créateur de pages d’administration ne doit pas afficher les colonnes dans les lignes.

<u>Résultats réels</u> :

Les colonnes apparaissent dans différentes lignes.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
