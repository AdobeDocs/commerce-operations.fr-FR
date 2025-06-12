---
title: 'ACSD-54018 : problème de performances avec la liste de produits du widget de catalogue'
description: Appliquez le correctif ACSD-54018 pour résoudre le problème d’Adobe Commerce en raison duquel la page se charge lentement lors de l’ajout d’une liste de produits de widgets de catalogue avec une condition et un type d’attribut booléen.
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 2fb7ca37-78cc-45f4-86a3-d922cf4d1457
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-54018 : problème de performances avec la liste de produits du widget de catalogue

Le correctif ACSD-54018 corrige le problème en raison duquel la page se charge lentement lors de l’ajout d’une liste de produits de widgets de catalogue avec une condition et un type d’attribut booléen. Ce correctif est disponible lorsque la version 1.1.38 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54018. Notez que le problème a été résolu dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La page se charge lentement lors de l’ajout d’une liste de produits de widgets de catalogue avec une condition et un type d’attribut booléen.

<u>Procédure à suivre </u> :

1. Générez 100 000 produits.
1. Créez un attribut bool avec l’étendue définie sur [!UICONTROL Store View].
1. Attribuez un attribut à tous les jeux d’attributs.
   * Attribuez la valeur d’attribut *Oui* à tous les produits.
1. Accédez maintenant à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et sélectionnez l’ensemble des 100 000 produits.
   * Choisissez **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**.
   * Définissez l’attribut bool sur *Oui* et enregistrez-le.
   * Si vous vous êtes déconnecté de cette étape, vérifiez les *Notes*.
1. Accédez à l’interface de ligne de commande et exécutez `php bin/magento queue:con:start product_action_attribute.update`.
   * Assurez-vous que les attributs de tous les produits sont mis à jour.
1. Accédez maintenant à **[!UICONTROL Content]** > **[!UICONTROL Pages]** et créez une page.
1. Ouvrez **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**.
1. Choisissez *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*.
1. Définissez le *[!UICONTROL Created attribute]* de condition sur *[!UICONTROL Yes]* et enregistrez-le.
1. Accédez au front-end et ouvrez la page créée.
1. Désactivez le cache de page complet et bloquez le cache HTML.
1. Vérifiez la vitesse de chargement de la page.
1. Rechargez la page plusieurs fois et calculez le temps de chargement moyen.

<u>Résultats attendus</u> :

La page se charge rapidement.

<u>Résultats réels</u> :

Le chargement de la page prend entre 5 et 10 secondes.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
