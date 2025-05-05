---
title: 'MDVA-37984 : le marchandisage visuel ne fonctionne pas correctement lors de l’application de mises à jour intermédiaires.'
description: Le correctif MDVA-37984 résout le problème en raison duquel la fonctionnalité "Faire correspondre le produit par règle" du marchandiseur visuel ne filtre pas correctement les produits lors de l’application de mises à jour intermédiaires. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID de correctif est MDVA-37984. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Categories, Merchandising, Products, Staging
role: Admin
exl-id: 3aeb74a4-b6f7-453a-a8f6-45a345aaa74f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-37984 : le marchandisage visuel ne fonctionne pas correctement lors de l’application de mises à jour intermédiaires.

Le correctif MDVA-37984 résout le problème en raison duquel la fonctionnalité &quot;Faire correspondre le produit par règle&quot; du marchandiseur visuel ne filtre pas correctement les produits lors de l’application de mises à jour intermédiaires. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID de correctif est MDVA-37984. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La fonctionnalité &quot;Match product by rule&quot; du marchandiseur visuel ne filtre pas correctement les produits lorsque des mises à jour intermédiaires sont appliquées.

<u>Étapes à reproduire</u> :

1. Créez une mise à jour de planification pour tout produit existant.
   * Définissez différentes valeurs pour `entity_id` et `row_id`.
1. Créez un produit configurable, puis un produit simple (les nouveaux produits `entity_id` et `row_ids` sont donc également différents).
   * Pour faciliter la réplication du problème, définissez une valeur de quantité reconnaissable pour le produit simple, par exemple 5000.
1. Accédez à une catégorie > **Produits de la catégorie** et activez l’option **Faire correspondre les produits par règle**.
1. Sélectionnez maintenant &quot;Quantité&quot; comme attribut, &quot;Supérieur&quot; comme opérateur et &quot;4500&quot; comme valeur.
1. Cliquez sur **save**.

<u>Résultats attendus</u> :

Le produit configurable nouvellement créé est répertorié.

<u>Résultats réels</u> :

Le produit configurable nouvellement créé n’est pas répertorié.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
