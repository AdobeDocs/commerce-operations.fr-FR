---
title: 'ACSD-53628 : le rapport de commande client CSV affiche des caractères spéciaux incorrects'
description: Appliquez le correctif ACSD-53628 pour résoudre le problème d’Adobe Commerce où le rapport de commande client CSV affiche des caractères spéciaux incorrects.
feature: Orders, Data Import/Export
role: Admin, Developer
exl-id: b6293efe-fbeb-4b1e-b408-34dc86228b8e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-53628 : le rapport de commande client CSV affiche des caractères spéciaux incorrects

Le correctif ACSD-53628 corrige le problème en raison duquel le rapport de commande client CSV affiche des caractères spéciaux incorrects. Ce correctif est disponible lorsque la version 1.1.37 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-53628. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) : 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) : 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le rapport de commande client CSV affiche des caractères spéciaux incorrects.

<u>Procédure à suivre </u> :

1. Remplacez **[!UICONTROL Base Currency]** et **[!UICONTROL Default Display Currency]** par Euro dans la configuration de la devise.
1. Passer une commande.
1. Dans la barre latérale d’administration, accédez à **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Sélectionnez des dates. Cliquez sur **[!UICONTROL Show Report]**. Cliquez sur **[!UICONTROL Export]** pour exporter le fichier CSV.

<u>Résultats attendus</u> :

Les caractères spéciaux d’un fichier CSV exporté s’affichent correctement dans Excel.

<u>Résultats réels</u> :

Le rapport de commande client CSV n’affiche pas correctement les caractères spéciaux.


## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
