---
title: 'MDVA-43824 : l''action d''annulation de commande a échoué avec l''erreur « Vous n''avez pas annulé l''article »'
description: 'Le correctif MDVA-43824 résout le problème d''échec de l''action d''annulation de commande avec l''erreur : *Vous n''avez pas annulé l''article*. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-43824. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.'
feature: Orders
role: Admin
exl-id: 8c2d15a0-2f53-4583-bdf2-86746f61160f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-43824 : l&#39;action d&#39;annulation de commande a échoué avec l&#39;erreur « Vous n&#39;avez pas annulé l&#39;article »

Le correctif MDVA-43824 résout le problème où l&#39;action d&#39;annulation de commande a échoué avec l&#39;erreur : *Vous n&#39;avez pas annulé l&#39;article*. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-43824. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.6 - 2.3.7-p3, 2.4.1 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La commande passée par un client connecté ne peut pas être annulée. L&#39;action d&#39;annulation de la commande a échoué avec l&#39;erreur suivante :

```
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u>Procédure à suivre </u> :

1. Créez une règle de vente (le type de coupon est Coupon spécifique ou Aucun coupon).
1. Accédez à la vitrine , connectez-vous en tant que client et ajoutez un produit au panier.
1. Accédez au panier et appliquez la règle de prix de panier si la règle de prix de panier comporte un coupon en tant que « Coupon spécifique ». La règle de prix de panier doit être appliquée avec succès.
1. Allez à la caisse et passez la commande avec n&#39;importe quel mode de paiement.
1. Sélectionnez Commerce Admin > **Ventes** > **Commandes**.
1. Ouvrez la commande passée à l’étape 4.
1. Cliquez sur le bouton **Annuler**.

<u>Résultats attendus</u> :

La commande est annulée sans erreur.

<u>Résultats réels</u> :

L&#39;action d&#39;annulation de la commande a échoué avec l&#39;erreur suivante : *Vous n&#39;avez pas annulé l&#39;article.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
