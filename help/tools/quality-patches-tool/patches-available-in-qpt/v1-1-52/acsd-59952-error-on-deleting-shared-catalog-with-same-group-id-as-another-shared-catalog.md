---
title: "ACSD-59952 : erreur lors de la suppression d’un catalogue partagé avec le même ID de groupe qu’un autre catalogue partagé"
description: Appliquez le correctif ACSD-59952 pour résoudre le problème Adobe Commerce en raison duquel une erreur est générée lors de la suppression d’un catalogue partagé avec le même `customer_group_id` qu’un autre catalogue partagé.
feature: B2B, REST
role: Admin, Developer
source-git-commit: a67f31aa905b420dcd2a17645734632d3f94520c
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# ACSD-59952 : erreur lors de la suppression d’un catalogue partagé avec le même ID de groupe qu’un autre catalogue partagé

Le correctif ACSD-59952 corrige l’erreur générée lors de la suppression de catalogues partagés avec le même `customer_group_id` qu’un autre catalogue partagé. Elle empêche en outre les utilisateurs de créer de tels catalogues partagés. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 est installé. L’ID de correctif est ACSD-59952. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un nouveau catalogue partagé avec le même `customer_group_id` qu’un autre catalogue partagé ne peut pas être créé. Cependant, si vous tentez de supprimer le catalogue partagé avec le même `customer_group_id`, une erreur s’affiche.

<u>Conditions préalables</u> :

Installez les modules Adobe Commerce B2B.

<u>Étapes à reproduire</u> :

1. Créez plusieurs catalogues partagés affectés au même `customer_group_id` à l&#39;aide de l&#39;appel API REST suivant :

   ```REST
   {
       "sharedCatalog": {
           "name": "test1",
           "description": "test",
           "customer_group_id": 1,
           "type": 0,
           "created_at": "03:11:00",
           "created_by": 1,
           "store_id": 0,
           "tax_class_id": 3
       }
   }
   ```

1. Essayez de supprimer l’un des catalogues partagés à l’aide de l’appel de l’API REST suivant :

   ```REST
   /rest/default/V1/sharedCatalog/4
   ```

<u>Résultats attendus</u> :

* La création de plusieurs catalogues partagés affectés au même `customer_group_id` n&#39;est pas possible.
* Le catalogue partagé dans le cas ci-dessus est supprimé avec succès.

<u>Résultats réels</u> :

* Il est possible de créer plusieurs catalogues partagés affectés au même `customer_group_id`.
* L’erreur suivante est renvoyée lors de la tentative de suppression du catalogue partagé avec le même `customer_group_id` : *Impossible de supprimer le catalogue partagé*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
