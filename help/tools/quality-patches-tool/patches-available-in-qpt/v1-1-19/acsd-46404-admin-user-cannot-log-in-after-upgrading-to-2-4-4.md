---
title: 'ACSD-46404 : impossible pour un administrateur de se connecter après la mise à niveau vers la version 2.4.4'
description: Le correctif ACSD-46404 résout le problème où un utilisateur administrateur ne peut pas se connecter après la mise à niveau vers la version 2.4.4. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.19 est installé. L’ID du correctif est ACSD-46404. Notez que le problème a été résolu dans Adobe Commerce 2.4.5.
feature: Admin Workspace
role: Admin
exl-id: f475ca56-5e06-4d4d-be42-f760c95968cf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-46404 : impossible pour un administrateur de se connecter après la mise à niveau vers la version 2.4.4

Le correctif ACSD-46404 résout le problème où un utilisateur administrateur ne peut pas se connecter après la mise à niveau vers la version 2.4.4. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.19 est installé. L’ID du correctif est ACSD-46404. Notez que le problème a été résolu dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur administrateur ne peut pas se connecter après la mise à niveau vers la version 2.4.4.

<u>Procédure à suivre </u> :

1. Connectez-vous au Panneau d’administration
1. Accédez à Store > **Settings** > **Configuration** > **Advanced** > **System** > **Security**.
1. Définissez la Taille maximale de session dans l’administrateur sur **0** et enregistrez-la.

<u>Résultats attendus</u> :

L’utilisateur administrateur peut se connecter avec succès.

<u>Résultats réels</u> :

L’utilisateur administrateur se déconnecte et ne peut pas se connecter.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
