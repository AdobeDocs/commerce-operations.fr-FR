---
title: "ACSD-53998 : le bloc dynamique basé sur le segment client ne fonctionne pas correctement après déconnexion"
description: Appliquez le correctif ACSD-53998 pour résoudre le problème Adobe Commerce en raison duquel un bloc dynamique basé sur un segment de client ne fonctionne pas correctement après déconnexion d’un compte client.
feature: Customers, Page Builder, Personalization
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-53998 : le bloc dynamique basé sur le segment client ne fonctionne pas correctement après déconnexion.

Le correctif ACSD-53998 corrige le problème lorsqu’un bloc dynamique basé sur un segment de client ne fonctionne pas correctement après déconnexion d’un compte client. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.39 est installé. L’ID de correctif est ACSD-53998. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2 - 2.4.4-p6, 2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un bloc dynamique basé sur un segment de client ne fonctionne pas correctement après déconnexion d’un compte de client.

<u>Conditions préalables</u> :

Installez et activez les modules [!DNL Page Builder].

<u>Étapes à reproduire</u> :

1. Créez deux segments de clients sans conditions.
1. Créez deux blocs dynamiques pour chaque segment.
1. Créez un bloc incluant les deux blocs dynamiques [!DNL Page Builder] blocs dynamiques.
1. Créez un widget comprenant le bloc ci-dessus et rendez le bloc visible sous la section de pied de page de toutes les pages.
1. Effacez les caches.
1. Ouvrez la page d’accueil.
1. Connectez-vous en tant que client.
1. Déconnectez-vous.

<u>Résultats attendus</u> :

La bannière créée pour les clients connectés ne s’affiche pas pour les utilisateurs invités.

<u>Résultats réels</u> :

La bannière créée pour le segment client connecté s’affiche même après la déconnexion du compte client.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
