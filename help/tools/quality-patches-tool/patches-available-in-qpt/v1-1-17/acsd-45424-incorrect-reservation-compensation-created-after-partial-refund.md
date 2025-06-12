---
title: 'ACSD-45424 : compensation de réservation incorrecte créée après un remboursement partiel'
description: Le correctif ACSD-45424 corrige le problème où une compensation de réservation incorrecte est créée après un remboursement partiel. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID du correctif est ACSD-45424. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.
feature: Orders
role: Admin
exl-id: 94435816-9f4a-40f9-be80-05836ed7781f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# ACSD-45424 : compensation de réservation incorrecte créée après un remboursement partiel

Le correctif ACSD-45424 corrige le problème où une compensation de réservation incorrecte est créée après un remboursement partiel. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID du correctif est ACSD-45424. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une compensation de réservation incorrecte est créée après un remboursement partiel.

<u>Procédure à suivre </u> :

1. Activez le mode d’expédition de livraison en magasin.
1. Créez trois sources d&#39;inventaire et assurez-vous que le lieu de prélèvement est actif dans chacune d&#39;elles (source1, source2, source3).
1. Créez un nouveau stock et affectez les trois sources au nouveau stock.
   * Ce stock doit être affecté au site web principal.
1. Créez un produit simple, P3, et attribuez-lui toutes les sources.
1. Ajoutez les quantités suivantes pour les origines du produit simple et activez les reliquats :
   * Source par défaut : 100
   * source1 - 0
   * source2 - 10
   * source3 - 0
1. Ajoutez le produit simple au panier à partir du serveur frontal et passez au formulaire d’expédition.
1. Sélectionnez « source1 » comme emplacement d’expédition.
1. Complétez la commande et exécutez la requête suivante dans la base de données :

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   L&#39;enregistrement de la commande passée s&#39;affichera dans la table `inventory_reservation`. La quantité est 10, ce qui est correct.
1. Facturez cette commande à partir du serveur principal.
1. Créez maintenant un avoir pour un seul produit. NE cochez PAS la case *Retour aux stocks*.
1. Exécutez la même requête à partir de l’étape 8.

<u>Résultats attendus</u> :

Si vous n&#39;avez pas sélectionné l&#39;option *Retour aux stocks* lors de la création de l&#39;avoir, la table `inventory_reservation` ne contiendra aucun enregistrement correspondant à l&#39;avoir.

<u>Résultats réels</u> :

Bien que vous n&#39;ayez pas sélectionné le *Retour aux stocks* lors de la création de l&#39;avoir, il ajoute un enregistrement à `inventory_reservation` table avec `creditmemo_created` type d&#39;événement. En outre, la quantité de l&#39;enregistrement d&#39;avoir ajouté dans la table `inventory_reservation` est de 10, même si vous n&#39;avez créé l&#39;avoir que pour une seule quantité.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
