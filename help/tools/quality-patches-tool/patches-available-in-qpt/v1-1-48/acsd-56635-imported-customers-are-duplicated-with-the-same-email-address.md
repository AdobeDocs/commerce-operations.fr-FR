---
title: 'ACSD-56635 : les clients importés sont dupliqués lorsque le partage de compte est défini sur  [!DNL Global]'
description: Appliquez le correctif ACSD-56635 pour résoudre le problème d’Adobe Commerce où le client importé est dupliqué avec la même adresse e-mail lorsque l’importation est utilisée avec un partage de compte défini sur  [!DNL Global].
feature: Customers, Attributes
role: Admin, Developer
exl-id: 73abec4a-03b0-45d4-bfc6-f3c6862e733c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-56635 : les clients importés sont dupliqués avec la même adresse électronique lorsque le partage de compte est défini sur [!DNL Global]

Le correctif ACSD-56635 corrige le problème de duplication du client importé avec la même adresse e-mail lorsque l’importation est utilisée avec le partage de compte défini sur [!DNL Global]. Ce correctif est disponible lorsque la version 1.1.48 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-56635. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les clients importés sont dupliqués avec la même adresse électronique lorsque le partage de compte est défini sur [!DNL Global].

<u>Procédure à suivre </u> :

1. Sous le **[!UICONTROL Admin]** Adobe Commerce (2.4-development b2b) , accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**.
1. Définissez le paramètre *[!UICONTROL Share Customer Accounts]* sur *[!DNL Global]*.
1. Créez plusieurs sites web et magasins :

   * ws1 > s11, s12 > sw111, sw122
   * ws2 > s21, s22 > sw211, sw212

1. Créez un nouveau client sous le *site web principal* à partir de l’adresse e-mail de l’administrateur utilisée comme <adb@yormail.com>.
1. Sous **[!UICONTROL Admin]**, accédez à **[!UICONTROL System]** > **[!UICONTROL Import]**.
1. Sélectionnez **[!UICONTROL Customer Entity Type]** comme *[!UICONTROL Customers Main File]*.
1. Utilisez la même adresse e-mail que <adb@yormail.com> sur un autre site web, par exemple ws1. Reportez-vous à l’exemple de fichier CSV customer.csv fourni ci-dessous.
1. Terminez l’importation pour afficher le nouvel utilisateur créé sous le site web *ws1* avec la même adresse électronique.

contenu customer.csv :

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>Résultats attendus</u> :

Le client importé avec la même adresse e-mail n’est pas dupliqué, mais mis à jour.

<u>Résultats réels</u> :

Les clients en double sont créés avec la même adresse e-mail lors de l’utilisation de l’import client.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
