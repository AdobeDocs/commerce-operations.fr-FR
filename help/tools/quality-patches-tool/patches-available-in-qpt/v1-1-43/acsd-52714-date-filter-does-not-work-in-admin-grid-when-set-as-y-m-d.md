---
title: 'ACSD-52714 : le filtre de date ne fonctionne pas dans la grille d’administration lorsqu’il est défini sur y-m-d'
description: Appliquez le correctif ACSD-52714 pour résoudre le problème d’Adobe Commerce en raison duquel le filtre de date ne fonctionne pas dans la grille d’administration lorsque le format de date est défini sur y-m-d.
feature: Attributes
role: Admin, Developer
exl-id: 4a34900b-9566-41bb-8d3e-18a440117907
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-52714 : le filtre de date ne fonctionne pas dans la grille d’administration lorsqu’il est défini sur y-m-d

Le correctif ACSD-52714 corrige le problème en raison duquel le filtre de date ne fonctionne pas dans la grille d’administration lorsque le format de date est défini sur y-m-d. Ce correctif est disponible lorsque la version 1.1.43 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-52714. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le filtre de date ne fonctionne pas dans la grille d’administration lorsque le format de date est défini sur y-m-j.

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce propre.
1. Modifier
   `/app/code/Magento/Customer/view/adminhtml/ui_component/customer_listing.xml`
fichier et ajouter
   `<dateFormat>Y-MM-dd</dateFormat>`
vers
   `<column name="created_at" class="Magento\Ui\Component\Listing\Columns\Date" component="Magento_Ui/js/grid/columns/date" sortOrder="100">`
sous la balise .
   `<dataType>date</dataType>`

1. Videz le cache `bin/magento c:f`.
1. Connectez-vous à Admin et créez un nouveau client à partir de **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.

   * de : date actuelle moins 1 jour
   * a : date courante

1. Cliquez sur **[!UICONTROL Apply Filters]**.

<u>Résultats attendus</u> :

Le filtre de date de la grille fonctionne correctement, quel que soit le paramètre régional défini.

<u>Résultats réels</u> :

Le message suivant apparaît : *Aucun enregistrement trouvé*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
