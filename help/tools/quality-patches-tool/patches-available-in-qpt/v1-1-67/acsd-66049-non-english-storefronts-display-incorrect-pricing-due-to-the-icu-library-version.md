---
title: 'ACSD-66049 : les vitrines non anglaises affichent un prix incorrect en raison de la version de la bibliothèque ICU'
description: Appliquez le correctif ACSD-66049 pour résoudre le problème d'Adobe Commerce où les vitrines non-anglaises affichent un prix incorrect en raison de l'inadéquation de la version de la bibliothèque ICU dans les anciens environnements PHP (versions 63.1 à 74.1).
feature: Products
role: Admin, Developer
type: Troubleshooting
exl-id: e667d462-87f6-4db5-bf3f-3213edac2f09
source-git-commit: da11e8bd5c4937ec2a7e548ce487797b83f8fd27
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-66049 : les vitrines non anglaises affichent un prix incorrect en raison de la version de la bibliothèque ICU

Le correctif ACSD-66049 corrige le problème où les vitrines non-anglaises affichent un prix incorrect en raison d&#39;une inadéquation des versions de la bibliothèque ICU dans les anciens environnements PHP (versions 63.1 à 74.1). Ce correctif est disponible lorsque la version 1.1.67 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66049. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p3 - 2.4.5-p13, 2.4.7 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les storefronts non anglais affichent un prix incorrect lorsque des versions plus anciennes de la bibliothèque ICU PHP (63.1 à 74.1) sont utilisées.

<u>Procédure à suivre </u> :

1. Vérifier la version de l’ICU :
   * Connectez-vous au serveur via SSH et exécutez la commande : `php -a`
   * À l’invite, saisissez : `echo INTL_ICU_VERSION;`
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale]** > **[!UICONTROL Locale Options]**. **[!UICONTROL Configure Locale]** = *[!UICONTROL Hebrew (Israel)]*.
1. Créez un produit au prix = 100.
1. Affichez la page produit sur le storefront.

<u>Résultats attendus</u> :

Le prix affiché n&#39;est pas 0.

<u>Résultats réels</u> :

Après avoir brièvement apparu comme 100, le prix est immédiatement mis à jour à 0.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
