---
title: 'MDVA-31590 : impossible de mettre à jour les attributs en bloc à l’aide des files d’attente asynchrones MySQL'
description: Le correctif MDVA-31590 résout le problème où les utilisateurs ne peuvent pas mettre à jour les attributs en bloc à l’aide des files d’attente asynchrones MySQL. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID du correctif est MDVA-31590. Notez que le problème a été résolu dans Adobe Commerce 2.4.2.
feature: Attributes, Services
role: Admin
exl-id: f8d1c3bd-e995-41ef-89e1-93eec6e8b1f1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-31590 : impossible de mettre à jour les attributs en bloc à l’aide des files d’attente asynchrones MySQL

Le correctif MDVA-31590 résout le problème où les utilisateurs ne peuvent pas mettre à jour les attributs en bloc à l’aide des files d’attente asynchrones MySQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID du correctif est MDVA-31590. Notez que le problème a été résolu dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0-2.4.1-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne peuvent pas mettre à jour les attributs en bloc à l’aide de MySQL async.

<u>Procédure à suivre </u> :

1. Sur la grille de produits en arrière-plan, effectuez une action en masse pour mettre à jour les valeurs d’attribut de quelques produits.
   * Vérifiez les produits et sélectionnez **Mettre à jour les attributs** dans le menu déroulant Actions.
1. Définissez des valeurs pour les attributs requis, affectez des produits à des sites web et enregistrez.
1. Une fois la page rechargée, un message du type suivant s’affiche :
   *Tâche « Mettre à jour les attributs pour N produits sélectionnés » : 1 élément(s) ont été planifiés pour une mise à jour.*
1. Patientez quelques secondes et rechargez la page principale.

<u>Résultats attendus</u> :

1. La page affiche un message de mise à jour réussie tel que : *1 élément(s) ont été mis à jour avec succès.*
1. Les valeurs d’attribut des produits associés sont mises à jour.
1. Dans la base de données, les nouveaux enregistrements sont créés dans `magento_bulk` table et dans `magento_operation` table (opérations liées à l’ensemble).
1. De nouveaux enregistrements sont créés dans la table `queue_message` (liée aux files d’attente `product_action_attribute.update` et/ou `product_action_attribute.website.update`).
1. `queue_message_status` table contient des enregistrements avec le statut « 4 ».
1. Il n’y a AUCUNE erreur dans `system.log`.

<u>Résultats réels</u> :

1. La page affiche toujours un message du type :
   *Tâche « Mettre à jour les attributs pour N produits sélectionnés » : 1 élément(s) ont été planifiés pour une mise à jour.*
1. Les valeurs d’attribut des produits sont mises à jour.
1. Un nouvel enregistrement est créé dans `message_bulk` table, mais il n&#39;y a aucun enregistrement associé dans `magento_operation` table.
1. De nouveaux enregistrements sont créés dans les tables `queue_message` et `queue_message_status`.
1. `queue_message_status` table contient un enregistrement avec le statut d&#39;erreur (valeur de statut « 6 »).
1. `system.log` contient une erreur similaire à ce qui suit :

   ```sql
   *main.CRITICAL: Message has been rejected: SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'operation_key' cannot be null, query was: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?) [] []*
   ```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
