---
title: 'MDVA-31590 : impossible de mettre à jour les attributs en masse à l’aide des files d’attente asynchrones MySQL'
description: Le correctif MDVA-31590 résout le problème où les utilisateurs ne peuvent pas mettre à jour les attributs en masse à l’aide des files d’attente asynchrones MySQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID de correctif est MDVA-31590. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
feature: Attributes, Services
role: Admin
exl-id: f8d1c3bd-e995-41ef-89e1-93eec6e8b1f1
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-31590 : impossible de mettre à jour les attributs en masse à l’aide des files d’attente asynchrones MySQL

Le correctif MDVA-31590 résout le problème où les utilisateurs ne peuvent pas mettre à jour les attributs en masse à l’aide des files d’attente asynchrones MySQL. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID de correctif est MDVA-31590. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0-2.4.1-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne peuvent pas mettre à jour les attributs en masse à l’aide de MySQL async.

<u>Étapes à reproduire</u> :

1. Sur la grille de produit du serveur principal, effectuez une action de masse pour mettre à jour les valeurs d’attribut de quelques produits.
   * Vérifiez les produits et sélectionnez **Mettre à jour les attributs** dans la liste déroulante Actions.
1. Définissez des valeurs pour les attributs requis, affectez des produits aux sites web et enregistrez.
1. Une fois la page rechargée, un message similaire à celui-ci s’affiche :
   *Tâche &quot;Mise à jour des attributs pour N produits sélectionnés&quot; : 1 élément(s) a été planifié pour une mise à jour.*
1. Patientez quelques secondes et rechargez la page principale.

<u>Résultats attendus</u> :

1. La page affiche un message de mise à jour réussi, tel que : *1 élément(s) ont été mis à jour avec succès.*
1. Les valeurs d’attribut pour les produits associés sont mises à jour.
1. Dans DB, de nouveaux enregistrements sont créés dans la table `magento_bulk` et la table `magento_operation` (opérations liées au volume).
1. De nouveaux enregistrements sont créés dans la table `queue_message` (liés aux files d&#39;attente `product_action_attribute.update` et/ou `product_action_attribute.website.update`).
1. La table `queue_message_status` contient des enregistrements avec le statut &quot;4&quot;.
1. Il n’y a AUCUNE erreur dans `system.log`.

<u>Résultats réels</u> :

1. La page affiche toujours un message du type :
   *Tâche &quot;Mise à jour des attributs pour N produits sélectionnés&quot; : 1 élément(s) a été planifié pour une mise à jour.*
1. Les valeurs d’attribut des produits sont mises à jour.
1. Un nouvel enregistrement est créé dans la table `message_bulk`, mais aucun enregistrement associé n’est présent dans la table `magento_operation`.
1. De nouveaux enregistrements sont créés dans les tables `queue_message` et `queue_message_status`.
1. La table `queue_message_status` a un enregistrement avec un état d’erreur (valeur de statut &quot;6&quot;).
1. `system.log` contient une erreur similaire à celle-ci :

   ```sql
   *main.CRITICAL: Message has been rejected: SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'operation_key' cannot be null, query was: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?) [] []*
   ```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
