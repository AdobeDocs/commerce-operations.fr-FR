---
title: 'ACSD-47004 : TVA non appliquée à l''adresse de facturation sans numéro de TVA'
description: Appliquez le correctif ACSD-47004 pour résoudre le problème d’Adobe Commerce en raison duquel la TVA n’est pas appliquée à une adresse de facturation sans numéro de TVA.
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
exl-id: 72a64937-1c04-4fc2-bc61-fd2056e24419
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 1%

---

# ACSD-47004 : TVA non appliquée à l&#39;adresse de facturation sans numéro de TVA

Le correctif ACSD-47004 corrige le problème où la TVA n’est pas appliquée à une adresse de facturation sans numéro de TVA. Ce correctif est disponible lorsque la version 1.1.24 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47004. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La TVA n&#39;est pas appliquée à une adresse de facturation sans numéro TVA.

<u>Procédure à suivre </u> :

1. Ouvrez [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]** et définissez le **[!UICONTROL Enable Automatic Assignment to Customer Group]** sur *[!UICONTROL Yes]*.
1. Définir différents groupes pour les validations des identifiants de TVA. Par exemple :

   ![VAT-ID-validations](/help/assets/tools/vat-id-validations.png)

1. Enregistrez un nouveau client.
1. Ajouter une nouvelle adresse par défaut sans TVA. Par exemple :

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. Vérifiez que le groupe du client reste [!UICONTROL General].
1. Modifiez cette adresse et ajoutez un numéro de TVA valide :

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. Assurez-vous que le groupe du client a été remplacé par [!UICONTROL Retailer].
1. Modifiez l&#39;adresse et supprimez le numéro de TVA :

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u>Résultats attendus</u> :

Le groupe de clients est automatiquement remplacé par le groupe de [!UICONTROL General] par défaut.

<u>Résultats réels</u> :

Le groupe de clients n’est pas automatiquement remplacé par le groupe de [!UICONTROL General] par défaut.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
