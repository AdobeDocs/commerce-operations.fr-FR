---
title: "ACSD-55628 : téléchargement du fichier sur le formulaire d’enregistrement de la société ; remplacement du fichier pour l’attribut du client sur storefront"
description: Appliquez le correctif ACSD-55628 pour résoudre le problème d’Adobe Commerce lors du téléchargement d’un fichier sur le formulaire d’enregistrement de la société et du remplacement d’un fichier pour un attribut du client sur le storefront.
feature: Storefront, Attributes, B2B, Customers
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-55628 : téléchargement du fichier sur le formulaire d’enregistrement de la société ; remplacement du fichier pour l’attribut du client sur storefront

>[!NOTE]
>
>Ce correctif remplace [ACSD-51240](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51240-uploaded-file-missing-while-registering-via-company-registration-form.md).

Le correctif ACSD-55628 corrige le problème en chargeant un fichier sur le formulaire d’enregistrement de la société et en remplaçant un fichier pour un attribut du client sur le storefront. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 est installé. L’ID de correctif est ACSD-55628. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2 &lt; 2.4.5 et 2.4.5-p1 &lt; 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Impossible de remplacer un fichier pour un attribut du client sur le storefront.

<u>Étapes à reproduire</u> :

1. Créez un nouvel attribut du client avec les valeurs suivantes :

   * *[!UICONTROL Input Type]* : *[!UICONTROL File (Attachment)]*
   * *[!UICONTROL Show on Storefront]* : *Oui*
   * *[!UICONTROL Forms to Use In]* : *toutes les options disponibles*

1. Connectez-vous en tant que client sur le storefront et ouvrez **[!UICONTROL My Account]** > **[!UICONTROL Account Information]**.
1. Chargez une nouvelle image et enregistrez-la.
1. Actualisez la page. Supprimez l’ancienne image et téléchargez-en une nouvelle. Enregistrez les modifications.

<u>Résultats attendus</u> :

La nouvelle image est enregistrée.

<u>Résultats réels</u> :

L’ancienne image est toujours affichée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
