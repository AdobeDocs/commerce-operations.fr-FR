---
title: 'ACSD-52714 : Le filtre de date ne fonctionne pas dans la grille d’administration lorsqu’il est défini sur y-m-d'
description: Appliquez le correctif ACSD-52714 pour résoudre le problème Adobe Commerce en raison duquel le filtre de date ne fonctionne pas dans la grille d’administration lorsque le format de date est défini sur y-m-d.
feature: Attributes
role: Admin, Developer
exl-id: 4a34900b-9566-41bb-8d3e-18a440117907
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-52714 : Le filtre de date ne fonctionne pas dans la grille d’administration lorsqu’il est défini sur y-m-d

Le correctif ACSD-52714 corrige le problème en raison duquel le filtre de date ne fonctionne pas dans la grille d’administration lorsque le format de date est défini sur y-m-d. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 est installé. L’ID de correctif est ACSD-52714. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le filtre de date ne fonctionne pas dans la grille admin lorsque le format de date est défini sur y-m-d.

<u>Étapes à reproduire</u> :

1. Installez Adobe Commerce propre.
1. Modifier
   `/app/code/Magento/Customer/view/adminhtml/ui_component/customer_listing.xml`
et ajoutez
   `<dateFormat>Y-MM-dd</dateFormat>`
to
   `<column name="created_at" class="Magento\Ui\Component\Listing\Columns\Date" component="Magento_Ui/js/grid/columns/date" sortOrder="100">`
sous la balise
   `<dataType>date</dataType>`

1. Videz le cache `bin/magento c:f`.
1. Connectez-vous à Admin et créez un client à partir de **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.

   * à partir de : date actuelle moins 1 jour
   * à : date courante

1. Cliquez sur **[!UICONTROL Apply Filters]**.

<u>Résultats attendus</u> :

Le filtre de date de la grille fonctionne correctement, quel que soit le paramètre régional défini.

<u>Résultats réels</u> :

Le message suivant apparaît : *Nous n&#39;avons trouvé aucun enregistrement*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
