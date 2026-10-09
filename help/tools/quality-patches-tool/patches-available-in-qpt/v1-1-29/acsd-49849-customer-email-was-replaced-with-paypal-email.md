---
title: 'ACSD-49849 : l''e-mail du client a été remplacé par l''e-mail PayPal'
description: Appliquez le correctif ACSD-49849 pour résoudre le problème d'Adobe Commerce où l'e-mail du client a été remplacé par un e-mail PayPal lors de la commande avec PayPal Express via GraphQL.
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 1d7a2bde-892a-4ded-a4b4-9450989c8aee
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%
---
# ACSD-49849 : l’e-mail du client est remplacé par [!DNL PayPal] e-mail

Le correctif ACSD-49849 corrige le problème de remplacement de l’e-mail d’un client par un e-mail [!DNL PayPal's] lors de la commande avec [!DNL PayPal Express] via GraphQL. Ce correctif est disponible lorsque la version 1.1.29 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-49849. Notez que le problème a été résolu dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’e-mail d’un client ou d’une cliente est remplacé par un e-mail [!DNL PayPal's] lors de la commande avec [!DNL PayPal Express] via GraphQL.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Activez et configurez [!DNL PayPal Express] et définissez **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et créez un produit simple.
1. Effectuez le passage en caisse des invités à l’aide de GraphQL. Pour plus d’informations, consultez le tutoriel de passage en caisse de [](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) dans la documentation pour les développeurs Adobe Commerce.
1. Utilisez [!DNL PayPal Express] comme mode de paiement.
1. Notez l’e-mail que vous avez utilisé à l’étape de [configuration de l’e-mail pour le panier](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) dans la documentation pour les développeurs d’Adobe Commerce.
1. Une fois la commande passée, accédez à l’administration Adobe Commerce et vérifiez l’e-mail dans la commande créée.

<u>Résultats attendus</u> :

L’adresse e-mail est la même que celle définie lors du passage en caisse.

<u>Résultats réels</u> :

L’adresse e-mail définie lors du passage en caisse est remplacée par celle définie dans le compte [!DNL PayPal].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
