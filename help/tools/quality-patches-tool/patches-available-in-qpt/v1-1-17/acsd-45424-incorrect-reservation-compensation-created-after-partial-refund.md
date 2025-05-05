---
title: "ACSD-45424 : Incorrection de la compensation de réservation créée après un remboursement partiel"
description: Le correctif ACSD-45424 corrige le problème où une compensation de réservation incorrecte est créée après un remboursement partiel. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID de correctif est ACSD-45424. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
feature: Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# ACSD-45424 : compensation de réservation incorrecte créée après un remboursement partiel

Le correctif ACSD-45424 corrige le problème où une compensation de réservation incorrecte est créée après un remboursement partiel. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID de correctif est ACSD-45424. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une compensation de réservation incorrecte est créée après un remboursement partiel.

<u>Étapes à reproduire</u> :

1. Activez le mode de livraison en magasin.
1. Créez trois sources d’inventaire et assurez-vous que l’emplacement de récupération est actif dans chacune d’elles (source1, source2, source3).
1. Créez un nouveau stock et affectez les trois sources au nouveau stock.
   * Ce stock doit être affecté au site web principal.
1. Créez un produit simple, P3, et affectez-lui toutes les sources.
1. Ajoutez les quantités suivantes pour les sources du produit simple et activez les commandes en arrière-plan :
   * Source par défaut - 100
   * source1 - 0
   * source2 - 10
   * source3 - 0
1. Ajoutez le produit simple au panier à partir de l’interface frontale et passez au formulaire d’expédition.
1. Sélectionnez &quot;source1&quot; comme emplacement d’expédition.
1. Exécutez la requête suivante dans la base de données :

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   Vous obtiendrez l’enregistrement de la commande dans la table `inventory_reservation`. La quantité est 10, ce qui est correct.
1. Facturez cette commande à partir du serveur principal.
1. Créez maintenant une note de crédit pour un seul produit. NE cochez PAS la case *Revenir à Stock* .
1. Exécutez la même requête à partir de l’étape 8.

<u>Résultats attendus</u> :

Si vous n’avez pas sélectionné *Revenir à Stock* au cours de la création de l’avoir, la table `inventory_reservation` n’aura pas d’enregistrement correspondant à l’avoir.

<u>Résultats réels</u> :

Même si vous n’avez pas sélectionné *Revenir au stock* lors de la création de l’avoir, un enregistrement est ajouté à la table `inventory_reservation` avec le type d’événement `creditmemo_created`. En outre, l’enregistrement de note de crédit ajouté à la table `inventory_reservation` a une quantité de 10, même si vous avez créé l’avoir de crédit pour une seule quantité.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
