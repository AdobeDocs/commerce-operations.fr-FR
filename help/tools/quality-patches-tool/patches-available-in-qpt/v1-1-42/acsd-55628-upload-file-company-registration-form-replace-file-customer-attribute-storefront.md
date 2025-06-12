---
title: 'ACSD-55628 : chargement du fichier sur le formulaire d’enregistrement de l’entreprise ; remplacement du fichier pour l’attribut du client sur le storefront'
description: Appliquez le correctif ACSD-55628 pour résoudre le problème Adobe Commerce avec le téléchargement d’un fichier sur le formulaire d’enregistrement de la société et le remplacement d’un fichier pour un attribut du client sur le storefront.
feature: Storefront, Attributes, B2B, Customers
role: Admin, Developer
exl-id: a008a205-ec1d-4a1d-9cd2-75f10a937057
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-55628 : chargement du fichier sur le formulaire d’enregistrement de l’entreprise ; remplacement du fichier pour l’attribut du client sur le storefront

>[!NOTE]
>
>Ce correctif remplace [ACSD-51240](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51240-uploaded-file-missing-while-registering-via-company-registration-form.md).

Le correctif ACSD-55628 corrige le problème en chargeant un fichier sur le formulaire d’enregistrement de l’entreprise et en remplaçant un fichier pour un attribut du client sur le storefront. Ce correctif est disponible lorsque la version 1.1.42 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-55628. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2 &lt; 2.4.5 et 2.4.5-p1 &lt; 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Impossible de remplacer un fichier pour un attribut du client sur le storefront.

<u>Procédure à suivre </u> :

1. Créez un nouvel attribut client avec les valeurs suivantes :

   * *[!UICONTROL Input Type]* : *[!UICONTROL File (Attachment)]*
   * *[!UICONTROL Show on Storefront]* : *Oui*
   * *[!UICONTROL Forms to Use In]* : *toutes les options disponibles*

1. Connectez-vous en tant que client sur le storefront et ouvrez **[!UICONTROL My Account]** > **[!UICONTROL Account Information]**.
1. Chargez une nouvelle image et enregistrez-la.
1. Actualisez la page. Supprimez l’ancienne image et chargez-en une nouvelle. Enregistrez les modifications.

<u>Résultats attendus</u> :

La nouvelle image est enregistrée.

<u>Résultats réels</u> :

L’ancienne image est toujours affichée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
