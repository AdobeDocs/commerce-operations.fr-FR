---
title: 'ACSD-53998 : le bloc dynamique basé sur le segment client ne fonctionne pas correctement après la déconnexion'
description: Appliquez le correctif ACSD-53998 pour résoudre le problème d’Adobe Commerce en raison duquel un bloc dynamique basé sur un segment client ne fonctionne pas correctement après s’être déconnecté d’un compte client.
feature: Customers, Page Builder, Personalization
role: Admin, Developer
exl-id: aa7001c7-bb35-4e5c-8ac9-3ed84b75d7cd
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
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
source-wordcount: '446'
ht-degree: 0%
---
# ACSD-53998 : le bloc dynamique basé sur le segment client ne fonctionne pas correctement après la déconnexion

Le correctif ACSD-53998 corrige le problème d’un bloc dynamique basé sur un segment client qui ne fonctionne pas correctement après s’être déconnecté d’un compte client. Ce correctif est disponible lorsque la version 1.1.39 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-53998. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2 - 2.4.4-p6, 2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un bloc dynamique basé sur un segment client ne fonctionne pas correctement après s’être déconnecté d’un compte client.

<u>Conditions préalables</u> :

Installation et activation des modules [!DNL Page Builder].

<u>Procédure à suivre </u> :

1. Créez deux segments clients sans condition.
1. Créez deux blocs dynamiques pour chaque segment.
1. Créez un bloc comprenant les deux blocs dynamiques comme blocs dynamiques [!DNL Page Builder].
1. Créez un widget contenant le bloc ci-dessus et rendez le bloc visible sous la section de pied de page de toutes les pages.
1. Effacez les caches.
1. Ouvrez la page d’accueil.
1. Connectez-vous en tant que client.
1. Déconnectez-vous.

<u>Résultats attendus</u> :

La bannière créée pour les clients connectés n’est pas affichée pour les utilisateurs invités.

<u>Résultats réels</u> :

La bannière créée pour le segment de clients et clientes connectés s’affiche même après s’être déconnecté du compte client.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
