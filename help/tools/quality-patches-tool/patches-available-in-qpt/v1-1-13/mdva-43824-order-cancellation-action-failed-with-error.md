---
title: '''MDVA-43824 : l’action d’annulation de commande a échoué avec l’erreur "Vous n’avez pas annulé l’article"'
description: '''Le correctif MDVA-43824 résout le problème où l’action d’annulation de commande échouait avec l’erreur : *Vous n’avez pas annulé l’élément*. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID de correctif est MDVA-43824. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5."'
feature: Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-43824 : l’action d’annulation de commande a échoué avec l’erreur &quot;Vous n’avez pas annulé l’article&quot;

Le correctif MDVA-43824 résout le problème où l’action d’annulation de commande échouait avec l’erreur : *Vous n’avez pas annulé l’élément*. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID de correctif est MDVA-43824. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.6 - 2.3.7-p3, 2.4.1 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La commande passée par un client connecté ne peut pas être annulée. L’action d’annulation de commande a échoué avec l’erreur suivante :

```
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u>Étapes à reproduire</u> :

1. Créez une règle de vente (le type de coupon est &quot;coupon spécifique&quot; ou &quot;Aucun bon&quot;).
1. Accédez au storefront et connectez-vous en tant que client et ajoutez un produit au panier.
1. Accédez au panier et appliquez la règle de prix du panier si la règle de prix du panier comporte un coupon &quot;coupon spécifique&quot;. La règle de prix du panier doit être appliquée avec succès.
1. Allez à la caisse et passez la commande avec n&#39;importe quel mode de paiement.
1. Accédez à l’administrateur Commerce > **Ventes** > **Commandes**.
1. Ouvrez la commande passée à l’étape 4.
1. Cliquez sur le bouton **Annuler** .

<u>Résultats attendus</u> :

La commande est annulée sans erreur.

<u>Résultats réels</u> :

L&#39;action d&#39;annulation de la commande a échoué avec l&#39;erreur suivante : *Vous n&#39;avez pas annulé l&#39;article.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
