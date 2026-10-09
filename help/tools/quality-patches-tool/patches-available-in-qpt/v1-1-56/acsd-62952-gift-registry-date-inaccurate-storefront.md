---
title: 'ACSD-62952 : La date d''enregistrement du cadeau ne s''affiche pas correctement sur le storefront'
description: Appliquez le correctif ACSD-62952 pour résoudre le problème d'Adobe Commerce où la date d'enregistrement du cadeau est affichée de manière incorrecte sur le storefront.
feature: Gift, Storefront
role: Admin, Developer
exl-id: c11e95ab-775d-4aa7-828b-29ec52685d47
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
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
source-wordcount: '338'
ht-degree: 0%
---
# ACSD-62952 : La date d&#39;enregistrement du cadeau ne s&#39;affiche pas correctement sur le storefront

Le correctif ACSD-62952 corrige le problème d&#39;affichage inexact de la date d&#39;enregistrement des cadeaux sur le storefront. Ce correctif est disponible lorsque la version 1.1.56 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62952. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La date de l&#39;événement affichée sur le storefront pour un registre des cadeaux partagé s&#39;affiche incorrectement un jour plus tôt que la date réelle.

<u>Procédure à suivre </u> :

1. Connectez-vous au serveur frontal en tant que client.
1. Dans le tableau de bord de la [!UICONTROL My Account], cliquez sur **[!UICONTROL Gift Registry]**.
1. S’il n’existe aucun registre, créez-en un et indiquez une date.
1. Ajoutez n’importe quel article au panier.
1. Sur la page du panier, cliquez sur **[!UICONTROL Add all items to Gift Registry]**.
1. Partagez le registre des cadeaux.

<u>Résultats attendus</u> :

Le registre des cadeaux affiche la date correcte de l&#39;événement.

<u>Résultats réels</u> :

Le registre des cadeaux ouvert à partir de l’e-mail d’invitation affiche la date de l’événement un jour plus tôt.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : mises à niveau et correctifs > Appliquer des correctifs dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
