---
title: 'ACSD-51574 : image non mise à jour sur le front-end lorsqu’elle est remplacée par une autre image'
description: Appliquez le correctif ACSD-51574 pour résoudre le problème Adobe Commerce en raison duquel l’image n’est pas mise à jour sur le front-end après l’avoir remplacée par une autre image.
feature: Configuration
role: Admin
exl-id: 199674fc-c3b3-4fee-9061-f0546833c1cd
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-51574 : image non mise à jour sur le front-end lorsqu’elle est remplacée par une autre image

Le correctif ACSD-51574 corrige le problème où l’image n’est pas mise à jour sur le front-end après l’avoir remplacée par une autre image. Ce correctif est disponible lorsque la version 1.1.37 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51574. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’image n’est pas mise à jour sur le front-end après l’avoir remplacée par une autre image.

<u>Procédure à suivre </u> :

1. Créez un produit avec quelques images.
1. Modifiez le produit et chargez une image dont le nom est connu (exemple : *image.jpg*).
1. Enregistrez le produit.
1. Modifiez à nouveau le produit et supprimez l’ancienne version de l’image, puis chargez la nouvelle version de l’image portant le même nom. **Assurez-vous que la nouvelle version est visiblement différente pour identifier le problème.**
1. Enregistrez le produit. Les images s’affichent dans les champs admin et frontend.
1. Modifiez à nouveau le produit et chargez à nouveau la même nouvelle image (en utilisant le même nom).
1. Enregistrez le produit et vérifiez la page produit sur le serveur frontal.

<u>Résultats attendus</u> :

L’image chargée la deuxième fois doit être la nouvelle image, avec le nom de l’image renommée.

<u>Résultats réels</u> :

L’image chargée la deuxième fois est l’ancienne version de l’image supprimée précédemment, au lieu de la même nouvelle image.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
