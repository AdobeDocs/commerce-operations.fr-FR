---
title: '''ACSD-47669 : Erreur interne du serveur lors de l''import de produits avec des options personnalisables'''
description: Appliquez le correctif ACSD-47669 pour résoudre le problème Adobe Commerce en raison duquel une erreur de serveur interne se produit lors de l’importation de produits avec des options personnalisables.
feature: Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47669 : Erreur interne du serveur lors de l&#39;import de produits avec des options personnalisables

Le correctif ACSD-47669 corrige le problème en raison duquel une erreur de serveur interne se produisait lors des importations de produits avec des options personnalisables. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.38 est installé. L’ID de correctif est ACSD-47669. Veuillez noter que le problème a déjà été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur de serveur interne s’est produite lors de l’import de produits avec des options personnalisables.

<u>Étapes à reproduire</u> :

1. Créez une vue de magasin supplémentaire. Assurez-vous que vous avez 2 vues de magasin, par exemple en, Royaume-Uni.
1. Créez deux produits simples, par exemple prod1 et prod2.
1. Préparez un fichier csv qui ajoute des options personnalisées pour les deux produits dans chaque vue de magasin et pour la portée **Toutes les vues de magasin**. Importez ce fichier csv.
1. Préparez un autre fichier csv contenant deux enregistrements. Le premier enregistrement doit être de mettre à jour les options personnalisées de &quot;prod1&quot; spécifiquement pour la portée de la vue de magasin britannique, et le second enregistrement doit être de mettre à jour les options personnalisées de &quot;prod2&quot; pour la portée **All Store View**. Importez ce second fichier csv.

<u>Résultats attendus</u> :

Vous devriez être en mesure de personnaliser les options sans erreur.

<u>Résultats réels</u> :

Une erreur de violation de contrainte d’intégrité se produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
