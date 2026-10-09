---
title: 'ACSD-54018 : problème de performances avec la liste de produits du widget de catalogue'
description: Appliquez le correctif ACSD-54018 pour résoudre le problème d’Adobe Commerce en raison duquel la page se charge lentement lors de l’ajout d’une liste de produits de widgets de catalogue avec une condition et un type d’attribut booléen.
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 2fb7ca37-78cc-45f4-86a3-d922cf4d1457
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
subfeature_v2:
  - id: ed510963-0b8c-4764-86f6-f3c7735bc334
    internal-label: Page Builder
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%
---
# ACSD-54018 : problème de performances avec la liste de produits du widget de catalogue

Le correctif ACSD-54018 corrige le problème en raison duquel la page se charge lentement lors de l’ajout d’une liste de produits de widgets de catalogue avec une condition et un type d’attribut booléen. Ce correctif est disponible lorsque la version 1.1.38 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-54018. Notez que le problème a été résolu dans Adobe Commerce 2.4.6.

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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
