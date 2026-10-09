---
title: 'ACSD-63992 : erreur de condition de bon et de méthode d’expédition [!UICONTROL Cart Price Rule] avec l’interface utilisateur d’administration.'
description: Appliquez le correctif ACSD-63992 pour résoudre le problème d’Adobe Commerce en raison duquel le [!UICONTROL Cart Price Rule] avec un coupon et une condition basée sur une méthode d’expédition ne peuvent pas être correctement appliqués via l’interface utilisateur d’administration.
feature: Price Rules, Admin Workspace
role: Admin, Developer
exl-id: 80f407c7-4552-4cfb-96ae-43773d2ec398
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
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
source-wordcount: '389'
ht-degree: 0%
---
# ACSD-63992 : erreur de condition de bon et de méthode d’expédition [!UICONTROL Cart Price Rule] avec l’interface utilisateur d’administration.

Le correctif ACSD-63992 corrige le problème en raison duquel le [!UICONTROL Cart Price Rule] avec un coupon et une condition basée sur une méthode d’expédition ne peuvent pas être correctement appliqués via l’interface utilisateur d’administration. Ce correctif est disponible lorsque la version 1.1.60 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63992. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsqu’une règle de panier inclut une condition pour la méthode d’expédition dans la section **[!UICONTROL Conditions]** , le code de coupon associé ne s’applique pas lors de la création d’une commande via le panneau d’administration. À la place, le système affiche l’erreur suivante :

_Le code de coupon &lt;> n&#39;est pas valide. Vérifiez le code et réessayez._

<u>Procédure à suivre </u> :

1. Créez une règle de prix de panier et décrivez ses conditions :
   * Sous *[!UICONTROL Conditions]* : ajoutez une condition pour inclure le mode d’expédition (par exemple, *[!UICONTROL Flat Rate]*).
   * Sous *[!UICONTROL Rule Information]* : définissez **[!UICONTROL Coupon]** sur *[!UICONTROL Specific Coupon]*, puis saisissez **[!UICONTROL Coupon Code]** comme *TEST*.
1. Créez une nouvelle commande à partir du Panneau d’administration et saisissez le code de coupon *TEST* dans le champ **[!UICONTROL Apply Coupon]** .

<u>Résultats attendus</u> :

Le coupon a été appliqué.

<u>Résultats réels</u> :

Le message d’erreur suivant s’affiche :

```text
"The "TEST" coupon code isn't valid. Verify the code and try again."
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
