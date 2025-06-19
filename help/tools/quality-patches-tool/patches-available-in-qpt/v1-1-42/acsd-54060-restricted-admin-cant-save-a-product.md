---
title: 'ACSD-54060 : l''administrateur restreint ne peut pas enregistrer le produit s''il est l''enfant d''un autre produit'
description: Appliquez le correctif ACSD-54060 pour résoudre le problème d’Adobe Commerce en raison duquel un administrateur restreint ne peut pas enregistrer un produit s’il est l’enfant d’un autre produit affecté à une portée différente.
feature: Admin Workspace, Roles/Permissions, Products
role: Admin, Developer
exl-id: 2af24cbf-65a1-4bd6-aad3-19b613bee7f2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-54060 : l&#39;administrateur restreint ne peut pas enregistrer le produit s&#39;il est l&#39;enfant d&#39;un autre produit

Le correctif ACSD-54060 corrige le problème en raison duquel un administrateur restreint ne peut pas enregistrer un produit s’il est l’enfant d’un autre produit affecté à une portée différente. Ce correctif est disponible lorsque la version 1.1.42 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54060. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un administrateur restreint ne peut pas enregistrer un produit s&#39;il est l&#39;enfant d&#39;un autre produit affecté à une portée différente.

<u>Procédure à suivre </u> :

1. Créez un site web supplémentaire.
1. Créez un produit simple et affectez-le aux deux sites web.
1. Créez un produit configurable avec le produit simple comme seule variation et affectez le produit configurable au site web par défaut uniquement.
1. Créez un utilisateur administrateur restreint ayant uniquement accès au deuxième site web.
1. Connectez-vous en tant qu’utilisateur administrateur restreint.
1. Essayez de modifier le nom de produit simple dans la portée du second site web.

<u>Résultats attendus</u> :

L’administrateur restreint peut modifier le nom du produit.

<u>Résultats réels</u> :

Une erreur se produit : *Des autorisations supplémentaires sont nécessaires pour afficher cet élément*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
