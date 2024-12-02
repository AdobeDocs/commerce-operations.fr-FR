---
title: 'MDVA-42657 : impossible de sélectionner des catégories dans les conditions de segment du client'
description: Le correctif MDVA-42657 résout le problème où l’utilisateur administrateur ne peut pas sélectionner de catégories dans les conditions de segment du client. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID de correctif est MDVA-42657. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Categories, Console, Customer Service
role: Admin
exl-id: 115bad99-a603-4940-897e-034974ed1a6c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-42657 : impossible de sélectionner des catégories dans les conditions de segment du client

Le correctif MDVA-42657 résout le problème où l’utilisateur administrateur ne peut pas sélectionner de catégories dans les conditions de segment du client. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID de correctif est MDVA-42657. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur administrateur ne peut pas sélectionner de catégories dans les conditions de segment du client.

<u>Étapes à reproduire</u> :

1. Accédez à **Customers** > **Segments**.
1. Créez un segment.
1. Accédez au segment nouvellement créé et cliquez sur **Conditions** dans le volet de navigation de gauche.
1. Cliquez sur le signe plus vert.
1. Sélectionnez Historique des produits sous Produits.
1. Remplacez &quot;consulté&quot; par &quot;ordonné&quot;.
1. Remplacez &quot;ALL&quot; par &quot;ANY&quot; (N’IMPORTE QUEL).
1. Cliquez sur le signe plus vert imbriqué et sélectionnez Catégorie.
1. Cliquez sur le signe **...** , puis sur l’icône de sélection (à gauche de la coche).
1. Ouvrez la console de développement du navigateur.
1. Cochez les cases correspondant à une ou plusieurs catégories et notez l’erreur JavaScript générée dans la console.
1. Cliquez sur le bouton **Enregistrer** .
1. Revenez à la condition et vérifiez si les catégories sélectionnées sont enregistrées.

<u>Résultats attendus</u> :

Les catégories sélectionnées sont enregistrées et sélectionnées lors de l’affichage/de la modification des conditions de segment.

<u>Résultats réels</u> :

Les catégories sélectionnées sont manquantes et n’ont pas été enregistrées correctement. Vous obtenez l’erreur suivante dans la console :

```
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
