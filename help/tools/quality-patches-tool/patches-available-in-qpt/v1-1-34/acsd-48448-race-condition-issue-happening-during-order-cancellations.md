---
title: 'ACSD-48448 : problème de condition de race lors des annulations de commande, provoquant une entrée dupliquée dans la table inventory_reservation'
description: Appliquez le correctif ACSD-48448 pour résoudre le problème de performances d’Adobe Commerce en raison duquel le problème de condition de concurrence se produit lors des annulations de commande, ce qui entraîne des entrées dupliquées dans la table inventory_reserve.
feature: Orders, Checkout
role: Admin
source-git-commit: 809defe75d7b218d8085f85ff815472a531040cf
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-48448 : *[!UICONTROL Race]* problème de condition lors des annulations de commande provoquant une entrée dupliquée dans la table `inventory_reservation`

Le correctif ACSD-48448 corrige le problème de condition *[!UICONTROL Race]* survenant lors des annulations de commande, ce qui entraîne des entrées dupliquées dans la table `inventory_reservation`. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.34 est installé. L’ID de correctif est ACSD-48448. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2 et 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un problème de condition *[!UICONTROL Race]* se produit lors des annulations de commande, ce qui entraîne la duplication des entrées dans la table `inventory_reservation`.

<u>Étapes à reproduire</u> :

1. passé une commande ;
1. Vérifiez la table `inventory_reservation` pour vous assurer qu’il existe un enregistrement pour l’événement `order_placed`.
1. Exécutez le script joint pour annuler la commande en parallèle (pensez à modifier l’URL et l’ID de commande).

`bash cancel_order.sh`

```
#!/bin/bash
baseUrl=" "
orderId=3
token=$(curl --location --request POST "${baseUrl}rest/V1/integration/admin/token" \
 -H 'Content-Type: application/json' \
 -d '{
  "username": "admin",
  "password": "password"
}')
echo ${token//\"/}
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
 &
sleep 0.1;
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
wait
```

<u>Résultats attendus</u> :

Les enregistrements ne sont pas dupliqués.

<u>Résultats réels</u> :

Les enregistrements en double sont créés dans la table `inventory_reservation` pour `order_canceled`.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool]
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide d’infrastructure Commerce on Cloud

## Lecture connexe

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
