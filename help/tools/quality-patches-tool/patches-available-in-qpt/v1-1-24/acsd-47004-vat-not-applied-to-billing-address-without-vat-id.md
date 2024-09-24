---
title: "ACSD-47004 : TVA non appliquée à l'adresse de facturation sans identifiant de TVA"
description: Appliquez le correctif ACSD-47004 pour résoudre le problème Adobe Commerce où la TVA n’est pas appliquée à une adresse de facturation sans identifiant de TVA.
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 1%

---

# ACSD-47004 : TVA non appliquée à l&#39;adresse de facturation sans identifiant de TVA

Le correctif ACSD-47004 corrige le problème où la TVA n&#39;est pas appliquée à une adresse de facturation sans ID de TVA. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 est installé. L’ID de correctif est ACSD-47004. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La TVA n&#39;est pas appliquée à une adresse de facturation sans identifiant de TVA.

<u>Étapes à reproduire</u> :

1. Ouvrez le [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]** et définissez le **[!UICONTROL Enable Automatic Assignment to Customer Group]** sur *[!UICONTROL Yes]*.
1. Définissez différents groupes pour les validations d’ID de TVA. Par exemple :

   ![TVA-ID-validations](/help/assets/tools/vat-id-validations.png)

1. Enregistrez un nouveau client.
1. Ajoutez une nouvelle adresse par défaut sans TVA. Par exemple :

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. Vérifiez que le groupe du client reste [!UICONTROL General].
1. Editez cette adresse et ajoutez un numéro de TVA valide :

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. Assurez-vous que le groupe du client a été remplacé par [!UICONTROL Retailer].
1. Editez l&#39;adresse et supprimez le numéro de TVA :

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u>Résultats attendus</u> :

Le groupe de clients est automatiquement remplacé par le groupe [!UICONTROL General] par défaut.

<u>Résultats réels</u> :

Le groupe de clients n’est pas automatiquement remplacé par le groupe [!UICONTROL General] par défaut.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
