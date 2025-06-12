---
title: 'ACSD-51853 : les styles de texte copiés ne sont pas appliqués à l’aide du générateur de page'
description: Appliquez le correctif ACSD-51853 pour résoudre le problème d’Adobe Commerce en raison duquel les styles de texte copiés ne sont pas appliqués lors de l’utilisation du générateur de page.
feature: Page Builder
role: Admin
exl-id: fda5ba6e-4786-473c-a3a2-7356aa20f5ae
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-51853 : les styles de texte copiés ne sont pas appliqués à l’aide du générateur de page

Le correctif ACSD-51853 corrige le problème où les styles de texte copiés ne sont pas appliqués lorsque le générateur de page est utilisé. Ce correctif est disponible lorsque la version 1.1.34 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51853. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les styles de texte copiés ne sont pas appliqués lorsque le générateur de page est utilisé

<u>Procédure à suivre </u> :

1. Connectez-vous à Admin.
1. Accédez à > **contenu** > **pages** > **Ouvrir une page** > **Modifier avec Page Builder**.
1. Faites glisser Ligne et *Texte* depuis **[!UICONTROL Elements]**.
1. Copiez **contenu enrichi**, collez ce texte dans un **[!UICONTROL Page Builder]**.

<u>Résultats attendus</u>

Le texte copié est collé avec tous les styles.

<u>Résultats réels</u>

Le texte copié est collé en tant que texte brut et tous les styles sont perdus.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
