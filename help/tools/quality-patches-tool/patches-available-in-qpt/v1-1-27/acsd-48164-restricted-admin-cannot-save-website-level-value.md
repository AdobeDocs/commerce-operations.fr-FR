---
title: 'ACSD-48164 : l’administrateur restreint ne peut pas enregistrer la valeur au niveau du site web'
description: Appliquez le correctif ACSD-48164 pour résoudre le problème d’Adobe Commerce en raison duquel un administrateur restreint ne peut pas enregistrer de valeur au niveau du site web.
feature: Admin Workspace
role: Admin
exl-id: 1ad4758e-7ecc-48d0-8313-1163188cbe73
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48164 : l’administrateur restreint ne peut pas enregistrer la valeur au niveau du site web

Le correctif ACSD-48164 corrige le problème en raison duquel un administrateur restreint ne peut pas enregistrer de valeur au niveau du site web. Ce correctif est disponible lorsque la version 1.1.27 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48164. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’administrateur restreint ne peut pas enregistrer une valeur au niveau du site web.

<u>Procédure à suivre </u> :

1. Créez un site web, un magasin et une vue de magasin dans [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**.
1. Créez un rôle d’administrateur dans [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**.

   * Accédez à **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**, sélectionnez le nouveau site web et attribuez ce rôle à n’importe quel utilisateur administrateur.

1. Sélectionnez un produit et affectez uniquement le nouveau site web. Ne sélectionnez pas le site web par défaut.
1. Connectez-vous en tant qu’utilisateur administrateur affecté à l’étape 2 et modifiez le produit sous **[!UICONTROL All Store View]** portée en modifiant n’importe quel attribut au niveau du site web tel que *[!UICONTROL Status]*, *[!UICONTROL Tax Class]*, puis définissez le produit comme nouveau.
1. Enregistrez le produit.

<u>Résultats attendus</u> :

L’utilisateur administrateur associé à l’étendue du rôle sur un site web peut enregistrer les attributs de produit au niveau du site web à l’aide de l’étendue du *[!UICONTROL All Store View]*.

<u>Résultats réels</u> :

Le message de réussite indiquant que le produit a été enregistré s’affiche, mais les valeurs des attributs de produit restent inchangées.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
