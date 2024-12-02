---
title: 'ACSD-59930 : améliore les performances des flux de l’entreprise'
description: Appliquez le correctif ACSD-5930 pour résoudre le problème Adobe Commerce où une erreur *Timeout* s’affiche dans le panneau d’administration lors de la création, de l’enregistrement ou de la suppression d’une société avec un administrateur dont les adresses sont *1000+* dans le carnet d’adresses.
feature: Customers, B2B
role: Admin, Developer
exl-id: eaa6c78d-13e3-439d-90f7-70c1c96c3197
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59930 : améliore les performances des flux de l’entreprise

Le correctif ACSD-59930 corrige le problème en raison duquel une erreur *Timeout* s’affichait dans le panneau d’administration lors de la création, de l’enregistrement ou de la suppression d’une société avec un administrateur dont les adresses *1000+* dans le carnet d’adresses. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.53 est installé. L’ID de correctif est ACSD-59930. Veuillez noter que ce problème doit être corrigé dans Adobe Commerce B2B-1.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Améliore les performances des flux de création, d’enregistrement et de suppression de l’entreprise.

<u>Conditions préalables :</u> :

Installez et activez les modules Adobe Commerce B2B.

<u>Étapes à reproduire</u> :

1. Créez un client avec des adresses *1000+* dans le *[!UICONTROL Address Book]*.
1. Créez une société et utilisez le client ci-dessus comme administrateur.
1. Enregistrez la société.

<u>Résultats attendus</u> :

L’entreprise est créée avec succès sans afficher d’erreurs de délai d’expiration.

<u>Résultats réels</u> :

Une erreur de délai d’expiration s’affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
