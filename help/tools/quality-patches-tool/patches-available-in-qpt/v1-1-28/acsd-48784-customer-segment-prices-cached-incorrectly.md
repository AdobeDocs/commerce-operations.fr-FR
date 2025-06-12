---
title: 'ACSD-48784 : les prix du segment client ne sont pas correctement mis en cache entre les groupes de clients'
description: Appliquez le correctif ACSD-48784 pour résoudre le problème d’Adobe Commerce où les prix des segments clients sont incorrectement mis en cache entre les groupes de clients.
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
exl-id: a691c61c-fdba-4d6a-8314-095dfb0ba4a1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-48784 : les prix du segment client ne sont pas correctement mis en cache entre les groupes de clients

Le correctif ACSD-48784 corrige le problème de mise en cache incorrecte des prix des segments clients entre les groupes de clients. Ce correctif est disponible lorsque la version 1.1.28 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48784. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les prix du segment client ne sont pas correctement mis en cache entre les groupes de clients.

<u>Conditions préalables</u> :

Configurez [!DNL Varnish] ou [!DNL Fastly].

<u>Procédure à suivre </u> :

1. Activez la mise en cache de toutes les pages dans votre boutique.
1. Connectez-vous au site en tant qu’utilisateur avec des prix de groupe de clients spéciaux.
1. Accédez à la page d’un produit avec une tarification spéciale du groupe de clients. Observez le *prix spécial*.
1. Dans un navigateur distinct, ouvrez la même page de produit en tant qu’utilisateur invité sans vous connecter. Observez le prix normal.
1. Accédez à l’interface d’administration d’Adobe Commerce et effacez l’Adobe Commerce et le cache [!DNL Fastly] pour ce magasin.
1. Dans le navigateur connecté, supprimez le cookie `X-Magento-Vary`.
1. Dans le navigateur connecté, rechargez la même page de produit plusieurs fois jusqu’à ce que la mise en cache soit complètement vidée.
1. Dans le navigateur non connecté, rechargez la page produit pour afficher les prix du groupe de clients.

<u>Résultats attendus</u> :

La page Produit affiche le prix correct pour des groupes de clients spécifiques.

<u>Résultats réels</u> :

* Les utilisateurs invités voient le prix spécial de l&#39;utilisateur connecté.
* Le mini panier affiche le prix correct une fois que le produit y est ajouté.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
