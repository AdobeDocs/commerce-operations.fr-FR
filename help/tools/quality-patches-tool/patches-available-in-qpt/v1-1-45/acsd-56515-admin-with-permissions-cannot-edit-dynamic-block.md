---
title: 'ACSD-56515 : l’administrateur disposant d’autorisations au niveau du site web ne peut pas modifier les [!UICONTROL Dynamic Block]'
description: Appliquez le correctif ACSD-56515 pour résoudre le problème d’Adobe Commerce en raison duquel l’administrateur disposant d’autorisations au niveau du site web ne peut pas ajouter ni modifier le [!UICONTROL Dynamic Block].
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: dd3e61a4-aba4-4f86-b4fe-88ca4276ace5
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e439352c-5b67-587d-b34e-d2a0aa5a0242
    internal-label: Roles/Permissions
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '384'
ht-degree: 0%
---
# ACSD-56515 : l’administrateur disposant d’autorisations au niveau du site web ne peut pas modifier les [!UICONTROL Dynamic Block]

Le correctif ACSD-56515 corrige le problème en raison duquel l’administrateur disposant d’autorisations au niveau du site web ne peut pas ajouter ni modifier le [!UICONTROL Dynamic Block]. Ce correctif est disponible lorsque la version 1.1.45 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-56515. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’administrateur disposant d’autorisations au niveau du site web ne peut pas ajouter ni modifier le [!UICONTROL Dynamic Block].

<u>Procédure à suivre </u> :

1. Créez un site web secondaire avec un magasin et une révision.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]** et créez un rôle d’utilisateur limité à la portée du site web secondaire avec toutes les ressources disponibles.
1. Créez un utilisateur administrateur avec le rôle créé ci-dessus.
1. Connectez-vous avec l’utilisateur administrateur restreint et créez un [!UICONTROL Dynamic Block].

<u>Résultats attendus</u> :

L’utilisateur administrateur disposant de restrictions sur le site web peut créer une [!UICONTROL Dynamic Block].

<u>Résultats réels</u> :

Vous obtenez l’erreur suivante : *Des autorisations supplémentaires sont nécessaires pour afficher cet élément*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
