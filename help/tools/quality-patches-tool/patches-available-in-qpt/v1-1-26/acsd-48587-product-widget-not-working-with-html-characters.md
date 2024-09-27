---
title: "ACSD-48587 : le widget de produit ne fonctionne pas avec les SKU contenant des caractères d’HTML"
description: Appliquez le correctif ACSD-48587 pour résoudre le problème Adobe Commerce en raison duquel les caractères spéciaux HTMLS dans les règles de correspondance du widget de produits les empêchent d’afficher les produits correspondants.
feature: Admin Workspace, CMS, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48587 : le widget de produit ne fonctionne pas avec les SKU contenant des caractères d’HTML.

Le correctif ACSD-48587 corrige le problème en raison duquel les caractères spéciaux HTMLS dans les règles de correspondance du widget de produits les empêchaient d’afficher les produits correspondants. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 est installé. L’ID de correctif est ACSD-48587. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le widget de produit ne fonctionne pas avec les SKU contenant les symboles *&quot;&amp;&quot;*.

<u>Étapes à reproduire</u> :

1. Créez un produit contenant *&quot;&amp;&quot;* dans le SKU (par exemple, s000&amp;01).
1. Modifiez le contenu d’une page CMS sur le *Créateur de pages*.
1. Ajoutez un widget de produits.
1. Modifiez le widget et définissez **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**.
1. Saisissez le SKU qui contient *&quot;&amp;&quot;* dans le champ des SKU du produit.
1. Enregistrez le contenu et la page CMS.
1. Vérifiez le contenu de la *page CMS* pour l’ *aperçu du générateur de page* et le storefront de produit.

<u>Résultats attendus</u> :

Le produit avec *&quot;&amp;&quot;* dans le SKU s’affiche dans l’aperçu du créateur de pages et sur le storefront.

<u>Résultats réels</u> :

Le produit avec *&quot;&amp;&quot;* dans le SKU ne s’affiche pas dans l’aperçu du créateur de pages.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
